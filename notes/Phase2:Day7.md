# Phase 2 - Lesson 7

# Persistent Memory Using JSON Storage

## Objective

Store AI conversations permanently using a JSON file instead of React state.

---

# Problem

Before persistence:

```text
User Message
↓
AI Response
↓
Refresh Page
↓
Conversation Lost
```

React state stores data only in memory.

```js
const [conversation, setConversation] = useState([]);
```

When the page refreshes, state resets.

---

# Solution

Store chat data inside:

```text
server/data/chats.json
```

Example:

```json
[
  {
    "role": "user",
    "text": "Hello"
  }
]
```

---

# Node.js fs Module

The fs module is used to interact with files.

Import:

```js
import fs from "fs";
```

---

# Reading Files

```js
const data = fs.readFileSync(
  "./data/chats.json",
  "utf-8"
);
```

---

# JSON.parse()

Converts JSON text into JavaScript objects.

```js
const chats = JSON.parse(data);
```

Example:

```json
[
  {
    "role":"user",
    "text":"Hello"
  }
]
```

becomes:

```js
[
  {
    role:"user",
    text:"Hello"
  }
]
```

---

# Adding Data

```js
chats.push({
  role:"user",
  text:"Hello"
});
```

---

# JSON.stringify()

Converts JavaScript objects into JSON text.

```js
JSON.stringify(chats, null, 2);
```

---

# Writing Files

```js
fs.writeFileSync(
  "./data/chats.json",
  JSON.stringify(chats, null, 2)
);
```

---

# Persistence Flow

```text
Read chats.json
↓
Convert JSON to Object
↓
Add New Message
↓
Convert Object to JSON
↓
Save File
```

---

# Placement Questions

## Q1. What is the fs module?

Answer:

The fs module is a built-in Node.js module used for reading, writing, updating, and deleting files.

---

## Q2. Difference between readFileSync() and writeFileSync()?

Answer:

readFileSync() reads data from a file.

writeFileSync() writes data into a file.

---

## Q3. What is JSON.parse()?

Answer:

JSON.parse() converts JSON text into JavaScript objects.

---

## Q4. What is JSON.stringify()?

Answer:

JSON.stringify() converts JavaScript objects into JSON text.

---

## Q5. What is Persistence?

Answer:

Persistence means storing data permanently so it remains available after application restart or refresh.

---

# Key Takeaways

* Learned file-based storage.
* Implemented persistent memory.
* Learned fs module.
* Learned JSON.parse().
* Learned JSON.stringify().
* Built first backend persistence layer.
