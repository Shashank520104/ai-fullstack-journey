# Phase 5 - Lesson 4
# AI Full Stack Developer Roadmap
# Topic: Feature-wise Architecture Decision

---

## Objective

Understand when to create separate feature-specific services and when NOT to over-engineer the backend.

This lesson focuses on architectural judgment, not just coding.

---

## Current Shaurya AI Architecture

Current backend flow:

React Frontend

↓

POST /chat

↓

AI Controller

↓

AI Service

↓

AI Client

↓

Gemini API

↓

Response

This architecture is currently good for prompt-based AI modes.

---

## Current Features

Shaurya AI currently has modes like:

- Mentor
- Coder
- Interviewer
- Project Advisor
- Email Generator
- LinkedIn Post Generator
- Instagram Caption Generator
- Question Paper Generator

Most of these modes currently differ only by prompt.

Example:

Mentor Mode

↓

Mentor Prompt

Coder Mode

↓

Coder Prompt

Project Advisor Mode

↓

Project Advisor Prompt

The workflow is same:

User Message

↓

Prompt Selection

↓

Gemini Call

↓

AI Response

---

## Important Engineering Decision

Do NOT create a separate service just because the prompt changes.

Changing only prompt

≠

New service required

Changing business workflow

=

New service required

---

## What is Feature Isolation?

Feature Isolation means each major feature should have its own module/service when it has independent business logic.

Example:

Resume Analyzer

- Upload resume
- Extract text
- Analyze skills
- Generate ATS score
- Return structured result

This deserves:

resumeService.js

---

Interview Simulator

- Generate question
- Accept answer
- Evaluate answer
- Give score
- Give feedback
- Ask next question

This deserves:

interviewService.js

---

## What is Premature Abstraction?

Premature Abstraction means creating unnecessary architecture before it is actually needed.

Example:

Creating these files too early:

mentorService.js

coderService.js

emailService.js

linkedinService.js

projectService.js

when all of them only change prompts.

This increases complexity without real benefit.

---

## What is YAGNI?

YAGNI means:

You Aren't Gonna Need It

It means:

Do not build architecture for future possibilities until the current project actually needs it.

Good engineers keep systems simple until complexity demands separation.

---

## Why We Did NOT Split All Services Today

Because current modes mostly use the same business flow:

Get user message

↓

Select prompt

↓

Call Gemini

↓

Return answer

So keeping them inside the current prompt-based system is better.

Creating many services now would add unnecessary complexity.

---

## When Should We Create a New Service?

Create a new service when the feature has:

- Different business logic
- Different workflow
- Different dependencies
- Different data processing
- Different lifecycle
- Different output structure

---

## Examples

### Should NOT create separate service yet

Mentor Mode

Coder Mode

Email Generator

LinkedIn Generator

Instagram Caption Generator

Reason:

They currently only differ by prompt.

---

### SHOULD create separate service later

Resume Analyzer

Reason:

Needs upload, parsing, scoring, structured result.

---

ATS Checker

Reason:

Needs resume-job comparison and scoring logic.

---

Interview Simulator

Reason:

Needs question generation, answer evaluation, score tracking.

---

RAG PDF Chat

Reason:

Needs file processing, chunking, embedding, vector search, retrieval.

---

## Correct Architecture Thinking

Bad Architecture:

Create many services before actual need.

Good Architecture:

Start simple.

Split when business logic becomes different.

Best Architecture:

Let the codebase grow naturally.

---

## Current Correct Decision

Keep:

aiService.js

for generic prompt-based chat modes.

Later create:

resumeService.js

interviewService.js

ragService.js

authService.js

when those real features are implemented.

---

## Placement Interview Questions

### Q1. When should you create a new service?

Answer:

A new service should be created when a feature has its own business logic, workflow, dependencies, or data processing requirements.

---

### Q2. What is Premature Abstraction?

Answer:

Premature Abstraction means creating extra layers or modules before they are needed, which increases complexity without giving real benefit.

---

### Q3. What is YAGNI?

Answer:

YAGNI stands for "You Aren't Gonna Need It." It means developers should avoid building unnecessary future features or architecture until the requirement actually exists.

---

### Q4. Why should we not create a separate service for every prompt mode?

Answer:

Because if the only difference is the prompt and the workflow is the same, then separate services add unnecessary complexity. A separate service is justified only when the feature has different business logic.

---

### Q5. Why will Resume Analyzer need its own service?

Answer:

Resume Analyzer has a different workflow involving file upload, resume parsing, analysis, ATS scoring, and structured output. Since its logic is different from normal chat, it deserves its own service.

---

## Mentor Takeaways

- More files do not always mean better architecture.
- Good architecture is simple but ready to evolve.
- Do not split services only because names are different.
- Split services when business logic becomes different.
- Avoid premature abstraction.
- Follow YAGNI.
- Build architecture according to the real project state.

---

## Phase 5 Progress

Completed:

- Lesson 1: Production Folder Architecture
- Lesson 2: Modular Backend Architecture
- Lesson 3: Enterprise AI Service Refactor
- Lesson 4: Feature-wise Architecture Decision

Next Lesson:

Lesson 5: Build first real feature - Resume Analyzer API

---

# End of Phase 5 - Lesson 4
