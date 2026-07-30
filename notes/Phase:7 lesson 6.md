# Phase 7 — Lesson 6

# Hashing vs Encryption vs Encoding (Placement Revision)

**AI Full Stack Developer Roadmap**

---

# Why Do We Need Password Security?

Suppose a user creates an account.

```text id="ycbw9n"
Password:

Shashank@123
```

Should the company store:

```text id="q3vhq7"
Shashank@123
```

directly in the database?

❌ No.

If the database is leaked, hackers get all passwords.

Companies use:

* Encoding
* Encryption
* Hashing

These are different concepts.

---

# Encoding

## What is Encoding?

Encoding changes the format of data.

Purpose:

✔ Easy Data Transfer

Not Security.

---

## Example

Text

```text id="oww1h4"
Har Har Mahadev
```

↓

Base64

```text id="xngj8s"
SGFyIEhhciBNYWhhZGV2
```

Can it be converted back?

✔ Yes.

---

## Encoding Examples

* Base64
* ASCII
* UTF-8

---

## Encoding Properties

| Property     | Value         |
| ------------ | ------------- |
| Reversible   | Yes           |
| Security     | No            |
| Key Required | No            |
| Purpose      | Data Transfer |

---

# Encryption

## What is Encryption?

Encryption hides data using a key.

Only someone with the correct key can read the original data.

---

## Flow

```text id="7q2i9f"
Original Data

↓

Encryption Key

↓

Encrypted Data

↓

Decryption Key

↓

Original Data
```

---

## Example

```text id="dwlxol"
Password

↓

Encryption

↓

@2ks8!hT

↓

Decryption

↓

Password
```

---

## Encryption Algorithms

* AES
* RSA

---

## Where Encryption is Used

* WhatsApp Messages
* Banking Systems
* HTTPS
* Credit Cards

---

## Encryption Properties

| Property     | Value           |
| ------------ | --------------- |
| Reversible   | Yes             |
| Key Required | Yes             |
| Security     | Yes             |
| Purpose      | Data Protection |

---

# Hashing

## What is Hashing?

Hashing converts data into a fixed random-looking value.

Hashing is one-way.

Cannot be reversed.

---

## Example

```text id="mnj9nr"
Shashank@123

↓

$2b$12$abcxyz...
```

Can we get original password back?

❌ No.

---

## Hashing Example

```text id="r87um9"
Coffee Beans

↓

Powder
```

Can we get beans back?

❌ No.

Hashing works similarly.

---

# Hash Function

Same input

↓

Same output.

Example

```text id="ngvfd1"
Mahadev

↓

jsh83ks8...
```

Every time.

---

# Login Process

Question:

If hashing cannot be reversed,

how does login work?

---

## Login Flow

User enters:

```text id="p2gmx8"
Shashank@123
```

↓

Server hashes again.

↓

Compares with stored hash.

↓

If match:

Login Successful.

---

## Flow

```text id="umc50v"
Password Entered

↓

Hash Again

↓

Compare

↓

Match

↓

Login
```

---

# Why Not Encrypt Passwords?

Encryption can be reversed.

If hackers steal encryption key,

all passwords become visible.

Hashing cannot be reversed.

Therefore:

Passwords are always hashed.

---

# Hashing Properties

| Property          | Value |
| ----------------- | ----- |
| One Way           | Yes   |
| Reversible        | No    |
| Fast Verification | Yes   |
| Deterministic     | Yes   |

---

# Problem with Normal Hashing

Suppose:

```text id="p2e5u4"
password123
```

User A

↓

Hash

↓

abc123

User B

↓

Hash

↓

abc123

Same password.

Same hash.

This is a problem.

---

# Salt

## What is Salt?

Salt is a random value added before hashing.

---

## Example

User A

```text id="skn6eb"
Password

+

Salt A

↓

Hash A
```

User B

```text id="txgq4x"
Password

+

Salt B

↓

Hash B
```

Even with same password,

hashes become different.

---

# bcrypt

bcrypt automatically:

✔ Generates Salt

✔ Hashes Password

✔ Protects against attacks

---

## Example

```javascript id="nhxwpo"
bcrypt.hash(password, 12);
```

12 means:

Cost Factor.

