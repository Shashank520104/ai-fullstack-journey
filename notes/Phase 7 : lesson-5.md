# Phase 7 — Lesson 5

# Sessions vs JWT vs Cookies (Placement Revision)

**AI Full Stack Developer Roadmap**

---

# Why Do We Need Authentication?

Suppose a user logs into Instagram.

```text id="3lq5tz"
Email

Password

↓

Login Successful
```

Now the user opens:

```http id="efwlv3"
GET /profile
```

Question:

How does the server know who sent this request?

There are three solutions:

* Sessions
* JWT
* Cookies

---

# Method 1 — Sessions

## What is a Session?

A Session is a server-side authentication mechanism.

After login,

the server creates a Session and stores user information.

The browser stores only a Session ID.

---

## Session Flow

```text id="g43v91"
Login

↓

Password Verified

↓

Server Creates Session

↓

Session Stored

↓

Browser Receives Session ID

↓

Future Requests

↓

Browser Sends Session ID

↓

Server Finds Session

↓

Access Granted
```

---

## Browser Stores

```text id="n8j3dy"
Session ID
```

Example

```text id="oam8g0"
abc123xyz
```

---

## Server Stores

```text id="mdq8wa"
Session ID

↓

User Information
```

---

## Advantages

* Easy to implement
* Secure
* Easy logout

---

## Disadvantages

* Server memory increases
* Difficult to scale
* Every logged-in user requires server storage

---

# Method 2 — JWT

## What is JWT?

JWT is a stateless authentication mechanism.

Server stores nothing.

Browser stores identity.

---

## JWT Flow

```text id="8vjlwm"
Login

↓

Password Verified

↓

JWT Created

↓

Browser Stores JWT

↓

Future Requests

↓

JWT Sent

↓

Server Verifies JWT

↓

Access Granted
```

---

## Browser Stores

JWT

Example

```text id="r87lxt"
xxxxx.yyyyy.zzzzz
```

---

## Server

Does NOT store Sessions.

Only verifies JWT.

---

## Advantages

* Stateless
* Fast
* Easy Scaling
* Better for Microservices

---

## Disadvantages

* Logout is more complex
* Stolen tokens remain valid until expiry
* Requires proper security practices

---

# Method 3 — Cookies

## What is a Cookie?

Cookie is **NOT an authentication method**.

Cookie is a browser storage mechanism.

It stores small pieces of data.

---

## Cookie Can Store

* JWT
* Session ID
* Theme
* Language
* User Preferences

---

## Cookie Flow

```text id="ms7j0d"
Browser

↓

Cookie Stored

↓

Future Requests

↓

Cookie Automatically Sent

↓

Server
```

---

# Types of Cookies

---

## Normal Cookie

JavaScript can read.

Example

```javascript id="0b7tf4"
document.cookie
```

Less secure.

---

## HttpOnly Cookie

JavaScript cannot read.

Browser automatically sends it.

Industry Standard.

---

## Secure Cookie

Cookie is sent only over HTTPS.

Never over HTTP.

Used in Production.

---

## SameSite Cookie

Protects against CSRF attacks.

Values

* Strict
* Lax
* None

---

# Local Storage vs Cookies

| Local Storage       | Cookies             |
| ------------------- | ------------------- |
| JavaScript Can Read | HttpOnly Cannot     |
| Must Send Manually  | Sent Automatically  |
| Higher XSS Risk     | More Secure         |
| Beginner Projects   | Production Projects |

---

# Sessions vs JWT

| Sessions           | JWT                         |
| ------------------ | --------------------------- |
| Stateful           | Stateless                   |
| Server Stores Data | Browser Stores Token        |
| Memory Required    | No Memory                   |
| Easy Logout        | Logout Requires Extra Logic |
| Difficult to Scale | Easy to Scale               |

---

# JWT vs Cookies

JWT

↓

Authentication Token

Cookie

↓

Storage Mechanism

JWT can be stored inside a Cookie.

---

# Industry Authentication

## Beginner Projects

```text id="mrm30r"
JWT

↓

Local Storage
```

---

## Production

```text id="dqdjhz"
JWT

↓

HttpOnly Cookie

↓

HTTPS
```

---

## Enterprise

```text id="pjlwmr"
Access Token

+

Refresh Token

+

HttpOnly Cookie

+

HTTPS

+

Redis Blacklist
```

---

# Authentication Comparison

```text id="mf2pgv"
Sessions

↓

Server Remembers User

-------------------------

JWT

↓

Browser Carries Identity

-------------------------

Cookies

↓

Browser Storage
```

---

