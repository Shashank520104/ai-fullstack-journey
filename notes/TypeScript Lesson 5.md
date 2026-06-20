# Lesson 05 - Control Flow Statements

> **Course:** TypeScript Mastery (Placement + Industry + AI Full Stack)
> **Lesson:** 05 - Control Flow Statements
> **Status:** ✅ Completed

---

# Lesson Objective

Learn how to control the execution flow of a TypeScript program using conditional statements and loops. These concepts form the foundation of business logic in React, Node.js, Express.js, and backend development.

---

# What is Control Flow?

Control Flow determines the order in which statements are executed in a program.

Without control flow:

```text
Statement 1
      ↓
Statement 2
      ↓
Statement 3
```

With control flow:

```text
Condition

↓

True ?

↓

YES → Execute Block A

NO  → Execute Block B
```

---

# if Statement

Executes a block only if the condition is true.

Syntax

```ts
if (condition) {
    // code
}
```

Example

```ts
let age = 20;

if (age >= 18) {
    console.log("Eligible to Vote");
}
```

---

# if...else Statement

Used when there are two possible outcomes.

Syntax

```ts
if (condition) {

}
else {

}
```

Example

```ts
let age = 15;

if (age >= 18) {
    console.log("Adult");
}
else {
    console.log("Minor");
}
```

---

# else if Statement

Used when multiple conditions need to be checked.

Example

```ts
let marks = 82;

if (marks >= 90) {
    console.log("Grade A");
}
else if (marks >= 75) {
    console.log("Grade B");
}
else if (marks >= 50) {
    console.log("Grade C");
}
else {
    console.log("Fail");
}
```

**Important:**

As soon as one condition becomes true, the remaining conditions are skipped.

---

# Nested if

An `if` statement inside another `if` statement.

Example

```ts
let age = 22;
let hasLicense = true;

if (age >= 18) {

    if (hasLicense) {
        console.log("Can Drive");
    }

}
```

---

# switch Statement

Used when comparing one variable against multiple exact values.

Syntax

```ts
switch(expression){

case value:
    // code
    break;

default:
    // code

}
```

Example

```ts
let day = 2;

switch(day){

case 1:
    console.log("Monday");
    break;

case 2:
    console.log("Tuesday");
    break;

default:
    console.log("Invalid Day");

}
```

---

# Why is break Important?

Without `break`, execution continues into the next case (fall-through).

Always use `break` unless fall-through is intentional.

---

# if...else vs switch

Use **if...else** for:

* Ranges
* Complex conditions
* Multiple variables

Use **switch** for:

* Exact values
* Menu systems
* Status codes
* Roles

---

# Loops

A loop repeatedly executes a block of code until a condition becomes false.

---

# for Loop

Best when the number of iterations is known.

Syntax

```ts
for(initialization; condition; update){

}
```

Example

```ts
for(let i = 1; i <= 5; i++){

    console.log(i);

}
```

---

# while Loop

Best when the number of iterations is unknown.

Example

```ts
let i = 1;

while(i <= 5){

    console.log(i);

    i++;

}
```

---

# do...while Loop

Executes at least one time.

Example

```ts
let i = 1;

do{

    console.log(i);

    i++;

}
while(i <= 5);
```

---

# break Statement

Immediately exits a loop.

Example

```ts
for(let i = 1; i <= 10; i++){

    if(i === 5){
        break;
    }

    console.log(i);

}
```

Output

```text
1
2
3
4
```

---

# continue Statement

Skips the current iteration.

Example

```ts
for(let i = 1; i <= 5; i++){

    if(i === 3){
        continue;
    }

    console.log(i);

}
```

Output

```text
1
2
4
5
```

---

# Infinite Loop

Example

```ts
while(true){

}
```

Runs forever unless terminated using `break`.

---

# Real-World Usage

## Authentication

```ts
if(isLoggedIn){

}
else{

}
```

---

## Role-Based Access

```ts
switch(role){

case "admin":

case "user":

}
```

---

## Rendering Lists

```ts
for(let i = 0; i < products.length; i++){

}
```

---

# Interview Questions

## Q1. What is Control Flow?

Control Flow determines the order in which program statements execute.

---

## Q2. Difference between if and switch?

| if                 | switch         |
| ------------------ | -------------- |
| Complex conditions | Exact values   |
| Supports ranges    | Exact matching |
| Multiple variables | One expression |

---

## Q3. Difference between for and while?

| for              | while              |
| ---------------- | ------------------ |
| Known iterations | Unknown iterations |

---

## Q4. Difference between while and do...while?

| while        | do...while                    |
| ------------ | ----------------------------- |
| Checks first | Executes once before checking |

---

## Q5. Difference between break and continue?

| break      | continue                |
| ---------- | ----------------------- |
| Stops loop | Skips current iteration |

---

## Q6. What is an Infinite Loop?

A loop that never terminates because its condition always remains true.

---

# Common Beginner Mistakes

❌ Forgetting `break` in `switch`

✔️ Add `break` after every case unless fall-through is intentional.

---

❌ Forgetting to update the loop variable

✔️ Always ensure the loop can terminate.

---

❌ Using `switch` for range-based conditions

✔️ Use `if...else` instead.

---

❌ Writing `=` instead of `===` in conditions

✔️ Always compare using `===`.

---

# Placement Tips

* `if...else` is one of the most frequently used concepts in backend development.
* `switch` is common for menu systems, user roles, and status handling.
* Understand the difference between `for`, `while`, and `do...while`.
* Be able to explain `break` and `continue` with examples.
* Avoid infinite loops in coding interviews.

---

# Key Takeaways

* Control Flow determines execution order.
* `if` executes when a condition is true.
* `if...else` provides two execution paths.
* `else if` handles multiple conditions.
* `switch` is best for exact value matching.
* `for` is used when iterations are known.
* `while` is used when iterations are unknown.
* `do...while` executes at least once.
* `break` exits a loop.
* `continue` skips the current iteration.

---

# Lesson Summary

After completing Lesson 05, you should understand:

* Control Flow
* if
* if...else
* else if
* Nested if
* switch
* for loop
* while loop
* do...while loop
* break
* continue
* Infinite loops
* Industry Best Practices

---

# Next Lesson

## Lesson 06 – Functions in TypeScript

Topics:

* What are Functions?
* Function Declaration
* Function Expression
* Arrow Functions
* Parameters
* Return Types
* Optional Parameters
* Default Parameters
* Rest Parameters
* Callback Functions
* Function Overloading
* Placement Coding Questions
* Interview Questions
* Industry Best Practices
