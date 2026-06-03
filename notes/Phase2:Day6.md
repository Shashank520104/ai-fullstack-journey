# 🚀 Phase 2 - Lesson 6

# Token Limits, Context Windows & Production Conversation Management

## 📌 Objective

Learn how real AI applications manage long conversations without sending unlimited chat history to the LLM.

By the end of this lesson, you will understand:

* What Tokens are
* What Context Window means
* Why AI forgets conversations
* Why sending full chat history is bad
* How production AI applications solve this problem
* How to implement conversation management in React + Express + Gemini

---

# 1. What is a Token?

A token is the smallest unit that an LLM processes.

Example:

Sentence:

Hello my name is Shashank

May become:

```
Hello
my
name
is
Shashank
```

5 Tokens

Another example:

```
I love AI
```

May become:

```
I
love
AI
```

3 Tokens

---

## Important

LLMs do NOT count words.

They count tokens.

A token can be:

* Word
* Part of a word
* Symbol
* Number
* Punctuation

---

# 2. Why Tokens Matter

Every model has a limit.

Example:

```
Gemini
GPT
Claude
Llama
```

can only read a certain number of tokens at once.

This limit is called:

## Context Window

---

# 3. What is Context Window?

Context Window = Maximum amount of information the model can remember in one request.

Example:

User:

```
Hi
```

AI:

```
Hello
```

User:

```
My name is Shashank
```

AI:

```
Nice to meet you Shashank
```

User:

```
What is my name?
```

AI:

```
Shashank
```

Why?

Because previous messages were sent again.

---

# 4. How ChatGPT Remembers

Wrong assumption:

```
User Message
→ AI
→ Memory Stored Forever
```

Reality:

Every request contains:

```
Message 1
Message 2
Message 3
Message 4
...
Latest Message
```

The entire conversation is sent again.

---

# 5. Problem in Real Applications

Imagine:

100 messages

Each message:

100 tokens

Total:

```
100 × 100
=
10,000 tokens
```

Every new request sends:

```
10,000 tokens
```

Again and Again

Problems:

* Slow response
* Expensive API calls
* Token limit exceeded

---

# 6. Production Solution

Never send complete conversation.

Send only recent conversation.

Example:

Keep only:

```
Last 10 Messages
```

Instead of:

```
Last 100 Messages
```

---

# 7. React Implementation

## Step 1

Create updated conversation

```js
const updatedConversation = [
  ...conversation,
  userMessage
];
```

---

## Step 2

Keep only recent messages

```js
const recentConversation =
updatedConversation.slice(-10);
```

Explanation:

```js
slice(-10)
```

returns only last 10 messages.

---

## Step 3

Send recent conversation

```js
body: JSON.stringify({
  conversation: recentConversation,
  mode: mode
})
```

---

# 8. Backend Conversation Handling

Receive conversation:

```js
const { conversation, mode } = req.body;
```

---

Validate:

```js
if (!conversation || conversation.length === 0)
{
    return res.status(400).json({
        error: "Conversation is required"
    });
}
```

---

Convert conversation to text

```js
const chatHistory =
conversation
.map((msg) =>
`${msg.role}:${msg.text}`)
.join("\n");
```

Example Output:

```
user: Hi

ai: Hello

user: My name is Shashank

ai: Nice to meet you
```

---

# 9. Send Context To Gemini

```js
const response =
await ai.models.generateContent({
    model: "gemini-2.5-flash",
    contents: `
    ${systemPrompt}

    Conversation History:

    ${chatHistory}
    `
});
```

Now Gemini receives:

* System Prompt
* Previous Messages
* Current User Context

This creates memory-like behavior.

---

# 10. Why Your AI Remembered Name

Conversation:

```
User:
My name is Shashank

AI:
Nice to meet you

User:
What is my name?
```

Because:

```js
recentConversation
```

contained both messages.

Gemini could see them.

Therefore:

```
Answer = Shashank
```

---

# 11. Industry Architecture

Real AI Systems:

```
Frontend
↓
Backend
↓
Conversation Manager
↓
Vector Database
↓
LLM
```

Examples:

* ChatGPT
* Claude
* Perplexity
* Cursor
* Windsurf
* Copilot

All use conversation management.

---

# 12. Current Limitation

Your AI currently remembers:

```
Last 10 Messages
```

Only.

After message 11:

Old messages disappear.

---

Example

Message 1:

```
My name is Shashank
```

Message 20:

```
What is my name?
```

AI may forget.

Because:

Message 1 was removed.

---

# 13. Production Level Solution

Instead of:

```js
slice(-10)
```

Companies use:

### Memory Summarization

Convert old chats into summary.

Example:

```
User Name: Shashank

Goal:
AI Full Stack Developer

Skills:
React
Node
Express
Gemini
```

Store summary.

Send summary with every request.

---

# 14. Advanced Solution

Use:

* Pinecone
* ChromaDB
* FAISS

Store embeddings.

Retrieve relevant memories.

This is called:

## RAG

(Retrieval Augmented Generation)

We will learn this in later phases.

---

# 15. Lesson 6 Final Architecture

```text
User Message
      ↓
React State
      ↓
Recent Conversation
      ↓
Fetch Request
      ↓
Express Backend
      ↓
System Prompt
      ↓
Chat History
      ↓
Gemini API
      ↓
AI Response
      ↓
React UI Update
```

---

# Interview Questions & Answers

## Q1. What is a Token?

Answer:

A token is the smallest unit processed by an LLM. Models calculate limits and costs using tokens instead of words.

---

## Q2. What is a Context Window?

Answer:

Context Window is the maximum amount of information an LLM can process in a single request.

---

## Q3. Why does ChatGPT remember previous messages?

Answer:

Because previous messages are sent again in every API request as conversation context.

---

## Q4. Why should we not send complete chat history?

Answer:

It increases token usage, API cost, response time, and can exceed model limits.

---

## Q5. How do production AI systems manage long conversations?

Answer:

They send only recent messages, summarize older messages, and use vector databases for memory retrieval.

---

## Q6. What does slice(-10) do?

Answer:

It returns the last 10 elements from an array.

Example:

```js
arr.slice(-10)
```

---

## Q7. What is RAG?

Answer:

Retrieval Augmented Generation is a technique where relevant information is retrieved from external storage and provided to the LLM before generating a response.

---

## Q8. Why are Vector Databases used in AI applications?

Answer:

They store embeddings and help retrieve relevant information efficiently for long-term memory systems.

---

# Lesson 6 Completion Checklist

* [x] Understood Tokens
* [x] Understood Context Window
* [x] Understood Conversation History
* [x] Implemented Recent Conversation Logic
* [x] Implemented Backend Context Handling
* [x] Learned Production Memory Concepts
* [x] Learned RAG Basics
* [x] Practiced Interview Questions

---

# Next Lesson

## Lesson 7 — Prompt Engineering Fundamentals

Topics:

* System Prompts
* User Prompts
* Role Prompting
* Few Shot Prompting
* Chain Of Thought
* Prompt Templates
* AI Assistant Personalities
* Production Prompt Design

Project Upgrade:

Create a professional multi-role AI assistant with optimized prompting.
