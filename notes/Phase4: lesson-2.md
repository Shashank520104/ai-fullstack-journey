# Phase 4 - Lesson 2: Embeddings

## Objective

Understand embeddings, semantic search, and how modern AI systems understand meaning.

---

## What are Embeddings?

Embeddings are numerical vector representations of text, images, or other data that capture semantic meaning.

Example:

```text
React Developer
↓
[0.12, 0.91, 0.45, 0.67, ...]
```

```text
Frontend Engineer
↓
[0.15, 0.88, 0.42, 0.69, ...]
```

Because the vectors are similar, the meanings are considered similar.

---

## Why Embeddings Exist

Computers understand numbers.

Humans understand meaning.

Embeddings convert meaning into numbers.

---

## Keyword Search vs Semantic Search

### Keyword Search

Search:

```text
Frontend
```

Document:

```text
React.js
```

Result:

```text
No Match
```

Because words are different.

---

### Semantic Search

Search:

```text
Frontend
```

Document:

```text
React.js
```

Result:

```text
Match Found
```

Because meanings are related.

---

## Real Example

Resume:

```text
I am skilled in React.js
```

User asks:

```text
What frontend technology do I know?
```

Keyword Search:

May fail.

Semantic Search:

Successfully retrieves React.js because React is strongly related to frontend development.

---

## How Embeddings Work

Text:

```text
React.js
```

Embedding:

```text
[
0.12,
0.56,
0.78,
0.34,
0.91,
...
]
```

Frontend:

```text
[
0.15,
0.59,
0.81,
0.31,
0.89,
...
]
```

The system compares entire vectors rather than individual words.

---

## Similarity Calculation

Vector Databases use:

* Cosine Similarity
* Euclidean Distance
* Dot Product

to find similar meanings.

---

## Why Embeddings Are Important

Embeddings enable:

* Semantic Search
* RAG Systems
* PDF Chat
* AI Memory
* Document Retrieval
* Recommendation Systems

---

## Real AI Architecture

```text
PDF
 ↓
Text
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

### What is an Embedding?

An embedding is a numerical vector representation of text, images, or data that captures semantic meaning and relationships.

---

### Why are Embeddings Used?

Embeddings enable semantic search by converting text into vectors that represent meaning rather than exact words.

---

### What problem do Embeddings solve?

Embeddings solve the problem of understanding meaning and similarity between different words, sentences, and documents.

---

## Key Learning

Keyword Search:

```text
Exact Words
```

Semantic Search:

```text
Meaning
```

Modern AI systems rely on embeddings to understand relationships between concepts and retrieve relevant information intelligently.
