# Phase 2 - Lesson 4

# AI Application Architecture & Request Flow

## Objective

Understand how a real-world AI application works from frontend to backend and back to frontend.

---

## Architecture

Frontend (React)
↓
HTTP Request
↓
Backend (Node.js + Express)
↓
Gemini API
↓
AI Response
↓
Backend
↓
Frontend
↓
UI Update

---

## Complete Flow

### Step 1: User enters prompt

Example:

What is AI Full Stack Development?

---

### Step 2: React captures input

```javascript
const [message, setMessage] = useState("");
```

---

### Step 3: User clicks Send

```javascript
<button onClick={sendMessage}>
  Send
</button>
```

---

### Step 4: HTTP Request sent

```javascript
fetch("http://localhost:8000/chat")
```

Request Body:

```json
{
  "prompt":"What is AI Full Stack Development?"
}
```

---

### Step 5: Express receives request

```javascript
app.post("/chat",(req,res)=>{
});
```

---

### Step 6: Backend extracts prompt

```javascript
const { prompt } = req.body;
```

---

### Step 7: Backend calls Gemini

```javascript
const response =
await ai.models.generateContent({
    model:"gemini-2.5-flash",
    contents:prompt
});
```

---

### Step 8: Gemini generates answer

Example:

AI Full Stack Development combines
frontend, backend and AI systems.

---

### Step 9: Backend returns response

```javascript
res.json({
    reply: response.text
});
```

---

### Step 10: React receives response

```javascript
const data = await response.json();
```

---

### Step 11: React updates state

```javascript
setReply(data.reply);
```

---

### Step 12: UI rerenders

```javascript
<p>{reply}</p>
```

---

## Important Concepts Learned

### Frontend

* React
* State Management
* Fetch API
* Event Handling

### Backend

* Express
* API Routes
* Request Handling
* Response Handling

### AI Layer

* Gemini API
* Prompt Processing
* Response Generation

---

## Interview Questions

### Q1

How does React communicate with Node.js backend?

Answer:
Using HTTP requests through Fetch API or Axios.

---

### Q2

What is the role of Express in an AI application?

Answer:
Express receives requests from frontend, communicates with AI APIs and sends responses back.

---

### Q3

Explain complete AI request flow.

Answer:
Frontend → Backend → AI Model → Backend → Frontend.

---

## Outcome

Built and understood complete AI request-response architecture used in production AI applications.
