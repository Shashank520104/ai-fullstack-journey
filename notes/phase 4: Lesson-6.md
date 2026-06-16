# Phase 4 - Lesson 6: AI Memory Systems

## Objective

Understand how AI systems remember important information across conversations.

---

# Problem Statement

LLMs are stateless.

Example:

User:

```text
My name is Shashank.
```

Later:

```text
What is my name?
```

Without memory:

```text
I don't know.
```

---

# What is AI Memory?

AI Memory is a mechanism that stores and retrieves relevant information to maintain context across interactions.

---

# Why Memory is Needed

Without memory:

* Generic Responses
* No Personalization
* No User Context

With memory:

* Personalized Responses
* Context Awareness
* Better Recommendations

---

# Types of Memory

## Short-Term Memory

Recent conversation history.

Example:

```js
conversation.slice(-10)
```

Purpose:

Provide recent context to the LLM.

---

# Limitations of Short-Term Memory

Problems:

* Context Window Limits
* High Token Cost
* Not Scalable

---

## Long-Term Memory

Stores important user information.

Examples:

* Career Goals
* Skills
* Preferences
* Learning Progress

Example:

```json
{
  "goal":"AI Full Stack Developer",
  "skills":["React","Node.js"],
  "interest":"AI Engineering"
}
```

---

# Memory Architecture

```text
User Message
      ↓
Memory Extractor
      ↓
Memory Storage
      ↓
Memory Retrieval
      ↓
LLM
      ↓
Response
```

---

# Example

User:

```text
I want an AI Full Stack Internship.
```

Stored:

```json
{
  "type":"goal",
  "value":"AI Full Stack Internship"
}
```

Later:

```text
Suggest projects.
```

AI retrieves memory and suggests AI-focused projects.

---

# What Should Be Stored?

Examples:

* Career Goals
* Technical Skills
* Learning Interests
* Long-Term Preferences

Example:

```text
Goal:
AI Full Stack Internship

Skills:
React
Node.js

Learning:
RAG
Vector Databases
```

---

# What Should NOT Be Stored?

Examples:

* Temporary Questions
* One-Time Requests
* Random Conversations

Example:

```text
What is React?
What is Node.js?
What is the capital of India?
```

---

# Memory + RAG

RAG:

```text
Retrieve Documents
```

Memory:

```text
Retrieve User Information
```

Modern AI Systems use both.

---

# Future Shaurya AI Architecture

```text
User
 ↓
Memory Retrieval
 ↓
RAG Retrieval
 ↓
Gemini
 ↓
Answer
```

---

# Placement Questions

## What is AI Memory?

AI Memory is a system that stores and retrieves relevant user information to maintain context across conversations.

---

## What is the difference between Short-Term and Long-Term Memory?

Short-Term Memory:

Recent Conversation Context

Long-Term Memory:

Stored User Information

---

## Are LLMs Stateful?

No.

LLMs are stateless and require external memory systems to remember information.

---

# Key Learning

Modern AI systems become intelligent by combining:

* Memory
* RAG
* Vector Databases
* LLMs

Memory enables personalization and context-aware responses.
