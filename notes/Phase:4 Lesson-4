# Phase 4 - Lesson 4: RAG (Retrieval-Augmented Generation)

## Objective

Understand how modern AI systems retrieve relevant information from external documents before generating responses.

RAG is one of the most important concepts in AI Engineering and is used in:

* ChatGPT PDF Chat
* Perplexity AI
* Notion AI
* Cursor
* GitHub Copilot Workspace

---

# Problem Statement

Suppose a user uploads:

```text
Resume.pdf
```

and asks:

```text
What is my CGPA?
```

Current Architecture:

```text
User
↓
Gemini
↓
Answer
```

Problem:

```text
Gemini never saw the PDF.
```

Therefore it cannot answer accurately.

---

# Naive Solution

Send entire PDF to Gemini.

Problems:

* Expensive
* Slow
* Token Waste
* Context Window Limits

Not scalable.

---

# Smart Solution: RAG

RAG stands for:

```text
Retrieval
Augmentation
Generation
```

---

# What is RAG?

RAG is an AI architecture that retrieves relevant information from external data sources and augments the prompt before sending it to the LLM for response generation.

---

# Three Core Components

## 1. Retrieval

Find relevant information.

Example:

Question:

```text
What is my CGPA?
```

Retrieved Chunk:

```text
CGPA: 8.41
```

---

## 2. Augmentation

Add retrieved information into the prompt.

Example:

```text
Context:
CGPA: 8.41

Question:
What is my CGPA?
```

---

## 3. Generation

LLM generates response.

Example:

```text
Your CGPA is 8.41.
```

---

# Complete RAG Pipeline

```text
PDF Upload
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
Prompt Augmentation
 ↓
LLM (Gemini)
 ↓
Answer
```

---

# Detailed Pipeline

## Step 1: PDF Upload

User uploads:

```text
Resume.pdf
```

---

## Step 2: Text Extraction

Extract content from PDF.

Example:

```text
Skills:
React
Node
MongoDB

CGPA:
8.41
```

---

## Step 3: Chunking

Split large document into smaller chunks.

Example:

```text
Chunk 1:
Education

Chunk 2:
Skills

Chunk 3:
Projects
```

Benefits:

* Better retrieval
* Reduced token usage
* Improved relevance

---

## Step 4: Embeddings

Convert chunks into vectors.

Example:

```text
Skills:
React
Node
MongoDB
```

↓

```text
[0.21,0.67,0.88...]
```

---

## Step 5: Vector Database

Store:

```text
Chunk
+
Embedding
+
Metadata
```

Example:

```json
{
  "text":"CGPA: 8.41",
  "embedding":[0.22,0.55,0.91]
}
```

---

## Step 6: Retrieval

User asks:

```text
What is my GPA?
```

Query is converted into embedding.

Vector similarity search runs.

Most relevant chunk found:

```text
CGPA: 8.41
```

---

## Step 7: Augmentation

Build enhanced prompt.

```text
Context:
CGPA: 8.41

Question:
What is my GPA?
```

---

## Step 8: Generation

Gemini receives:

```text
Context
+
Question
```

and generates:

```text
Your CGPA is 8.41.
```

---

# Why RAG is Powerful

Without RAG:

```text
LLM only knows training data.
```

With RAG:

```text
LLM can answer from your documents.
```

Benefits:

* More accurate
* Lower cost
* Less token usage
* No model retraining required
* Real-time knowledge updates

---

# Real World Use Cases

* Resume Analysis
* PDF Chat Systems
* Knowledge Base Search
* Company Documentation Assistants
* Legal Document Search
* Medical Document Search
* Customer Support Bots

---

# Placement Questions

## Q1. What is RAG?

Answer:

RAG (Retrieval-Augmented Generation) is an AI architecture that retrieves relevant information from external data sources and augments the LLM prompt before generating a response.

---

## Q2. What are the three components of RAG?

Answer:

```text
Retrieval
Augmentation
Generation
```

---

## Q3. Why is RAG better than sending entire PDFs?

Answer:

RAG retrieves only relevant chunks, reducing token usage, improving accuracy, lowering costs, and increasing scalability.

---

## Q4. What problem does RAG solve?

Answer:

RAG enables LLMs to access and answer questions using external documents without retraining the model.

---

# Shaurya AI Future Architecture

Current:

```text
User
↓
Gemini
↓
Answer
```

Future:

```text
Resume PDF
↓
Chunking
↓
Embeddings
↓
ChromaDB
↓
Retriever
↓
Gemini
↓
Answer
```

---

# Key Learning

RAG is the bridge between:

```text
User Documents
```

and

```text
Large Language Models
```

It enables AI systems to answer questions using external knowledge efficiently and accurately.

This architecture powers most modern AI applications.
