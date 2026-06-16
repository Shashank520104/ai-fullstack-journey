# Phase 4 - Lesson 5: PDF Chat Architecture

## Objective

Understand how modern AI applications answer questions from uploaded PDF documents using RAG architecture.

---

# Problem Statement

User uploads:

Resume.pdf

and asks:

"What is my CGPA?"

A normal LLM cannot answer because it has never seen the uploaded PDF.

---

# Goal

Build an AI system that can:

1. Read PDFs
2. Extract text
3. Store knowledge
4. Answer questions from the uploaded document

---

# PDF Chat Architecture

```text
PDF Upload
 ↓
PDF Parsing
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
Gemini
 ↓
Answer
```

---

# Frontend Components

React Components:

* PDF Upload Button
* Chat Input
* Send Button
* Response Area

Example Flow:

```text
Upload Resume
 ↓
Ask Question
 ↓
Get Answer
```

---

# Backend Routes

```text
/upload-pdf
/chat-with-pdf
```

---

# PDF Parsing

Purpose:

Convert PDF into readable text.

Tools:

* pdf-parse
* LangChain PDF Loader
* PyPDF

Example Output:

```text
Education:
CGPA 8.41

Skills:
React
Node
MongoDB
```

---

# Chunking

Large documents are divided into smaller sections.

Example:

Chunk 1:
Education

Chunk 2:
Skills

Chunk 3:
Projects

Benefits:

* Better Retrieval
* Faster Search
* Lower Token Usage

---

# Embeddings

Each chunk is converted into a numerical vector.

Example:

```text
React Node MongoDB
```

↓

```text
[0.21, 0.67, 0.88...]
```

Purpose:

Represent meaning numerically.

---

# Vector Database

Stores:

* Chunk Text
* Embedding
* Metadata

Example:

```json
{
  "text":"CGPA 8.41",
  "embedding":[0.22,0.55,0.91]
}
```

---

# Retrieval

User Question:

"What is my GPA?"

Retriever searches vector database.

Finds:

```text
CGPA 8.41
```

---

# Prompt Augmentation

Context:

```text
CGPA 8.41
```

Question:

```text
What is my GPA?
```

Combined Prompt:

```text
Context:
CGPA 8.41

Question:
What is my GPA?
```

---

# Generation

Gemini generates:

```text
Your CGPA is 8.41.
```

---

# Placement Questions

## What is PDF Parsing?

PDF Parsing is the process of extracting readable text from PDF documents.

---

## Why do we use Chunking?

Chunking improves retrieval accuracy and reduces token usage.

---

## Why can't we directly send large PDFs to Gemini?

Because it increases token cost, reduces efficiency, and may exceed context limits.

---

# Key Learning

PDF Chat Systems use:

* Parsing
* Chunking
* Embeddings
* Vector Databases
* Retrieval
* RAG

This architecture powers modern document-aware AI systems.
