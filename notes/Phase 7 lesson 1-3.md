# Phase 7 Notes — Authentication & Production Backend

## Lessons 1–3 (Placement Revision)

**AI Full Stack Developer Roadmap**

---

# Lesson 1 — Authentication Fundamentals

## What is Authentication?

Authentication answers one question:

> **Who are you?**

Example:

* Login to Gmail
* Login to Instagram
* Login to LinkedIn

The server verifies your identity.

---

## What is Authorization?

Authorization answers:

> **What are you allowed to do?**

Example:

Student

* View Marks ✅
* Edit Marks ❌

Teacher

* View Marks ✅
* Upload Marks ✅

Admin

* Full Access ✅

---

## Authentication vs Authorization

| Authentication    | Authorization        |
| ----------------- | -------------------- |
| Verifies Identity | Verifies Permissions |
| Login             | Access Control       |
| "Who are you?"    | "What can you do?"   |

---

## Authentication Flow

User

↓

Login Form

↓

Backend

↓

Database

↓

Password Verified

↓

User Authenticated

---

## Why Authentication Exists

Without Authentication:

Anyone can access protected resources.

Authentication proves the identity of the user.

---

## What is HTTP?

HTTP is a communication protocol between client and server.

Example:

```http
GET /profile
```

---

## HTTP is Stateless

Every request is independent.

Example:

```text
Request 1

↓

Completed

↓

Request 2

↓

Server forgets Request 1
```

Server remembers nothing.

---

## Why is Stateless a Problem?

Suppose:

User logs in.

Next request:

```http
GET /profile
```

How does the server know:

> This request belongs to Shashank?

It doesn't.

Therefore Authentication Systems are needed.

---

## Two Authentication Methods

### Sessions

Server stores login information.

Browser stores Session ID.

```text
Browser

↓

Session ID

↓

Server

↓

Session Data
```

---

### JWT

Server creates a Token.

Browser stores Token.

Every request sends Token.

Server verifies Token.

No server-side session storage required.

---

# Placement Questions

### Q1

Authentication or Authorization comes first?

Answer:

Authentication

↓

Authorization

---

### Q2

Why is HTTP called Stateless?

Answer:

Because it never remembers previous requests.

---

### Q3

Difference between Authentication and Authorization?

Authentication:

Identity

Authorization:

Permission

---

---

# Lesson 2 — JWT Basics

## What is JWT?

JWT

=

JSON Web Token

It is a signed digital identity card.

---

## Full Form

JSON

↓

Stores data

Web

↓

Used for Web Applications

Token

↓

Digital Identity Card

---

## Real Life Example

Movie Ticket

You pay once.

After that,

you only show the ticket.

JWT works the same way.

---

## Authentication using JWT

User

↓

Login

↓

Server verifies password

↓

Server creates JWT

↓

JWT sent to Browser

↓

Browser stores JWT

↓

Every request

↓

JWT sent

↓

Server verifies JWT

↓

Access Granted

---

## Where is JWT Stored?

1.

Local Storage

```javascript
localStorage.setItem("token", token);
```

Easy

Used in beginner projects.

---

2.

HttpOnly Cookie

Industry Standard

Safer

More Secure

---

## JWT Advantages

* Stateless
* Fast
* Scalable
* Cross Platform

---

## Why not simply send User ID?

Example

```json
{
"id":"123"
}
```

Hacker changes

```json
{
"id":"123",
"role":"admin"
}
```

Server cannot trust it.

JWT solves this using Signature.

---

## Important Point

JWT is

**Signed**

NOT

**Encrypted**

Payload is readable.

Signature protects it.

---

# Placement Questions

### Q1

Why is JWT called Stateless Authentication?

Answer:

Server stores no session.

JWT itself contains identity.

---

### Q2

Can JWT be stored in Local Storage?

Yes.

But HttpOnly Cookies are more secure.

---

### Q3

Why do companies prefer JWT?

* No session storage
* Better scalability
* Easy verification

---

---

# Lesson 3 — JWT Internals

JWT has exactly three parts.

```text
HEADER

↓

PAYLOAD

↓

SIGNATURE
```

Looks like:

```text
xxxxx.yyyyy.zzzzz
```

---

# Part 1

## HEADER

Stores metadata.

Example:

```json
{
"alg":"HS256",
"typ":"JWT"
}
```

---

### alg

Algorithm used.

Example:

HS256

---

### typ

JWT

---

Header tells:

> How was this JWT created?

---

# Part 2

## PAYLOAD

Stores user information.

Example

```json
{
"id":"123",
"name":"Shashank",
"role":"user"
}
```

---

Payload may contain

* User ID
* Name
* Email
* Role
* Expiry

---

Never Store

* Password
* OTP
* Secret Keys

---

## Can Payload be Read?

Yes.

Payload is NOT encrypted.

Anyone can decode it.

---

# Part 3

## SIGNATURE

Most important part.

Protects Header + Payload.

Created using

Header

*

Payload

*

JWT_SECRET

↓

Algorithm

↓

Signature

---

# JWT_SECRET

Example

```env
JWT_SECRET=HarHarMahadev123
```

Only server knows this.

Never expose it.

---

# During Every Request

Browser sends

Header

Payload

Signature

↓

Server recreates Signature

↓

Matches?

Yes

↓

Access Granted

No

↓

Invalid Token

---

# Why Hacker Cannot Become Admin

Suppose hacker changes

```json
{
"role":"admin"
}
```

Payload changes.

Signature becomes invalid.

Server rejects token.

---

# Biggest Placement Question

If Payload is readable,

why is JWT secure?

Answer:

Because Signature prevents modification.

Without JWT_SECRET,

no valid Signature can be created.

---

## JWT Summary

Header

↓

Metadata

Payload

↓

User Information

Signature

↓

Security

---

# Important Interview Points

JWT is Signed.

JWT is Stateless.

Payload is Readable.

Signature protects the token.

JWT_SECRET should never be shared.

Passwords are never stored inside JWT.

---

# Frequently Asked Interview Questions

### 1.

What is JWT?

A signed stateless token used for authentication.

---

### 2.

Difference between Session and JWT?

Session

* Stateful
* Server stores session

JWT

* Stateless
* Browser stores token

---

### 3.

Why is Payload readable?

Because JWT is signed, not encrypted.

---

### 4.

Which part protects JWT?

Signature

---

### 5.

Can hacker modify Payload?

No.

Signature becomes invalid.

---

### 6.

Can hacker create his own JWT?

No.

JWT_SECRET is unknown.

---

### 7.

What happens if JWT_SECRET changes?

All previous tokens become invalid.

---

# Quick Revision

## Authentication

Who are you?

---

## Authorization

What are you allowed to do?

---

## HTTP

Stateless

---

## JWT

Digital Identity Card

---

## JWT Parts

Header

Payload

Signature

---

## Header

Metadata

---

## Payload

User Data

---

## Signature

Security

---

## JWT_SECRET

Known only to Server

---

## Never Store

Passwords

OTP

Secrets

Inside JWT

---

# End of Lesson 3

Next:

**Lesson 4 — JWT Lifecycle**

* jwt.sign()
* jwt.verify()
* Token Expiry
* expiresIn
* Verification Process
* How Middleware Uses JWT
* Complete Internal Flow

