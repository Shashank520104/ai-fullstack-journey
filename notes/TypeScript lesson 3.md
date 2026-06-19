# Lesson 03 - Variables & Primitive Data Types

> **Course:** TypeScript Mastery (Placement + Industry + AI Full Stack)
> **Lesson:** 03 - Variables & Primitive Data Types
> **Status:** ✅ Completed

---

# Lesson Objective

Learn how TypeScript stores data using variables and primitive data types, understand type annotations and type inference, and master the differences between `let`, `const`, and `var`.

---

# What is a Variable?

A **variable** is a named memory location used to store data.

Example:

```ts
let age = 20;
```

Visualization:

```text
Memory

+------------+
| age | 20   |
+------------+
```

---

# What is a Data Type?

A **data type** tells TypeScript what kind of value a variable can store.

Example:

```ts
let age: number = 20;
```

The compiler now knows that `age` can only store numbers.

---

# Why are Data Types Important?

Data types help to:

* Prevent invalid values
* Improve code readability
* Catch errors during compilation
* Improve IDE support and autocomplete

Example:

```ts
let age: number = 20;

age = "Twenty"; // ❌ Error
```

---

# Primitive Data Types

## 1. number

Stores numeric values.

```ts
let age: number = 20;
let price: number = 499.99;
```

---

## 2. string

Stores textual values.

```ts
let name: string = "Shashank";
```

---

## 3. boolean

Stores only:

* true
* false

```ts
let isPlaced: boolean = true;
```

---

## 4. undefined

Represents a variable that has been declared but not assigned a value.

```ts
let internshipId: undefined = undefined;
```

---

## 5. null

Represents an intentionally empty value.

```ts
let joiningDate: null = null;
```

---

## 6. bigint

Stores very large integer values.

```ts
let population: bigint = 12345678901234567890n;
```

---

## 7. symbol

Creates unique identifiers.

```ts
let id: symbol = Symbol("id");
```

---

# Type Annotation

Type Annotation means explicitly specifying the type of a variable.

Syntax:

```ts
variableName: type
```

Example:

```ts
let salary: number = 50000;
```

---

# Type Inference

Type Inference is the ability of TypeScript to automatically determine a variable's type based on its assigned value.

Example:

```ts
let age = 20;
```

TypeScript automatically infers:

```text
age → number
```

---

# Type Annotation vs Type Inference

## Type Annotation

```ts
let age: number = 20;
```

* Explicit
* Developer specifies the type

---

## Type Inference

```ts
let age = 20;
```

* Implicit
* TypeScript determines the type automatically

---

# Type Safety

TypeScript prevents assigning incorrect data types.

Example:

```ts
let age: number = 20;

age = "Twenty"; // ❌ Error
```

This feature is called **Type Safety**.

---

# Compile-Time Error

Errors detected before the program executes.

Example:

```ts
let age: number = "Twenty";
```

The TypeScript compiler reports an error immediately.

---

# Runtime Error

Errors that occur while the program is executing.

Example:

```js
const user = null;

console.log(user.name);
```

This compiles but crashes at runtime because `user` is `null`.

---

# let vs const vs var

## var

Characteristics:

* Function scoped
* Can be redeclared
* Can be reassigned
* Hoisted

Example:

```ts
var age = 20;

var age = 30;
```

⚠️ Avoid using `var` in modern applications.

---

## let

Characteristics:

* Block scoped
* Cannot be redeclared in the same scope
* Can be reassigned

Example:

```ts
let age = 20;

age = 21;
```

---

## const

Characteristics:

* Block scoped
* Cannot be redeclared
* Cannot be reassigned

Example:

```ts
const PI = 3.14159;
```

---

# Industry Best Practice

✔️ Use `const` by default.

✔️ Use `let` only when the variable value needs to change.

❌ Avoid `var`.

---

# Naming Conventions

Good:

```ts
let studentName = "Shashank";

let totalMarks = 500;

const MAX_USERS = 100;
```

Bad:

```ts
let a;

let xyz;

let data1;
```

Use meaningful and descriptive variable names.

---

# Interview Questions

## Q1. What is a variable?

**Answer:**

A variable is a named memory location used to store data.

---

## Q2. What is a data type?

**Answer:**

A data type specifies what kind of value a variable can store.

---

## Q3. What is Type Annotation?

**Answer:**

Type Annotation is the explicit declaration of a variable's data type.

---

## Q4. What is Type Inference?

**Answer:**

Type Inference is TypeScript's ability to automatically determine a variable's type based on its assigned value.

---

## Q5. Difference between Type Annotation and Type Inference?

| Type Annotation          | Type Inference           |
| ------------------------ | ------------------------ |
| Explicit                 | Implicit                 |
| Developer specifies type | Compiler determines type |

---

## Q6. Difference between `let`, `const`, and `var`?

| let                  | const                | var               |
| -------------------- | -------------------- | ----------------- |
| Block scoped         | Block scoped         | Function scoped   |
| Reassignable         | Not reassignable     | Reassignable      |
| Cannot be redeclared | Cannot be redeclared | Can be redeclared |

---

## Q7. What is a Compile-Time Error?

**Answer:**

An error detected by the TypeScript compiler before program execution.

---

## Q8. What is a Runtime Error?

**Answer:**

An error that occurs while the program is running.

---

## Q9. What is Type Safety?

**Answer:**

Type Safety prevents assigning values of incorrect data types to variables.

---

## Q10. Why should we prefer `const` over `let`?

**Answer:**

`const` prevents accidental reassignment, making code safer, more predictable, and easier to maintain.

---

# Common Beginner Mistakes

❌ Using `var` in modern projects.

✔️ Prefer `const` and `let`.

---

❌ Adding type annotations everywhere.

✔️ Use type inference when the type is obvious.

---

❌ Confusing `null` with `undefined`.

✔️ `undefined` = not assigned.

✔️ `null` = intentionally empty.

---

❌ Giving meaningless variable names.

✔️ Always use descriptive names.

---

# Placement Tips

* Be able to explain the difference between **Type Annotation** and **Type Inference** with examples.
* Interviewers frequently ask about `let`, `const`, and `var`.
* Understand the difference between **Compile-Time** and **Runtime** errors.
* Use meaningful variable names in coding interviews.
* Follow the rule:

  * `const` → default choice
  * `let` → when reassignment is required
  * `var` → avoid

---

# Key Takeaways

* Variables store data in memory.
* Data types define what values a variable can hold.
* Type Annotation explicitly specifies a type.
* Type Inference automatically determines a type.
* TypeScript provides Type Safety.
* Compile-time errors are caught before execution.
* Runtime errors occur while executing the program.
* Prefer `const` over `let`, and avoid `var` in modern development.

---

# Lesson Summary

After completing Lesson 03, you should understand:

* Variables
* Primitive Data Types
* Type Annotation
* Type Inference
* Type Safety
* Compile-Time vs Runtime Errors
* `let`, `const`, and `var`
* Naming Conventions
* Industry Best Practices

---

# Next Lesson

## Lesson 04 – Operators in TypeScript

Topics:

* Arithmetic Operators
* Assignment Operators
* Comparison Operators
* Logical Operators
* Increment & Decrement
* Ternary Operator
* Nullish Coalescing (`??`)
* Optional Chaining (`?.`)
* Operator Precedence
* Placement Coding Questions
* Interview Questions
