# Lesson 11 – Authentication & JWT (Complete Placement Notes)

> Phase 5 – Backend Authentication System
> Project: Shaurya AI
> Goal: Understand and implement Authentication, Authorization, bcrypt, JWT, Middleware, and Protected Routes from basics to production level.

---

# 1. Authentication vs Authorization

## Authentication

Authentication answers:

> "Who are you?"

It verifies the identity of a user.

Example:

- Login using Email + Password
- OTP Verification
- Google Login

Example:

```
Email
Password

↓

Verified

↓

Authenticated
```

---

## Authorization

Authorization answers:

> "What are you allowed to do?"

It checks permissions after authentication.

Example:

```
User

↓

Authenticated

↓

Role = Admin

↓

Can Delete Users
```

---

## Difference

| Authentication | Authorization |
|---------------|---------------|
| Verifies identity | Verifies permissions |
| Happens first | Happens after authentication |
| Login | Role Checking |

---

# Placement Question

Q: Can Authorization happen before Authentication?

Answer:

No.

The system must first know who the user is before deciding what they are allowed to access.

---

# 2. Session vs JWT

## Session Authentication

```
Login

↓

Server Creates Session

↓

Stores Session in Memory / Redis

↓

Browser Stores Session ID

↓

Every Request

↓

Server Looks Up Session
```

Problems

- Server stores every session
- Memory increases
- Hard to scale

---

## JWT Authentication

```
Login

↓

JWT Created

↓

Browser Stores JWT

↓

Every Request

↓

JWT Sent

↓

Server Verifies

↓

Done
```

Advantages

- Stateless
- Highly scalable
- Faster
- Preferred for modern APIs

---

# Placement Question

Q:

Which is more scalable?

Answer:

JWT because the server does not need to store session data.

---

# 3. User Model

```javascript
const userSchema = new mongoose.Schema({
    name,
    email,
    password,
    role
});
```

Role uses enum

```javascript
enum:["user","admin"]
```

Meaning

Only these values are allowed.

---

createdAt

updatedAt

Generated automatically by Mongoose.

---

# Placement Question

Difference between Schema and Model?

Schema

Blueprint

↓

Model

Creates documents using that blueprint.

---

# 4. Signup Flow

```
Frontend

↓

Route

↓

Controller

↓

Service

↓

Model

↓

MongoDB
```

---

# Controller Responsibility

- Receive Request
- Call Service
- Return Response

Never write business logic here.

---

# Service Responsibility

Business Logic

- Duplicate Email Check
- Hash Password
- Save User

---

# Placement Question

Why keep Controller thin?

Answer

Because controllers should only handle HTTP requests and responses. Business logic belongs inside services for better maintainability and reusability.

---

# 5. Duplicate Email Check

```javascript
const existingUser = await User.findOne({
    email
});
```

If found

↓

Throw Error

```javascript
throw new Error("Email already exists");
```

---

Why?

Email must remain unique.

---

# Placement Question

Why search using email?

Answer

Email is unique while passwords are not.

---

# 6. Password Hashing

Never store

```
Shashank@123
```

Store

```
$2b$10$sdjhsd78...
```

Using

```javascript
bcrypt.hash(password,12)
```

---

Hashing is

ONE WAY

Encryption is

TWO WAY

---

bcrypt never decrypts passwords.

---

# Salt

bcrypt automatically adds random salt.

Same password

↓

Different hashes.

---

# Placement Question

Q:

Can bcrypt decrypt passwords?

Answer

No.

bcrypt is a one-way hashing algorithm.

---

# Placement Question

What does

```javascript
bcrypt.hash(password,12)
```

return?

Answer

Password Hash.

---

# 7. Login Flow

```
Receive Email + Password

↓

Find User

↓

User Exists?

↓

No

↓

Invalid Credentials

-----------------

Yes

↓

bcrypt.compare()

↓

Password Correct?

↓

No

↓

Invalid Credentials

-----------------

Yes

↓

Generate JWT

↓

Return JWT
```

---

Finding User

```javascript
User.findOne({
    email
});
```

---

Password Check

```javascript
bcrypt.compare(
    password,
    user.password
);
```

Returns

```
true

or

false
```

---

# Placement Question

Why don't we search using password?

Answer

Passwords are stored as hashes.

---

# Placement Question

Why return

```
Invalid email or password
```

instead of

