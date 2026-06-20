# Lesson 04 - Operators in TypeScript

> **Course:** TypeScript Mastery (Placement + Industry + AI Full Stack)
> **Lesson:** 04 - Operators in TypeScript
> **Status:** ✅ Completed

---

# Lesson Objective

Learn how operators work in TypeScript and understand how they are used in real-world applications like React, Node.js, Express.js, and backend development.

---

# What is an Operator?

An **operator** is a special symbol that performs an operation on one or more operands (values or variables).

Example:

```ts
let sum = 10 + 20;
```

Here:

* `10` → Operand
* `20` → Operand
* `+` → Operator

---

# Types of Operators

* Arithmetic Operators
* Assignment Operators
* Comparison Operators
* Logical Operators
* Increment & Decrement Operators
* Ternary Operator
* Nullish Coalescing Operator (`??`)
* Optional Chaining Operator (`?.`)

---

# Arithmetic Operators

| Operator | Description         | Example  |
| -------- | ------------------- | -------- |
| `+`      | Addition            | `10 + 5` |
| `-`      | Subtraction         | `10 - 5` |
| `*`      | Multiplication      | `10 * 5` |
| `/`      | Division            | `10 / 5` |
| `%`      | Modulus (Remainder) | `10 % 3` |
| `**`     | Exponent            | `2 ** 3` |

---

## Modulus Operator (%)

Returns the remainder after division.

Example:

```ts
10 % 3
```

Output:

```text
1
```

Common Uses:

* Even/Odd checking
* Cyclic operations
* Index calculations

Example:

```ts
if (number % 2 === 0)
```

---

# Assignment Operators

| Operator | Equivalent  |
| -------- | ----------- |
| `=`      | Assignment  |
| `+=`     | `a = a + b` |
| `-=`     | `a = a - b` |
| `*=`     | `a = a * b` |
| `/=`     | `a = a / b` |
| `%=`     | `a = a % b` |

Example:

```ts
let marks = 80;

marks += 10;
```

Output:

```text
90
```

---

# Comparison Operators

Comparison operators always return a **boolean** value.

| Operator | Meaning               |
| -------- | --------------------- |
| `==`     | Loose Equality        |
| `===`    | Strict Equality       |
| `!=`     | Loose Inequality      |
| `!==`    | Strict Inequality     |
| `>`      | Greater Than          |
| `<`      | Less Than             |
| `>=`     | Greater Than or Equal |
| `<=`     | Less Than or Equal    |

---

## Difference Between `==` and `===`

### Loose Equality (`==`)

```ts
5 == "5"
```

Output:

```text
true
```

Performs type conversion.

---

### Strict Equality (`===`)

```ts
5 === "5"
```

Output:

```text
false
```

Compares both **value** and **data type**.

✔️ Always prefer `===` in modern development.

---

# Logical Operators

## AND (`&&`)

Returns `true` only if **both conditions are true**.

```ts
age >= 18 && hasID
```

---

## OR (`||`)

Returns `true` if **at least one condition is true**.

```ts
isAdmin || isModerator
```

---

## NOT (`!`)

Reverses a boolean value.

```ts
!isLoggedIn
```

---

# Increment & Decrement Operators

## Increment

```ts
count++;
```

Adds `1`.

---

## Decrement

```ts
count--;
```

Subtracts `1`.

---

# Pre Increment

```ts
++count;
```

Increment first, then use.

---

# Post Increment

```ts
count++;
```

Use first, then increment.

Example:

```ts
let a = 5;

console.log(++a);
```

Output:

```text
6
```

Example:

```ts
let a = 5;

console.log(a++);
```

Output:

```text
5
```

After execution:

```text
a = 6
```

---

# Ternary Operator

Short form of an `if-else` statement.

Syntax:

```ts
condition ? value1 : value2;
```

Example:

```ts
const result = age >= 18 ? "Adult" : "Minor";
```

---

# Nullish Coalescing Operator (`??`)

