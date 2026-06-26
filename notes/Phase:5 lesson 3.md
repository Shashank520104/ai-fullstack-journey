# Phase 5 – Lesson 3

# AI Full Stack Developer Roadmap

# Topic: Enterprise AI Service Architecture

---

# Objective

Refactor the backend into reusable and maintainable layers following enterprise software engineering principles.

---

# Previous Architecture

Frontend

↓

Routes

↓

Controller

↓

AI Service

↓

Gemini SDK

↓

JSON Storage

↓

Prompt

Problems

- AI Service had too many responsibilities.
- Difficult to maintain.
- Hard to switch AI providers.
- Violated Single Responsibility Principle.

---

# New Enterprise Architecture

Frontend

↓

Routes

↓

Controller

↓

AI Service

↓

Memory Layer

↓

Prompt Manager

↓

AI Client

↓

Gemini Config

↓

Gemini API

Each layer performs one responsibility only.

---

# Step 1 — Shared Gemini Configuration

Created

config/

gemini.js

Purpose

- Initialize Gemini only once.
- Export reusable Gemini client.
- Follow DRY principle.
- Easy provider replacement.

Example

```javascript
const ai = new GoogleGenAI({
    apiKey: process.env.GEMINI_API_KEY
});

export default ai;
```

---

# Step 2 — Memory Layer

Created

memory/

chatMemory.js

Responsibilities

- Read chat history
- Save chat history
- Clear chat history

Functions

- getChatHistory()
- saveChatHistory()
- clearChatHistory()

Benefits

- Removes file operations from AI Service.
- Centralized storage logic.
- Easy migration to MongoDB later.

---

# Step 3 — AI Client

Created

services/

aiClient.js

Purpose

Handle communication with Gemini.

Responsibilities

- Call Gemini API
- Return generated response

Business logic should never directly call Gemini.

Example

```javascript
callGemini(systemPrompt, chatHistory)
```

---

# Step 4 — AI Service Refactoring

Old

AI Service

↓

Gemini

↓

JSON

↓

Prompt

↓

Everything

New

AI Service

↓

Memory

↓

Prompt

↓

AI Client

AI Service now only coordinates the workflow.

---

# New AI Service Workflow

1. Load previous chats
2. Save latest user message
3. Fetch system prompt
4. Convert conversation
5. Call AI Client
6. Save AI response
7. Return response

---

# DRY Principle

Don't Repeat Yourself.

Instead of

```javascript
ai.models.generateContent(...)
```

inside every service,

create

```javascript
callGemini()
```

Benefits

- One reusable function
- Easier maintenance
- Easy provider replacement

---

# Single Responsibility Principle

Every file performs one task.

Examples

config/

Gemini configuration

memory/

Memory management

services/

Business logic

controllers/

Request-response handling

routes/

API endpoints

prompts/

System prompts

---

# Separation of Concerns

Controller

↓

Service

↓

Memory

↓

Prompt

↓

AI Client

↓

Configuration

Each layer has a dedicated responsibility.

---

# Loose Coupling

If Gemini changes,

Only

aiClient.js

needs modification.

Other services remain unchanged.

---

# High Cohesion

All memory logic

↓

chatMemory.js

All AI communication

↓

aiClient.js

All prompt management

↓

prompts.js

Related functionality remains together.

---

# Final Folder Structure

server/

├── config/
│   └── gemini.js

├── controllers/
│   └── aiController.js

├── routes/
│   └── aiRoutes.js

├── services/
│   ├── aiService.js
│   └── aiClient.js

├── memory/
│   └── chatMemory.js

├── prompts/
│   └── prompts.js

├── data/

└── server.js

---

# Placement Interview Questions

## Q1. Why create aiClient.js?

Answer

To separate AI provider communication from business logic. This improves maintainability, follows the Single Responsibility Principle, and allows switching AI providers by modifying only one file.

---

## Q2. Why create chatMemory.js?

Answer

To isolate storage operations from business logic. The AI Service should generate responses, while the memory layer manages data storage.

---

## Q3. What is DRY?

Answer

Don't Repeat Yourself.

Avoid duplicate code by creating reusable modules and functions.

---

## Q4. What is Single Responsibility Principle?

Answer

Each class, module, or file should have only one responsibility.

---

## Q5. What is Loose Coupling?

Answer

Different modules should depend as little as possible on each other. Changes in one module should not require changes throughout the application.

---

## Q6. What is High Cohesion?

Answer

Closely related functionality should remain inside the same module.

Example

chatMemory.js contains only memory-related functions.

---

## Q7. If Gemini is replaced with OpenAI, which file changes?

Answer

Only

services/

aiClient.js

should change.

No modifications should be required in controllers, services, or routes.

---

# Mentor Takeaways

✔ Follow DRY

✔ Follow SRP

✔ Separate Business Logic

✔ Separate Storage Logic

✔ Separate AI Provider Logic

✔ Keep AI Service focused on workflow

✔ Build reusable architecture

✔ Think like a software engineer, not just a coder

---

# Progress

Completed

✅ Shared Gemini Config

✅ Memory Layer

✅ AI Client

✅ AI Service Refactoring

✅ Enterprise Architecture

---

# Next Lesson

Phase 5

Lesson 4

Feature-wise Service Architecture

ResumeService

InterviewService

CareerService

ProjectAdvisorService

ATSService

BugFixService

Each AI feature will have its own service following enterprise architecture.

---

# End of Phase 5 – Lesson 3
