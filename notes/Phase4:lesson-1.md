# Phase 4 - Lesson 1: AI System Architecture

## Objective

Understand how modern AI systems are structured and how they differ from simple AI integrations.

---

## Current Shaurya AI Architecture

```text
User
 ↓
React Frontend
 ↓
Express Backend
 ↓
Gemini API
 ↓
Response
```

Architecture:

```text
┌─────────┐
│ React   │
└────┬────┘
     │
     ▼
┌─────────┐
│ Express │
└────┬────┘
     │
     ▼
┌─────────┐
│ Gemini  │
└─────────┘
```

---

## What is an LLM Wrapper?

An LLM Wrapper is an application that forwards user requests to a Large Language Model and returns responses without additional AI infrastructure.

Example:

```text
User
 ↓
Backend
 ↓
Gemini
 ↓
User
```

---

## Limitations of Current Architecture

* No document understanding
* No PDF analysis
* No semantic search
* No memory
* No retrieval system
* No vector database

---

## Modern AI Architecture

```text
User
 ↓
Frontend
 ↓
Backend
 ↓
Vector Database
 ↓
Retriever
 ↓
LLM
 ↓
Response
```

---

## Components of Modern AI Systems

### Frontend

Examples:

* React
* Next.js
* Angular

Purpose:

* User Interface

---

### Backend

Examples:

* Node.js
* Python
* Java

Purpose:

* Business Logic

---

### LLM

Examples:

* Gemini
* GPT
* Claude
* Llama

Purpose:

* Reasoning and Generation

---

### Database

Examples:

* MongoDB
* PostgreSQL
* MySQL

Purpose:

* Store Users
* Store Chats
* Store Application Data

---

### Vector Database

Examples:

* Pinecone
* ChromaDB
* Qdrant
* Weaviate

Purpose:

* Store Embeddings
* Semantic Search

---

## Production AI Pipeline

```text
PDF Upload
      ↓
PDF Parser
      ↓
Text Extraction
      ↓
Chunking
      ↓
Embeddings
      ↓
Vector Database
      ↓
Retriever
      ↓
LLM
      ↓
Answer
```

---

## Placement Questions

### What is an LLM Wrapper?

An LLM Wrapper is an application that sends user requests to a Large Language Model and returns responses without additional AI infrastructure such as RAG, memory, or vector databases.

---

### What is the architecture of Shaurya AI today?

```text
React Frontend
 ↓
Express Backend
 ↓
Gemini API
 ↓
Response
```

---

## Key Learning

AI App Developer:

```text
Frontend
 ↓
Backend
 ↓
LLM
```

AI Engineer:

```text
Frontend
 ↓
Backend
 ↓
Embeddings
 ↓
Vector DB
 ↓
Retriever
 ↓
LLM
```

This is the foundation of modern AI systems.