Returns the right-hand value only if the left-hand value is **null** or **undefined**.

Example:

```ts
let username = null;

console.log(username ?? "Guest");
```

Output:

```text
Guest
```

---

# Difference Between `||` and `??`

```ts
let score = 0;

console.log(score || 100);
```

Output:

```text
100
```

Because `0` is **falsy**.

---

```ts
console.log(score ?? 100);
```

Output:

```text
0
```

Because `??` checks only for:

* `null`
* `undefined`

---

# Optional Chaining (`?.`)

Safely accesses nested properties.

Example:

```ts
const user = {
    name: "Shashank"
};

console.log(user.address?.city);
```

Output:

```text
undefined
```

Instead of throwing an error.

---

# Operator Precedence

Example:

```ts
10 + 5 * 2
```

Output:

```text
20
```

Because:

```text
*
↓

before

↓

+
```

Use parentheses for clarity.

```ts
(10 + 5) * 2
```

Output:

```text
30
```

---

# Interview Questions

## Q1. What is an operator?

**Answer:**

An operator is a special symbol that performs operations on one or more operands.

---

## Q2. Difference between Arithmetic and Assignment Operators?

**Answer:**

* Arithmetic operators perform mathematical calculations.
* Assignment operators assign or update variable values.

---

## Q3. Difference between `==` and `===`?

| `==`                     | `===`              |
| ------------------------ | ------------------ |
| Loose Equality           | Strict Equality    |
| Performs type conversion | No type conversion |

---

## Q4. Difference between `||` and `??`?

| `||` | `??` |
|------|-------|
| Checks all falsy values | Checks only `null` and `undefined` |

---

## Q5. Difference between Pre Increment and Post Increment?

**Pre Increment**

```ts
++a;
```

Increment first.

---

**Post Increment**

```ts
a++;
```

Use first, increment later.

---

## Q6. What is Optional Chaining?

**Answer:**

Optional chaining safely accesses nested object properties without throwing runtime errors if an intermediate property is `null` or `undefined`.

---

## Q7. Why should we prefer `===` over `==`?

**Answer:**

Because `===` compares both value and type, preventing unexpected type coercion bugs.

---

# Common Beginner Mistakes

❌ Using `==` instead of `===`.

✔️ Prefer strict equality.

---

❌ Confusing `%` with division.

✔️ `%` returns the remainder.

---

❌ Forgetting the difference between `++a` and `a++`.

---

❌ Using `||` instead of `??` for default values.

✔️ Use `??` when valid values like `0`, `false`, or `""` should not be replaced.

---

# Placement Tips

* Always use `===` in interviews unless specifically asked about `==`.
* Be comfortable explaining `%` because it appears frequently in DSA.
* Understand the practical difference between `||` and `??`; React interviewers often ask this.
* Learn optional chaining thoroughly since it is heavily used with API responses.

---

# Key Takeaways

* Operators perform operations on operands.
* Arithmetic operators handle calculations.
* Assignment operators update variable values.
* Comparison operators return boolean values.
* Logical operators combine conditions.
* Prefer `===` over `==`.
* Use `??` instead of `||` when only `null` or `undefined` should trigger a default value.
* Optional chaining prevents runtime errors while accessing nested properties.
* Use parentheses when operator precedence might reduce readability.

---

# Lesson Summary

After completing Lesson 04, you should understand:

* Arithmetic Operators
* Assignment Operators
* Comparison Operators
* Logical Operators
* Increment & Decrement
* Ternary Operator
* Nullish Coalescing (`??`)
* Optional Chaining (`?.`)
* Operator Precedence
* Industry Best Practices

---

# Next Lesson

## Lesson 05 – Control Flow Statements

Topics:

* `if`
* `if...else`
* `else if`
* Nested `if`
* `switch`
* `for` loop
* `while` loop
* `do...while` loop
* `break`
* `continue`
* Real-world Placement Questions
* Interview Questions
