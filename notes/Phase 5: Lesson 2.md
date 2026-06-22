# Phase 5 - Lesson 2

# AI Full Stack Developer Roadmap

# Topic: Modular Backend Architecture

---

# Objective

Learn how production backend applications separate responsibilities using Routes, Controllers, and Services.

The goal is to convert a beginner backend into an enterprise-level backend architecture.

---

# Why Modular Architecture?

Beginner Backend

server.js

↓

Everything

Problems

* Difficult to maintain
* Difficult to debug
* Difficult to scale
* Difficult for multiple developers to work together

---

Production Backend

Each module has a single responsibility.

Benefits

* Clean Architecture
* Easy Maintenance
* Easy Debugging
* Better Team Collaboration
* High Scalability

---

# Layered Backend Flow

React Frontend

↓

server.js

↓

Routes

↓

Controllers

↓

Services

↓

Prompts

↓

Gemini API

↓

Controller

↓

Frontend

---

# Responsibilities of Each Layer

---

## server.js

Purpose

Application Entry Point

Responsibilities

* Initialize Express
* Configure Middleware
* Register Routes
* Start Server

Should NOT contain

* AI Logic
* Prompt Engineering
* Business Logic

---

## Routes

Purpose

Map HTTP endpoints to controllers.

Example

POST /chat

↓

chatController

GET /history

↓

historyController

DELETE /history

↓

clearHistoryController

Routes never contain business logic.

---

## Controllers

Purpose

Handle Request and Response.

Responsibilities

* Receive Request
* Validate Input
* Call Service
* Return JSON Response

Controllers should never contain AI logic.

---

## Services

Purpose

Business Logic Layer.

Responsibilities

* Prompt Selection
* Gemini API Calls
* Memory Handling
* File Operations
* Data Processing
* AI Orchestration

Services are considered the brain of the backend.

---

## Prompts

Purpose

Store all system prompts separately.

Examples

mentorPrompt

resumePrompt

careerPrompt

interviewPrompt

Benefits

* Easy Maintenance
* Cleaner Code
* Reusable Prompts

---

# Request Flow

User

↓

Frontend

↓

POST /chat

↓

Route

↓

Controller

↓

AI Service

↓

Prompt Manager

↓

Gemini API

↓

Controller

↓

Frontend

---

# Why Use Services?

Instead of

Controller

↓

Gemini

Use

Controller

↓

Service

↓

Gemini

Benefits

* Reusable
* Cleaner
* Easier Testing
* Better Maintainability

---

# Loose Coupling

Meaning

Each module depends as little as possible on other modules.

Example

Today

Gemini

Tomorrow

OpenAI

Only aiService.js changes.

Routes

Controllers

Frontend

Remain unchanged.

---

# Separation of Concerns

Every file should perform only one responsibility.

Examples

Routes

↓

Routing

Controllers

↓

Request Handling

Services

↓

Business Logic

Prompts

↓

System Prompts

---

# Open-Closed Principle

A software module should be

Open for Extension

Closed for Modification

Example

Adding

Resume Analyzer

Interview Simulator

Code Reviewer

Should only require

New Controller

*

New Service

*

New Prompt

Existing code should remain unchanged.

---

# Enterprise Folder Structure

server/

│

├── routes/

│      aiRoutes.js

│

├── controllers/

│      aiController.js

│

├── services/

│      aiService.js

│

├── prompts/

│      prompts.js

│

├── data/

│      chats.json

│

└── server.js

---

# AI Service Flow

AI Service

↓

Load Prompt

↓

Prepare Conversation

↓

Call Gemini

↓

Receive Response

↓

Store History

↓

Return Result

AI Service acts as the orchestrator of the entire AI pipeline.

---

# Future Enterprise Flow

Frontend

↓

Routes

↓

Controllers

↓

AI Service

↓

Memory Manager

↓

Retriever

↓

Prompt Manager

↓

Vector Database

↓

Gemini

↓

Output Parser

↓

Controller

↓

Frontend

---

# Placement Interview Questions

---

Q1. Why do we use Routes?

Answer

Routes map incoming HTTP requests to controllers. They should not contain business logic.

---

Q2. Why do we use Controllers?

Answer

Controllers manage the request-response lifecycle. They validate input, call services, and return responses.

---

Q3. Why do we use Services?

Answer

Services contain business logic, AI orchestration, database interaction, memory handling, and API integrations.

---

Q4. What is Loose Coupling?

Answer

Loose coupling means modules are minimally dependent on each other. This makes applications easier to maintain and extend.

---

Q5. What is Layered Architecture?

Answer

Layered architecture separates an application into independent layers, each with a specific responsibility, improving maintainability and scalability.

---

Q6. What is the Open-Closed Principle?

Answer

Software should be open for extension but closed for modification. New features should be added with new modules instead of changing existing code.

---

# Mentor Takeaways

✔ server.js should remain minimal.

✔ Routes only map endpoints.

✔ Controllers handle requests and responses.

✔ Services contain business logic.

✔ Prompts remain modular.

✔ AI Service orchestrates the AI workflow.

✔ Loose coupling improves maintainability.

✔ Layered architecture is the industry standard.

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

Next Lesson

➡ AI Service Layer & Dependency Injection

Topics

* Service Reusability
* Dependency Injection
* Shared AI Services
* Enterprise AI Design

---

# End of Phase 5 - Lesson 2