```
Email not found
```

Answer

To prevent attackers from discovering registered email addresses.

---

# 8. JWT

JWT

=

JSON Web Token

Structure

```
Header

.

Payload

.

Signature
```

Example

```
xxxxx.yyyyy.zzzzz
```

---

Header

Contains

Algorithm

---

Payload

Contains

```
id

role
```

Payload is

NOT encrypted

Only Base64 encoded.

---

Signature

Protects against tampering.

---

# Placement Question

Can users read Payload?

Answer

Yes.

Payload is Base64 encoded.

---

Can users modify Payload?

Yes.

But verification will fail because the signature becomes invalid.

---

# 9. JWT Generation

```javascript
const token = jwt.sign(

{
    id:user._id,
    role:user.role
},

process.env.JWT_SECRET,

{
    expiresIn:"7d"
}

);
```

---

Payload

↓

Safe Information

---

Secret

↓

Known only to server

---

Options

↓

Expiry

---

# Placement Question

Should password be stored inside JWT?

Answer

Never.

JWT payload is readable.

---

# 10. Authentication Middleware

Purpose

Verify JWT before allowing access.

---

Flow

```
Request

↓

Authorization Header

↓

Token Exists?

↓

No

↓

401

----------------

Yes

↓

jwt.verify()

↓

Invalid?

↓

401

----------------

Valid

↓

req.user

↓

next()

↓

Controller
```

---

Header Format

```
Authorization

Bearer eyJhbGc...
```

Extract Token

```javascript
const token =
authHeader.split(" ")[1];
```

---

Verify

```javascript
jwt.verify(
token,
process.env.JWT_SECRET
);
```

---

Attach User

```javascript
req.user=decoded;
```

---

Continue

```javascript
next();
```

---

# Placement Question

Why attach

```
req.user
```

instead of querying database again?

Answer

Middleware verifies JWT once and makes decoded user information available to every controller.

---

What happens if next() is forgotten?

Answer

Request hangs.

Controller never executes.

---

HTTP Status Code

Unauthorized

```
401
```

---

# 11. Protected Route

```
GET

/api/profile
```

Protected

```javascript
router.get(

"/profile",

authMiddleware,

profileController

);
```

Middleware runs

↓

Controller runs

---

# End-to-End Authentication Flow

```
Signup

↓

Hash Password

↓

Save User

↓

Login

↓

Compare Password

↓

Generate JWT

↓

Frontend Stores JWT

↓

Protected Request

↓

Middleware Verifies JWT

↓

Controller Executes

↓

Response
```

---

# Most Asked Placement Questions

### Q1

Difference between Authentication and Authorization?

---

### Q2

Difference between Session and JWT?

---

### Q3

Why is JWT Stateless?

---

### Q4

Why hash passwords?

---

### Q5

Difference between Encryption and Hashing?

---

### Q6

Can bcrypt decrypt passwords?

---

### Q7

How does bcrypt.compare() work?

---

### Q8

Why are same passwords producing different hashes?

---

### Q9

Can JWT payload be read?

---

### Q10

Can JWT payload be modified?

---

### Q11

What does JWT Signature do?

---

### Q12

What is JWT Secret?

---

### Q13

What happens after JWT expires?

Answer

jwt.verify() throws an expiration error and the user must log in again (or refresh the token if refresh tokens are implemented).

---

### Q14

Why attach req.user?

---

### Q15

What happens if next() is not called?

---

### Q16

Why return only selected fields instead of returning the whole user document?

Answer

To avoid exposing sensitive information such as password hashes and internal metadata.

---

# Key Interview Keywords

- Authentication
- Authorization
- Stateless Authentication
- bcrypt
- Salt
- Hashing
- JWT
- Header
- Payload
- Signature
- Middleware
- Protected Routes
- req.user
- next()
- Least Privilege Principle
- Generic Error Messages
- Role-Based Access Control (RBAC)

---

# Lesson 11 Summary

✅ Authentication vs Authorization

✅ Session vs JWT

✅ User Model

✅ Signup API

✅ Duplicate Email Check

✅ Password Hashing

✅ Login API

✅ bcrypt.compare()

✅ JWT Generation

✅ JWT Verification

✅ Authentication Middleware

✅ Protected Routes

This lesson forms the complete foundation of backend authentication used in modern MERN applications and is one of the highest-priority topics for Node.js backend interviews.
