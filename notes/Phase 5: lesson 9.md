# Phase 5 - Lesson 9

# AI Full Stack Developer Roadmap

# Topic: PDF Parsing & Document Processing Pipeline

---

# Objective

Learn how production AI systems process uploaded PDF documents before sending them to AI models.

Understand:

- Why AI cannot directly read PDF files
- PDF Parsing
- Text Extraction
- Document Processing Pipeline
- Resource Cleanup
- Temporary File Management

---

# Problem Statement

User uploads:

Resume.pdf

Question:

Can Gemini directly understand a PDF file?

Answer:

No.

Gemini requires plain text.

Therefore the backend must first extract text from the uploaded PDF.

---

# Previous Architecture

Frontend

↓

Upload PDF

↓

Multer

↓

Resume Service

↓

Gemini

Problem

Gemini received

uploads/Resume.pdf

instead of actual resume text.

---

# Correct Production Architecture

Frontend

↓

Upload PDF

↓

Multer

↓

Resume Service

↓

Read PDF

↓

Extract Text

↓

Gemini

↓

Structured JSON

↓

Frontend

---

# Why PDF Parsing?

PDF files are stored as binary data.

AI models understand natural language.

Therefore

PDF

↓

Text Extraction

↓

AI

---

# pdf-parse

Purpose

Read PDF files and extract plain text.

Installation

```bash
npm install pdf-parse
```

Imports

```javascript
import fs from "fs";
import pdf from "pdf-parse";
```

---

# Reading Uploaded File

```javascript
const pdfBuffer = fs.readFileSync(resume);
```

Purpose

Read uploaded PDF from disk into memory.

Input

PDF Path

Output

Buffer

---

# Extracting Text

```javascript
const pdfData = await pdf(pdfBuffer);

const resumeText = pdfData.text;
```

Purpose

Convert PDF buffer into readable text.

Output

Plain Resume Text

---

# Sending Text to Gemini

Before

```javascript
Candidate Resume:

${resume}
```

Wrong

Resume contained only file path.

After

```javascript
Candidate Resume:

${resumeText}
```

Correct

Gemini now analyzes the actual resume content.

---

# Document Processing Pipeline

PDF Upload

↓

Read File

↓

Extract Text

↓

Create Prompt

↓

Gemini

↓

JSON

↓

Frontend

Each stage transforms the data into a better format.

---

# Temporary Files

Uploaded PDF files are temporary resources.

Keeping them forever wastes server storage.

Professional applications delete uploaded files after processing.

---

# Resource Cleanup

Delete uploaded PDF after successful processing.

Example

```javascript
fs.unlinkSync(resume);
```

Purpose

Remove temporary file.

---

# Cleanup During Errors

Even if

- pdf-parse fails
- Gemini fails
- JSON parsing fails
- Schema validation fails

Uploaded file should still be deleted.

Example

```javascript
catch (error) {

    if (fs.existsSync(resume)) {
        fs.unlinkSync(resume);
    }

    throw new Error(error.message);
}
```

This prevents unnecessary storage usage.

---

# Software Engineering Principles Learned

## Single Responsibility Principle

Upload Middleware

↓

Upload File

Resume Service

↓

Process Resume

PDF Parser

↓

Extract Text

Gemini

↓

AI Analysis

---

## Data Transformation Pipeline

Binary PDF

↓

Text

↓

Prompt

↓

Structured JSON

↓

Frontend

---

## Resource Cleanup

Temporary resources must always be deleted after use.

---

## Fail Safe Programming

Cleanup should occur even when an error happens.

---

# Folder Responsibilities

middleware/

- Upload files

controllers/

- Handle Request & Response

services/

- Business Logic

schemas/

- Validate AI Output

uploads/

- Temporary storage for uploaded files

---

# Final Resume Analyzer Flow

User Uploads PDF

↓

POST /resume/resume-analysis

↓

uploadMiddleware.js

↓

resumeController.js

↓

resumeService.js

↓

Read PDF

↓

Extract Text

↓

Gemini

↓

ResumeSchema Validation

↓

Delete Temporary PDF

↓

Frontend

---

# Why Don't We Send PDF Directly To Gemini?

Gemini expects text.

PDF is a binary document.

Backend extracts text first, then creates an AI prompt.

---

# Placement Interview Questions

## Q1. Why can't Gemini directly analyze uploaded PDF files?

Answer

Gemini APIs expect text input.

A PDF is a binary document, so the backend must extract readable text before sending it to Gemini.

---

## Q2. Why do we use pdf-parse?

Answer

pdf-parse converts PDF documents into plain text that AI models can understand.

---

## Q3. Why should uploaded PDFs be deleted?

Answer

Uploaded PDFs are temporary resources.

Deleting them prevents storage issues and keeps the server clean.

---

## Q4. Why should cleanup happen inside the catch block?

Answer

Even when processing fails, temporary files should be removed to avoid orphaned files and wasted disk space.

---

## Q5. What is a Document Processing Pipeline?

Answer

A sequence of operations where a document is uploaded, converted into text, analyzed by AI, validated, and returned as structured data.

---

## Q6. Why is PDF parsing business logic?

Answer

Extracting resume text is part of the Resume Analysis workflow.

Therefore it belongs in the service layer.

---

## Q7. What is the responsibility of Multer?

Answer

Multer receives uploaded files, validates them, stores them temporarily, and provides access through req.file.

---

## Q8. What is Resource Cleanup?

Answer

Resource Cleanup is the process of removing temporary resources such as uploaded files, database connections, or memory buffers after processing.

---

## Q9. Why shouldn't controllers parse PDFs?

Answer

Controllers should only coordinate requests and responses.

PDF parsing belongs to the service because it is business logic.

---

## Q10. Explain the Resume Analyzer architecture.

Answer

Frontend uploads PDF.

↓

Multer stores it temporarily.

↓

Controller forwards request.

↓

Resume Service reads the PDF.

↓

pdf-parse extracts text.

↓

Gemini analyzes the text.

↓

Schema validates the response.

↓

Temporary PDF is deleted.

↓

Response is sent to frontend.

---

# Mentor Takeaways

- AI models understand text, not binary documents.
- PDF parsing converts documents into AI-readable text.
- Document Processing Pipelines are used in production AI systems.
- Uploaded files should always be treated as temporary resources.
- Cleanup should happen after success and failure.
- Business logic belongs inside services.
- Middleware should only manage file uploads.
- Controllers should remain lightweight.

---

# Phase 5 Progress

Completed

✅ Lesson 1 – Production Folder Architecture

✅ Lesson 2 – Modular Backend Architecture

✅ Lesson 3 – Enterprise AI Refactoring

✅ Lesson 4 – Feature-wise Architecture

✅ Lesson 5 – Resume Analyzer API

✅ Lesson 6 – Structured AI Responses (JSON)

✅ Lesson 7 – Schema Validation & Zod

✅ Lesson 8 – File Upload Architecture (Multer)

✅ Lesson 9 – PDF Parsing & Document Processing Pipeline

---

# Mentor Review

Lesson 9 transformed Shaurya AI from an application that simply accepts uploaded files into a true Document AI system.

The project now follows a production-grade document processing pipeline where uploaded PDFs are converted into plain text, analyzed using Gemini, validated with a schema, and cleaned up after processing.

This architecture is used in ATS Resume Analyzers, Legal AI, Medical AI, Research Paper AI, and Retrieval-Augmented Generation (RAG) systems.

---

# End of Phase 5 - Lesson 9
