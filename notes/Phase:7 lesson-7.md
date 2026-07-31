# Phase 7 — Lesson 7

# bcrypt Internals & Password Security (Placement Revision)

**AI Full Stack Developer Roadmap**

---

# Why bcrypt?

Suppose a user signs up.

```text
Password

↓

Shashank@123
```

The password should **never** be stored directly.

Instead:

```text
Password

↓

bcrypt

↓

Secure Hash

↓

Store in Database
```

---

# What is bcrypt?

**bcrypt** is a password hashing algorithm specially designed for securely storing passwords.

Unlike normal hashing algorithms, bcrypt is intentionally **slow**.

This makes password cracking much harder.

---

# Why Was bcrypt Created?

Older algorithms like SHA-256 are very fast.

A hacker can try millions of passwords every second.

bcrypt slows this process, making brute-force attacks extremely expensive.

---

# SHA-256 vs bcrypt

| SHA-256                 | bcrypt                    |
| ----------------------- | ------------------------- |
| Very Fast               | Intentionally Slow        |
| No Salt Built-in        | Salt Built-in             |
| Good for File Integrity | Good for Password Storage |
| Easier to Brute Force   | Harder to Brute Force     |

---

# What Happens Inside `bcrypt.hash()`

Example:

```javascript
bcrypt.hash(password, 12);
```

Internally:

```text
Password

↓

Generate Random Salt

↓

Password + Salt

↓

bcrypt Algorithm

↓

Secure Hash
```

---

# Step 1 — Password

Example:

```text
Shashank@123
```

---

# Step 2 — Salt Generation

bcrypt automatically generates a random Salt.

Example:

```text
x82ks9a9b
```

Every user gets a different Salt.

---

# Step 3 — Combine Password + Salt

```text
Password

+

Salt
```

↓

Input to bcrypt.

---

# Step 4 — Generate Hash

Output Example:

```text
$2b$12$KYV8mM5Q...
```

This is stored in the database.

---

# What is Salt?

Salt is a random string added before hashing.

Purpose:

✔ Prevent identical hashes

✔ Prevent Rainbow Table attacks

---

## Example

User A

```text
Password

↓

123456

↓

Salt A

↓

Hash A
```

User B

```text
Password

↓

123456

↓

Salt B

↓

Hash B
```

Result:

```text
Hash A ≠ Hash B
```

Even though passwords are identical.

---

# Cost Factor

Example:

```javascript
bcrypt.hash(password, 12);
```

12 is called:

* Cost Factor
* Work Factor

---

# Higher Cost Factor

Higher Cost

↓

More Calculations

↓

Slower Hashing

↓

More Secure

---

# Typical Cost Factors

| Cost | Meaning           |
| ---: | ----------------- |
|    8 | Fast              |
|   10 | Good              |
|   12 | Industry Standard |
|   14 | High Security     |
|   16 | Very Slow         |

---

# Why Slow Hashing is Good

A hacker performs a brute-force attack.

Example:

```text
123456

password

admin123

hello123
```

If hashing is fast,

millions of passwords can be tested.

bcrypt slows every attempt.

This makes brute-force attacks impractical.

---

# Structure of a bcrypt Hash

Example:

```text
$2b$12$KYV8mM5Q...
```

Contains:

```text
Version

↓

Cost Factor

↓

Salt

↓

Hash
```

Everything is stored inside one string.

---

# How `bcrypt.compare()` Works

Question:

If hashing cannot be reversed,

how does login work?

---

Flow:

```text
User Password

↓

Extract Salt From Stored Hash

↓

Hash Password Again

↓

Compare Hashes

↓

Login Success
```

bcrypt **never decrypts** the password.

It hashes the entered password again using the stored Salt.

---

# Login Flow

```text
User Enters Password

↓

bcrypt.compare()

↓

Extract Salt

↓

Hash Again

↓

Compare

↓

Access Granted
```

---

# Brute Force Attack

A hacker repeatedly tries passwords.

Example:

```text
123456

password

admin

welcome123
```

bcrypt slows each attempt.

---

# Rainbow Table Attack

A Rainbow Table contains precomputed password hashes.

Example:

```text
123456

↓

Hash

password

↓

Hash

admin

↓

Hash
```

Without Salt,

these tables are dangerous.

---

# How Salt Stops Rainbow Tables

Without Salt

```text
Same Password

↓

Same Hash
```

With Salt

