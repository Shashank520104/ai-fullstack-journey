# Phase 2 - Lesson 5

# Conversational Memory System

## Objective

Enable the AI assistant to remember previous messages within the same chat session.

---

## Problem

Without memory:

User:
My name is Shashank

User:
What is my name?

AI:
I don't know your name.

Reason:

Only the latest message is sent to Gemini.

---

## Solution

Store conversation history and send entire conversation to backend.

---

## Step 1: Create Conversation State

```javascript
const [conversation,setConversation]
= useState([]);
```

Purpose:

Stores complete chat history.

---

## Conversation Structure

```javascript
[
 {
   role:"user",
   text:"Hello"
 },

 {
   role:"ai",
   text:"Hi"
 }
]
```

---

## Step 2: Store User Message

```javascript
const userMessage = {
 role:"user",
 text:message
};
```

---

## Step 3: Update Conversation

```javascript
const updatedConversation = [
 ...conversation,
 userMessage
];

setConversation(updatedConversation);
```

---

## Step 4: Send Full History

```javascript
body: JSON.stringify({
 conversation: updatedConversation,
 mode: mode
})
```

---

## Step 5: Backend Receives History

```javascript
const { conversation } = req.body;
```

---

## Step 6: Convert Into Chat History

```javascript
const chatHistory =
conversation
.map((msg)=>
`${msg.role}:${msg.text}`)
.join("\n");
```

Example:

```text
user: My name is Shashank
ai: Hello Shashank
user: What is my name?
```

---

## Step 7: Send History To Gemini

```javascript
contents: `
${systemPrompt}

Conversation History:
${chatHistory}
`
```

---

## Result

User:
My name is Shaurya

User:
What is my name?

AI:
Shaurya

Memory works successfully.

---

## Bugs Faced

### Bug 1

Wrong variable name

```javascript
converstation
```

Correct:

```javascript
conversation
```

---

### Bug 2

State update timing issue

Wrong:

```javascript
setConversation(...)

conversation
```

Correct:

```javascript
const updatedConversation = [
 ...conversation,
 userMessage
];
```

---

## Concepts Learned

### React

* Arrays in State
* State Updates
* Spread Operator
* Rendering Lists

### Backend

* Parsing Conversation History
* Request Body Handling

### AI

* Multi-turn Conversations
* Context Injection
* Memory Simulation

---

## Interview Questions

### Q1

How does ChatGPT remember previous messages?

Answer:
Conversation history is sent along with new prompts.

---

### Q2

What is conversational memory?

Answer:
Providing previous chat history to the AI model so it can answer using context.

---

### Q3

Why is conversation history important?

Answer:
It enables context-aware and human-like interactions.

---

## Outcome

Implemented a working conversational AI assistant capable of remembering previous messages during a chat session.
