# Phase 2 - Lesson 8

# Auto Loading Chat History

## Objective

Load saved conversations automatically when the application starts.

---

# Problem

Even though messages were saved inside chats.json:

```text
Refresh Page
↓
Conversation Disappears
```

because React state resets.

```js
const [conversation, setConversation] = useState([]);
```

---

# Solution

Create a GET API route.

```text
GET /history
```

Backend reads saved chats and sends them to React.

---

# Backend Route

```js
app.get("/history", (req, res) => {

  const data = fs.readFileSync(
    "./data/chats.json",
    "utf-8"
  );

  const chats = JSON.parse(data);

  res.status(200).json(chats);

});
```

---

# HTTP GET Method

Purpose:

```text
Retrieve Data
```

Example:

```js
fetch("/history");
```

---

# React useEffect()

Purpose:

Run code automatically when a component loads.

```js
useEffect(() => {

}, []);
```

---

# Why Empty Dependency Array?

```js
[]
```

means:

```text
Run Once On Component Mount
```

---

# Loading History

```js
const loadHistory = async () => {

  const response =
  await fetch(
    "http://localhost:8000/history"
  );

  const data =
  await response.json();

  setConversation(data);
};
```

---

# Running Automatically

```js
useEffect(() => {

  loadHistory();

}, []);
```

---

# Complete Flow

```text
React Loads
↓
useEffect Runs
↓
loadHistory()
↓
GET /history
↓
Backend Reads chats.json
↓
Returns Messages
↓
setConversation()
↓
UI Updates
```

---

# Placement Questions

## Q1. What is useEffect()?

Answer:

useEffect() is a React Hook used to perform side effects such as API calls, subscriptions, timers, and DOM updates.

---

## Q2. When does useEffect(() => {}, []) run?

Answer:

It runs only once when the component mounts.

---

## Q3. Difference between GET and POST?

Answer:

GET is used to retrieve data.

POST is used to send or create data.

---

## Q4. What is Component Mounting?

Answer:

Mounting is the process when a React component is created and rendered for the first time.

---

## Q5. Why use useEffect for API calls?

Answer:

Because API calls are side effects and should run automatically when a component loads.

---

# Key Takeaways

* Learned GET APIs.
* Learned useEffect().
* Learned Component Lifecycle.
* Learned Auto Data Fetching.
* Implemented Chat History Loading.
* Built a ChatGPT-like persistent chat experience.
