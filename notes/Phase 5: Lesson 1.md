# Phase 5 - Lesson 1

# AI Full Stack Developer Roadmap

# Topic: Production Folder Architecture

---

# Objective

Learn how to transform a beginner AI application into a production-ready application using proper software architecture and folder structure.

---

# Why Folder Architecture Matters

Beginner Project

server.js

↓

Everything

Problems

* Difficult to read
* Difficult to debug
* Difficult to scale
* Difficult for teams to work together

---

Production Project

Each component has its own responsibility.

Advantages

* Clean code
* Easy debugging
* Easy maintenance
* Easy scalability
* Better teamwork

---

# Software Engineering Principle

One File

=

One Responsibility

Never put all application logic inside one file.

---

# Beginner Architecture

server.js

↓

Routes

↓

Gemini Logic

↓

Memory

↓

Prompt

↓

Everything

Not scalable.

---

# Production Architecture

server/

│

├── config/

├── controllers/

├── routes/

├── services/

├── prompts/

├── memory/

├── middleware/

├── utils/

├── data/

└── server.js

Every folder has a single responsibility.

---

# Folder Responsibilities

---

## config/

Purpose

Stores application configuration.

Examples

* Gemini Configuration
* Database Connection
* Environment Variables
* Constants

Example Files

config/

gemini.js

db.js

constants.js

---

## routes/

Purpose

Defines API endpoints.

Contains

* GET
* POST
* PUT
* DELETE

Routes never contain business logic.

Example

POST /chat

GET /history

DELETE /history

---

## controllers/

Purpose

Receives request.

Calls service.

Returns response.

Responsibilities

* Read Request
* Validate Input
* Call Service
* Return JSON

Controller should not contain AI logic.

---

## services/

Purpose

Contains business logic.

Examples

* Gemini API Calls
* Resume Analysis
* ATS Logic
* Interview Logic

Service is the brain of the application.

---

## prompts/

Purpose

Store all system prompts separately.

Example

mentorPrompt.js

resumePrompt.js

careerPrompt.js

interviewPrompt.js

Benefits

* Easy maintenance
* Cleaner code
* Reusable prompts

---

## memory/

Purpose

Manage conversation memory.

Examples

* Long-Term Memory
* Short-Term Memory
* Session Memory
* Summary Memory

---

## middleware/

Purpose

Runs before controller.

Examples

* Authentication
* Authorization
* Logging
* Error Handling
* Rate Limiting

---

## utils/

Purpose

Common helper functions.

Examples

* Logger
* Formatter
* Validators
* Helper Functions

Reusable across entire project.

---

## data/

Purpose

Temporary storage.

Examples

* chats.json
* Local development files

Later replaced by database.

---

# server.js Responsibility

server.js should only:

* Initialize Express
* Configure Middleware
* Load Routes
* Start Server

It should NOT contain business logic.

---

# Request Flow

React

↓

Routes

↓

Controller

↓

Service

↓

Gemini

↓

Controller

↓

Frontend

Notice

Controller communicates with Service.

Service communicates with Gemini.

---

# Why Services?

Instead of

server.js

↓

Gemini API

Use

Controller

↓

Service

↓

Gemini

Benefits

* Reusable
* Testable
* Cleaner
* Easier Debugging

---

# Why Controllers?

Controller only manages request-response cycle.

It should not process AI logic.

---

# Why Routes?

Routes only define API endpoints.

No processing should happen here.

---

# Why Middleware?

Middleware handles common operations before requests reach controllers.

Examples

* Authentication
* Logging
* Error Handling

---

# Enterprise Principle

Separate Concerns.

Each module should perform one task only.

This improves

* Maintainability
* Scalability
* Readability
* Team Collaboration

---

# Current Shaurya AI

React

↓

server.js

↓

Gemini

Good for learning.

---

# Future Shaurya AI

React

↓

Routes

↓

Controller

↓

Service

↓

Memory

↓

Retriever

↓

Prompt

↓

Gemini

↓

Output Parser

↓

Frontend

Enterprise Architecture.

---

# Placement Interview Questions

---

Q1. Why should business logic not be written inside server.js?

Answer

server.js should only initialize the application. Business logic belongs in services and controllers to improve scalability, maintainability, and readability.

---

Q2. Difference between Controller and Service?

Controller

* Receives Request
* Validates Input
* Calls Service
* Returns Response

Service

* Contains Business Logic
* Calls External APIs
* Processes Data
* Returns Results

---

Q3. Why separate prompts into a prompts folder?

Answer

To improve maintainability, reusability, readability, and make prompt updates easier without modifying backend logic.

---

Q4. What belongs inside config folder?

Answer

Application configuration such as API keys, database connections, constants, and environment variables.

---

Q5. What is Separation of Concerns?

Answer

It is a software engineering principle where each module performs a single responsibility, making applications easier to maintain and scale.

---

# Mentor Takeaways

✔ One File = One Responsibility

✔ server.js should remain minimal.

✔ Controllers manage requests.

✔ Services contain business logic.

✔ Routes define endpoints.

✔ Prompts should be modular.

✔ Middleware handles cross-cutting concerns.

✔ Clean architecture improves scalability.

✔ Production applications are modular, not monolithic.

---

# Current Roadmap Progress

Completed

✅ Phase 1 – MERN Fundamentals

✅ Phase 2 – AI Integration

✅ Phase 3 – Advanced AI Features

✅ Phase 4 – AI Engineering Fundamentals

Started

🚀 Phase 5 – Production AI Development

Completed

✅ Lesson 1 – Production Folder Architecture

Next Lesson

➡ Modular Backend Architecture

* Controllers
* Routes
* Services
* Utilities
* Project Refactoring

---

# End of Phase 5 - Lesson 1