```text
Same Password

↓

Different Salt

↓

Different Hash
```

Rainbow Tables become ineffective.

---

# Industry Standard Password Flow

```text
Password

↓

Generate Salt

↓

bcrypt

↓

Hash

↓

Store in Database
```

Never store plain passwords.

Never encrypt passwords.

Always hash them.

---

# Why bcrypt Instead of SHA-256?

bcrypt provides:

✔ Salt

✔ Adjustable Cost Factor

✔ Slow Hashing

✔ Better Password Security

---

# Quick Comparison

| Feature                | SHA-256         | bcrypt      |
| ---------------------- | --------------- | ----------- |
| Speed                  | Very Fast       | Slow        |
| Salt Built-in          | No              | Yes         |
| Password Storage       | Not Recommended | Recommended |
| Brute Force Resistance | Low             | High        |

---

# Advantages of bcrypt

✔ Built-in Salt

✔ Configurable Cost Factor

✔ Strong Password Security

✔ Industry Standard

✔ Protects Against Rainbow Tables

---

# Important Interview Questions

---

## Q1

What is bcrypt?

**Answer**

bcrypt is a password hashing algorithm designed specifically for secure password storage.

---

## Q2

Why is bcrypt intentionally slow?

**Answer**

To slow down brute-force attacks and make password cracking expensive.

---

## Q3

What is Salt?

**Answer**

Salt is a random value added to a password before hashing.

It ensures that identical passwords generate different hashes.

---

## Q4

Why is Salt important?

**Answer**

Salt prevents Rainbow Table attacks and identical password hashes.

---

## Q5

Can bcrypt decrypt passwords?

**Answer**

No.

bcrypt is a hashing algorithm.

Hashes cannot be decrypted.

---

## Q6

How does `bcrypt.compare()` work?

**Answer**

It extracts the Salt from the stored hash, hashes the entered password again, and compares both hashes.

---

## Q7

Does bcrypt store the Salt separately?

**Answer**

No.

Salt is embedded inside the bcrypt hash string.

---

## Q8

Can two users with the same password have different bcrypt hashes?

**Answer**

Yes.

Because bcrypt generates a different random Salt for every password.

---

## Q9

What is the Cost Factor?

**Answer**

The Cost Factor controls how many computational rounds bcrypt performs.

Higher Cost means greater security but slower hashing.

---

## Q10

Why shouldn't SHA-256 be used directly for password storage?

**Answer**

SHA-256 is too fast and has no built-in Salt, making brute-force attacks easier.

---

## Q11

Which is more secure for passwords?

* SHA-256
* bcrypt

**Answer**

bcrypt.

---

## Q12

Can a hacker reverse a bcrypt hash?

**Answer**

No.

The only practical attack is guessing passwords through brute force.

---

## Q13

What information is contained inside a bcrypt hash?

**Answer**

* Version
* Cost Factor
* Salt
* Password Hash

---

## Q14

What happens if the Cost Factor increases?

**Answer**

Advantages:

* Stronger Security
* Harder Brute Force

Disadvantages:

* Slower Login
* Higher CPU Usage

---

# High Frequency Placement Questions

### ⭐ Why is bcrypt preferred over SHA-256?

---

### ⭐ What is Salt?

---

### ⭐ How does bcrypt.compare() work without decryption?

---

### ⭐ What is Cost Factor?

---

### ⭐ Why are identical passwords stored as different hashes?

---

### ⭐ How does bcrypt protect against Rainbow Table attacks?

---

# Quick Revision

```text
Password

↓

Generate Salt

↓

Password + Salt

↓

bcrypt

↓

Hash Stored

------------------------

Login

↓

Entered Password

↓

Extract Salt

↓

Hash Again

↓

Compare

↓

Login Success
```

---

# Key Takeaways

* bcrypt is the industry standard for password hashing.
* Salt ensures identical passwords produce different hashes.
* Cost Factor controls hashing difficulty.
* bcrypt hashes cannot be decrypted.
* `bcrypt.compare()` re-hashes the entered password instead of decrypting.
* bcrypt protects against Brute Force and Rainbow Table attacks.

---

# End of Lesson 7

## Next Lesson

**Phase 7 — Lesson 8**

### Authentication Middleware & Protected Routes

Topics:

* Middleware Basics
* JWT Verification
* `req.user`
* Protected Routes
* Role-Based Authorization
* Production Authentication Flow