# Advantages Summary

## Sessions

✔ Easy Logout

✔ Secure

✔ Simple

---

## JWT

✔ Stateless

✔ Scalable

✔ Fast Verification

✔ Good for APIs

---

## Cookies

✔ Automatic Request Sending

✔ HttpOnly Security

✔ Secure Storage

---

# Disadvantages Summary

## Sessions

✘ Server Memory Required

✘ Scaling Problems

---

## JWT

✘ Logout Difficult

✘ Stolen Token Remains Valid Until Expiry

---

## Local Storage

✘ Vulnerable to XSS

---

# Which One Should You Use?

## College Projects

JWT

*

Local Storage

---

## Startups

JWT

*

HttpOnly Cookies

---

## Large Companies

JWT

*

Refresh Tokens

*

HttpOnly Cookies

*

HTTPS

*

Token Rotation

---

# Quick Revision

```text id="9cbv8z"
Sessions

↓

Server Stores User

----------------------

JWT

↓

Browser Stores Identity

----------------------

Cookies

↓

Storage Mechanism

----------------------

HttpOnly Cookie

↓

JavaScript Cannot Read

----------------------

Secure Cookie

↓

HTTPS Only
```

---

# Placement Interview Questions

## Q1

What is the difference between Authentication and Authorization?

**Answer**

Authentication verifies identity.

Authorization verifies permissions.

---

## Q2

What is a Session?

**Answer**

A Session is a server-side authentication mechanism where the server stores user information and the browser stores only a Session ID.

---

## Q3

Why is JWT called Stateless?

**Answer**

Because the server does not store login sessions.

The token itself carries the user's identity.

---

## Q4

What is a Cookie?

**Answer**

A Cookie is a browser storage mechanism used to store small pieces of data like Session IDs or JWTs.

---

## Q5

Is Cookie an Authentication Method?

**Answer**

No.

Cookie is only a storage mechanism.

---

## Q6

Can JWT exist without Cookies?

**Answer**

Yes.

JWT can be stored in Local Storage or Session Storage.

---

## Q7

Can Cookies exist without JWT?

**Answer**

Yes.

Cookies can store any small data.

---

## Q8

What is HttpOnly Cookie?

**Answer**

A Cookie that JavaScript cannot access.

Only the browser can automatically send it with requests.

---

## Q9

Why is HttpOnly Cookie more secure?

**Answer**

Because JavaScript cannot steal it during XSS attacks.

---

## Q10

Which is safer?

* JWT in Local Storage
* JWT in HttpOnly Cookie

**Answer**

JWT inside HttpOnly Cookie.

---

## Q11

Why do companies prefer JWT over Sessions?

**Answer**

Because JWT is Stateless, scales better, and reduces server memory usage.

---

## Q12

What are the disadvantages of JWT?

**Answer**

* Difficult logout
* Token remains valid until expiry
* Requires proper security practices

---

## Q13

What is Secure Cookie?

**Answer**

A Cookie that is sent only over HTTPS.

---

## Q14

What is SameSite Cookie?

**Answer**

A Cookie attribute that helps prevent CSRF attacks.

---

## Q15

Which authentication method requires server memory?

**Answer**

Sessions.

---

# High-Frequency Placement Questions

### ⭐ Why do companies use JWT + HttpOnly Cookies?

**Answer**

* Stateless Authentication
* Better Security
* Protection from XSS
* Automatic Cookie Transmission
* Suitable for Production

---

### ⭐ Why is Local Storage not recommended in Production?

**Answer**

Because JavaScript can access Local Storage, making it vulnerable to XSS attacks.

---

### ⭐ Which authentication system scales better?

**Answer**

JWT.

Because the server does not store user sessions.

---

### ⭐ Can JWT be used without Cookies?

**Answer**

Yes.

JWT can be stored in Local Storage, Session Storage, or Cookies.

---

### ⭐ Difference Between Sessions, JWT, and Cookies

| Sessions           | JWT                  | Cookies                 |
| ------------------ | -------------------- | ----------------------- |
| Authentication     | Authentication       | Storage                 |
| Stateful           | Stateless            | Storage Mechanism       |
| Server Stores Data | Browser Stores Token | Browser Stores Data     |
| Requires Memory    | No Memory            | No Authentication Logic |

---

# End of Lesson 5

## Next Lesson

**Phase 7 — Lesson 6**

**Hashing vs Encryption vs Encoding**

Topics:

* Hashing
* Encryption
* Encoding
* bcrypt
* Salt
* Why Passwords Cannot Be Decrypted
* Industry Password Security
* Placement Interview Questions
