# Phase 7 — Lesson 4

# JWT Lifecycle (Placement Revision)

**AI Full Stack Developer Roadmap**

---

# What is JWT Lifecycle?

JWT Lifecycle is the complete journey of a JSON Web Token from the moment a user logs in until the token expires.

---

# Complete JWT Flow

```text
User Login

↓

Password Verification

↓

JWT Created

↓

JWT Sent to Browser

↓

Browser Stores JWT

↓

Future API Requests

↓

JWT Sent to Backend

↓

JWT Verified

↓

Access Granted
```

---

# Step 1 — User Login

User enters:

```json
{
  "email": "shashank@gmail.com",
  "password": "Shashank@123"
}
```

↓

Backend receives request.

↓

Backend checks MongoDB.

↓

Password is compared using bcrypt.

If password matches,

Login Successful.

---

# Step 2 — JWT Creation

Backend creates JWT using

```javascript
jwt.sign(payload, secret, options);
```

---

## Syntax

```javascript
jwt.sign(
    payload,
    secret,
    options
);
```

---

# Argument 1

## Payload

Contains user information.

Example:

```javascript
{
    id: user._id,
    role: user.role
}
```

Usually contains

* User ID
* Role
* Email

Never store

* Password
* OTP
* Secret Keys

inside JWT.

---

# Argument 2

## Secret

Example

```javascript
process.env.JWT_SECRET
```

Purpose

* Used while creating JWT.
* Used again while verifying JWT.

Important

JWT_SECRET should never be exposed.

Never commit it to GitHub.

Never send it to Frontend.

---

# Argument 3

## Options

Example

```javascript
{
   expiresIn: "7d"
}
```

Meaning

JWT remains valid for 7 days.

After that,

user must login again.

---

# Result

Server generates

```text
xxxxx.yyyyy.zzzzz
```

JWT

↓

Sends it to Browser.

---

# Step 3 — Browser Stores JWT

Example

```javascript
localStorage.setItem("token", token);
```

Browser now has the user's identity.

---

# Step 4 — Protected Request

User opens Dashboard.

Frontend sends

```http
GET /dashboard
```

along with

```http
Authorization: Bearer <JWT_TOKEN>
```

This is called a **Bearer Token**.

---

# Step 5 — JWT Verification

Backend verifies JWT using

```javascript
jwt.verify(token, process.env.JWT_SECRET);
```

---

# What verify() Checks

✔ Signature

✔ Expiry Time

✔ Token Tampering

If everything is valid,

JWT Payload is returned.

Example

```javascript
{
    id: "123",
    role: "user"
}
```

Server now knows the user's identity.

---

# What if Token is Modified?

Suppose hacker changes

```json
{
    "role": "user"
}
```

to

```json
{
    "role": "admin"
}
```

Payload changes.

Signature becomes invalid.

Server returns

```text
401 Unauthorized
```

---

# Token Expiry

Example

```javascript
expiresIn: "7d"
```

After 7 days

↓

verify() throws

```text
TokenExpiredError
```

User must login again.

---

# Why Token Expiry is Important

If a token is stolen,

it cannot be used forever.

Expiry limits the damage.

---

# Complete Internal Flow

```text
Login

↓

Password Verified

↓

jwt.sign()

↓

JWT Created

↓

Browser Stores JWT

↓

Protected Request

↓

JWT Sent

↓

jwt.verify()

↓

Signature Checked

↓

Expiry Checked

↓

Payload Returned

↓

Access Granted
```

---

# Difference

## jwt.sign()

Purpose

Creates JWT.

Used during Login.

---

## jwt.verify()

Purpose

Checks JWT.

Used on Protected Routes.

---

# Important Interview Points

✔ JWT is Stateless.

✔ Browser stores JWT.

✔ Server does not store Sessions.

✔ JWT_SECRET is required for both sign() and verify().

✔ verify() checks Signature and Expiry.

✔ Expired Tokens are rejected.

---

# Common Interview Questions

## Q1

Which function creates JWT?

Answer

```javascript
jwt.sign()
```

---

## Q2

Which function verifies JWT?

Answer

```javascript
jwt.verify()
```

---

## Q3

Why is the same JWT_SECRET used in sign() and verify()?

Answer

The server uses JWT_SECRET while creating the Signature.

Later,

the same secret is required to recreate the Signature and verify that the token has not been modified.

---

## Q4

What happens if JWT_SECRET changes?

Answer

All previously generated JWTs become invalid.

Users must login again.

---

## Q5

Why do we use expiresIn?

Answer

To limit how long a JWT remains valid.

This reduces security risks if a token is stolen.

---

## Q6

What does jwt.verify() return?

Answer

The decoded Payload.

Example

```javascript
{
    id: "...",
    role: "user"
}
```

---

## Q7

What status code is returned for an expired or invalid JWT?

Answer

```text
401 Unauthorized
```

---

# Quick Revision

```text
jwt.sign()

↓

Creates Token

----------------------

jwt.verify()

↓

Checks Token

----------------------

JWT_SECRET

↓

Known Only To Server

----------------------

expiresIn

↓

Token Validity

----------------------

Bearer Token

↓

Authorization Header
```

---

# End of Lesson 4

Next:

**Lesson 5 — Sessions vs JWT vs Cookies**