Higher Cost:

✔ More Security

✘ Slower Hashing

---

# Login with bcrypt

```javascript id="59wqmq"
bcrypt.compare(
    enteredPassword,
    storedHash
);
```

bcrypt:

✔ Extracts Salt

✔ Recreates Hash

✔ Compares

---

# Why bcrypt?

✔ Salt Included

✔ Slow Against Attackers

✔ Industry Standard

---

# Encoding vs Encryption vs Hashing

| Feature      | Encoding      | Encryption | Hashing        |
| ------------ | ------------- | ---------- | -------------- |
| Purpose      | Data Transfer | Hide Data  | Store Password |
| Reversible   | Yes           | Yes        | No             |
| Key Required | No            | Yes        | No             |
| Security     | No            | Yes        | Very High      |

---

# Real World Examples

Encoding

↓

Base64

---

Encryption

↓

WhatsApp

---

Hashing

↓

Instagram Password

---

# Common Attacks

## Brute Force Attack

Attacker tries many passwords.

Example:

```text id="dy3w5h"
123456

123457

123458
```

bcrypt slows this attack.

---

## Rainbow Table Attack

Hackers store precomputed hashes.

Salt defeats Rainbow Tables.

---

# Industry Rule

Passwords:

```text id="if0zh3"
Password

↓

Salt

↓

bcrypt

↓

Hash

↓

Store in Database
```

---

# Important Interview Questions

## Q1

What is Encoding?

**Answer**

Encoding changes data format for transmission.

It is not used for security.

---

## Q2

What is Encryption?

**Answer**

Encryption protects data using a key.

Data can be decrypted using the correct key.

---

## Q3

What is Hashing?

**Answer**

Hashing converts data into a fixed value.

Hashing is one-way.

Cannot be reversed.

---

## Q4

Why do companies hash passwords?

**Answer**

Because hashed passwords cannot be decrypted.

---

## Q5

Why don't companies encrypt passwords?

**Answer**

Encrypted passwords can be decrypted.

Hashed passwords cannot.

---

## Q6

How does login work if hashes cannot be reversed?

**Answer**

The server hashes the entered password again and compares both hashes.

---

## Q7

What is Salt?

**Answer**

Salt is a random value added before hashing to create unique hashes.

---

## Q8

Why is Salt important?

**Answer**

Salt prevents Rainbow Table attacks.

---

## Q9

What is bcrypt?

**Answer**

bcrypt is a password hashing library with built-in Salt.

---

## Q10

Why is bcrypt preferred over SHA256?

**Answer**

bcrypt:

✔ Salt

✔ Slow Hashing

✔ Better Password Security

SHA256 is too fast.

---

## Q11

Will bcrypt generate same hashes for same passwords?

**Answer**

No.

Different Salt creates different hashes.

---

## Q12

Can Hashing be reversed?

**Answer**

No.

Hashing is one-way.

---

## Q13

Can Encryption be reversed?

**Answer**

Yes.

Using the correct key.

---

## Q14

What is Cost Factor in bcrypt?

**Answer**

Cost Factor controls hashing complexity.

Higher Cost:

✔ More Secure

✘ Slower

---

# High Frequency Placement Questions

### ⭐ Difference between Encoding, Encryption and Hashing?

---

### ⭐ Why is bcrypt used?

---

### ⭐ Why are passwords hashed and not encrypted?

---

### ⭐ What is Salt?

---

### ⭐ Can hashes be reversed?

---

### ⭐ How does bcrypt.compare() work?

---

# Quick Revision

```text id="3og0tl"
Encoding

↓

Format Change

↓

Reversible

-------------------

Encryption

↓

Data Protection

↓

Key Required

↓

Reversible

-------------------

Hashing

↓

Password Storage

↓

One Way

↓

Cannot Reverse

-------------------

Salt

↓

Unique Hashes

-------------------

bcrypt

↓

Salt + Hashing
```

---

# End of Lesson 6

## Next Lesson

**Phase 7 — Lesson 7**

### bcrypt Internals

Topics:

* Cost Factor
* Salt Generation
* bcrypt.compare()
* Rainbow Table Attack
* Brute Force Attack
* Industry Password Security
* Advanced Interview Questions
