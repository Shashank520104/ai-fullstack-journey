# Phase 5 - Lesson 5

# AI Full Stack Developer Roadmap

# Topic: Building the First Real AI Feature - Resume Analyzer API

---

# Objective

Learn how to build the first independent AI feature using enterprise backend architecture.

The Resume Analyzer is the first feature that has its own business logic and therefore deserves its own Route, Controller, and Service.

---

# Why Resume Analyzer Needs Its Own Service

Normal Chat Flow

User Message

↓

Prompt

↓

Gemini

↓

Response

Only the prompt changes.

---

Resume Analyzer Flow

Upload Resume

↓

Validate Input

↓

Extract Resume Text

↓

Create AI Prompt

↓

Call Gemini

↓

Analyze Resume

↓

Return ATS Result

This is a completely different business workflow.

Therefore Resume Analyzer deserves its own architecture.

---

# Enterprise Architecture

Frontend

↓

POST /resume-analysis

↓

resumeRoute.js

↓

resumeController.js

↓

resumeService.js

↓

AI Client

↓

Gemini

↓

Frontend

---

# Folder Structure

server/

├── routes/

│   └── resumeRoutes.js

│

├── controllers/

│   └── resumeController.js

│

├── services/

│   └── resumeService.js

---

# Route Responsibility

Purpose

Map HTTP request to controller.

Example

```javascript
router.post("/resume-analysis", analyzeResumeController);
```

Routes should never contain business logic.

---

# Controller Responsibility

Purpose

Receive request

↓

Read req.body

↓

Call Service

↓

Return JSON response

Controllers should never contain AI logic.

---

# Service Responsibility

Purpose

Contains complete business logic.

Responsibilities

- Resume Analysis
- Prompt Creation
- AI Calls
- Response Processing
- Future PDF Parsing
- ATS Logic

Services are the brain of the application.

---

# Current Resume Service

Temporary Flow

Resume

↓

Dummy Response

↓

Frontend

Later

Resume

↓

AI Prompt

↓

Gemini

↓

ATS Analysis

↓

Frontend

---

# Why Build Dummy Response First?

Instead of directly integrating Gemini,

Professional developers first verify that:

- Route works
- Controller works
- Service works
- API works
- Response format works

After the pipeline is verified,

AI is integrated.

This is called

Incremental Development.

---

# Incremental Development

Bad Practice

Write

1000 lines

↓

Run

↓

Debug

---

Good Practice

20 lines

↓

Test

↓

Next 20 lines

↓

Test

↓

Repeat

Benefits

- Easier debugging
- Faster development
- Better testing
- Cleaner architecture

---

# callGemini()

Resume Service should NOT initialize Gemini.

Correct Flow

resumeService.js

↓

callGemini()

↓

aiClient.js

↓

config/gemini.js

↓

Gemini

Benefits

- DRY Principle
- Easy Maintenance
- Centralized Configuration
- Loose Coupling

---

# Why Not Initialize Gemini Everywhere?

Bad

mentorService

↓

New Gemini Instance

resumeService

↓

New Gemini Instance

careerService

↓

New Gemini Instance

---

Good

mentorService

↓

callGemini()

resumeService

↓

callGemini()

careerService

↓

callGemini()

↓

AI Client

↓

Gemini

Only one Gemini configuration.

---

# Separation of Responsibilities

Route

↓

Maps URL

---

Controller

↓

Handles Request & Response

---

Service

↓

Business Logic

---

AI Client

↓

Communicates with Gemini

Each layer performs only one responsibility.

---

# Open-Closed Principle

Current

Dummy ATS Response

Tomorrow

Real Gemini Response

Only

resumeService.js

changes.

Other layers remain unchanged.

Software becomes

Open for Extension

Closed for Modification.

---

# Current Resume Analyzer Flow

Frontend

↓

resumeRoute.js

↓

resumeController.js

↓

resumeService.js

↓

callGemini()

↓

Gemini

↓

Controller

↓

Frontend

---

# Software Engineering Principles Learned

## Single Responsibility Principle (SRP)

Each layer has only one responsibility.

---

## DRY

Gemini initialization exists only once.

---

## Separation of Concerns

Route

↓

Controller

↓

Service

↓

AI Client

Each performs one task.

---

## Incremental Development

Build

↓

Test

↓

Improve

instead of building everything together.

---

## Open-Closed Principle

Extend business logic without modifying architecture.

---

# Placement Interview Questions

## Q1. Why does Resume Analyzer need its own service?

Answer

Resume Analyzer has its own business workflow involving resume processing, prompt creation, AI analysis, and ATS evaluation. Therefore it deserves its own Route, Controller, and Service.

---

## Q2. Why do we build dummy responses before integrating AI?

Answer

Dummy responses verify the complete API pipeline before adding complex AI logic. This follows incremental development and simplifies debugging.

---

## Q3. Why should Services contain business logic?

Answer

Services are responsible for implementing application logic. Controllers only coordinate requests and responses.

---

## Q4. Why should Controller not call Gemini directly?

Answer

Controllers should only manage HTTP requests and responses. Calling Gemini is business logic and belongs in the service layer.

---

## Q5. Why should callGemini() be reused?

Answer

It follows DRY, centralizes Gemini configuration, simplifies maintenance, and avoids duplicate code.

---

# Mentor Takeaways

- Resume Analyzer is the first true feature of Shaurya AI.
- Build Route → Controller → Service before adding AI.
- Services own business logic.
- Controllers remain lightweight.
- Reuse AI Client.
- Follow incremental development.
- Architecture should evolve with the application.
- Build features one layer at a time.

---

# Current Roadmap Progress

Completed

✅ Phase 1 – MERN Fundamentals

✅ Phase 2 – AI Integration

✅ Phase 3 – Advanced AI Features

✅ Phase 4 – AI Engineering Fundamentals

Phase 5

✅ Lesson 1 – Production Folder Architecture

✅ Lesson 2 – Modular Backend Architecture

✅ Lesson 3 – Enterprise AI Refactoring

✅ Lesson 4 – Feature-wise Architecture Decision

✅ Lesson 5 – Resume Analyzer API

Next Lesson

➡ Lesson 6 – Structured AI Responses (JSON)

---

# Mentor Review

Lesson 5 marked the transition of Shaurya AI from a generic AI chatbot into an AI platform with independent feature APIs.

Instead of routing every request through a single chat endpoint, the project now follows enterprise architecture by giving complex features their own Route, Controller, and Service.

This architecture improves scalability, maintainability, and prepares the project for future AI features such as Interview Simulator, Career Advisor, and RAG-based document analysis.

---

# End of Phase 5 - Lesson 5
