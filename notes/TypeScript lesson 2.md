# Lesson 02 - TypeScript Setup and Compiler

> **Course:** TypeScript Mastery (Placement + Industry + AI Full Stack)
> **Lesson:** 02 - TypeScript Setup and Compiler
> **Status:** ✅ Completed

---

# Lesson Objective

Understand how TypeScript works internally and learn how to set up a professional TypeScript development environment.

---

# TypeScript Execution Flow

```text
Developer
      ↓
Write TypeScript (.ts)
      ↓
TypeScript Compiler (tsc)
      ↓
Generate JavaScript (.js)
      ↓
Browser / Node.js
      ↓
Output
```

**Important:** Browsers and Node.js execute **JavaScript**, not TypeScript.

---

# What is the TypeScript Compiler?

The **TypeScript Compiler (`tsc`)** is a tool that:

* Checks for type-related errors.
* Converts TypeScript (`.ts`) files into JavaScript (`.js`) files.

Example:

### TypeScript

```ts
let age: number = 20;
```

### Generated JavaScript

```js
let age = 20;
```

---

# What is Node.js?

Node.js is a **JavaScript Runtime Environment**.

It allows JavaScript to run **outside the browser**.

Without Node.js, technologies like:

* React
* Express.js
* TypeScript
* npm

cannot be used effectively for backend or development workflows.

---

# What is a Runtime?

A runtime is an environment where code executes.

Examples:

* Browser Runtime
* Node.js Runtime

---

# What is npm?

**npm = Node Package Manager**

It is the default package manager for Node.js.

Responsibilities:

* Install packages
* Manage project dependencies
* Manage project scripts

Examples:

```bash
npm install react
npm install express
npm install axios
npm install typescript
```

---

# What is a Package?

A package is reusable code created by another developer.

Instead of writing everything from scratch, developers install packages using npm.

---

# What is npx?

**npx** executes packages without requiring a global installation.

Example:

```bash
npx tsc --init
```

This runs the TypeScript compiler available in the current project.

---

# npm vs npx

| npm                               | npx                       |
| --------------------------------- | ------------------------- |
| Installs packages                 | Executes packages         |
| Adds dependencies to the project  | Runs commands directly    |
| Example: `npm install typescript` | Example: `npx tsc --init` |

---

# Local vs Global Installation

## Global Installation

```bash
npm install -g typescript
```

* Available across the entire computer.
* Same version used by every project.

---

## Local Installation

```bash
npm install --save-dev typescript
```

* Installed only inside the current project.
* Different projects can use different TypeScript versions.
* Preferred in professional development.

---

# Why Use Local Installation?

* Version consistency
* Better project portability
* Prevents dependency conflicts
* Industry best practice

---

# What is package.json?

Created using:

```bash
npm init -y
```

It stores:

* Project information
* Installed dependencies
* Scripts
* Package versions

---

# What is tsconfig.json?

Generated using:

```bash
npx tsc --init
```

`tsconfig.json` is the configuration file for the TypeScript compiler.

It controls:

* Compiler options
* Target JavaScript version
* Included files
* Excluded files
* Module system
* Project settings

---

# Creating a TypeScript Project

### Step 1

Create a project folder.

```text
typescript-learning
```

---

### Step 2

Initialize npm.

```bash
npm init -y
```

---

### Step 3

Install TypeScript.

```bash
npm install --save-dev typescript
```

---

### Step 4

Generate compiler configuration.

```bash
npx tsc --init
```

---

### Step 5

Create:

```text
index.ts
```

---

### Step 6

Write TypeScript code.

```ts
let message: string = "Har Har Mahadev";

console.log(message);
```

---

### Step 7

Compile the project.

```bash
npx tsc
```

Generates:

```text
index.js
```

---

### Step 8

Run JavaScript.

```bash
node index.js
```

Output:

```text
Har Har Mahadev
```

---

# Complete Workflow

```text
Write index.ts
        ↓
Save File
        ↓
npx tsc
        ↓
Compiler generates index.js
        ↓
node index.js
        ↓
Output
```

---

# Important Commands

```bash
npm init -y
```

Creates `package.json`.

---

```bash
npm install --save-dev typescript
```

Installs TypeScript locally.

---

```bash
npx tsc --init
```

Creates `tsconfig.json`.

---

```bash
npx tsc
```

Compiles TypeScript into JavaScript.

---

```bash
node index.js
```

Runs the compiled JavaScript file.

---

# Interview Questions

## Q1. What is Node.js?

**Answer:**

Node.js is a JavaScript runtime environment that allows JavaScript to run outside the browser.

---

## Q2. What is a Runtime?

**Answer:**

A runtime is an environment where code is executed.

Examples:

* Browser
* Node.js

---

## Q3. What is npm?

**Answer:**

npm (Node Package Manager) is used to install and manage JavaScript packages and project dependencies.

---

## Q4. What is npx?

**Answer:**

npx is used to execute packages without installing them globally.

---

## Q5. Difference between npm and npx?

| npm                  | npx                    |
| -------------------- | ---------------------- |
| Installs packages    | Executes packages      |
| Creates dependencies | Runs commands directly |

---

## Q6. What is the TypeScript compiler?

**Answer:**

The TypeScript compiler checks for type errors and converts TypeScript code into JavaScript.

---

## Q7. Why do we use tsconfig.json?

**Answer:**

It stores the compiler configuration and project settings for TypeScript.

---

## Q8. Why is TypeScript installed as a development dependency?

**Answer:**

Because TypeScript is only required during development to compile code. Production applications run JavaScript, not TypeScript.

---

# Common Beginner Mistakes

❌ Forgetting to save the file before running `npx tsc`.

✔️ Always save (`Ctrl + S`) before compiling.

---

❌ Trying to execute `.ts` files directly with Node.js.

✔️ Compile TypeScript first, then execute the generated `.js` file.

---

❌ Confusing npm with npx.

✔️ npm installs packages.

✔️ npx executes packages.

---

❌ Installing every package globally.

✔️ Install project dependencies locally unless there is a specific reason to install globally.

---

# Placement Tips

* Understand the complete TypeScript workflow instead of memorizing commands.
* Know the difference between **compile time** and **runtime**.
* Be able to explain the role of **Node.js**, **npm**, **npx**, and the **TypeScript compiler**.
* Remember why professional projects prefer **local dependencies**.

---

# Key Takeaways

* TypeScript must be compiled before execution.
* Node.js executes JavaScript outside the browser.
* npm manages packages.
* npx executes packages.
* `package.json` stores project metadata and dependencies.
* `tsconfig.json` controls TypeScript compiler behavior.
* Local package installation is the industry standard.

---

# Lesson Summary

After completing Lesson 02, you should understand:

* TypeScript compilation workflow
* Node.js runtime
* npm and package management
* npx usage
* Local vs global installations
* package.json
* tsconfig.json
* Creating and running a TypeScript project

---

# Next Lesson

## Lesson 03 – Variables & Primitive Data Types

Topics:

* Variables in TypeScript
* Type Annotations
* Type Inference
* Primitive Data Types
* let, const and var
* Compile-Time vs Runtime Errors
* First Placement Coding Questions
