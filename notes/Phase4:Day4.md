# Node.js Day 3 + Day 4

## Topics Covered

* JWT Authentication
* bcrypt Password Hashing
* Auth Middleware
* MVC Folder Structure
* Environment Variables (.env)
* Error Handling
* Interview Questions

---

## JWT Authentication

### Install Packages

```bash
npm install bcryptjs jsonwebtoken
```

### Hash Password

```js
const hashedPassword = await bcrypt.hash(password, 10);
```

### Compare Password

```js
const isMatch = await bcrypt.compare(password, user.password);
```

### Generate JWT

```js
const token = jwt.sign(
  { userId: user.id, email: user.email },
  process.env.JWT_SECRET,
  { expiresIn: "24h" }
);
```

### Verify JWT

```js
const decoded = jwt.verify(
  token,
  process.env.JWT_SECRET
);
```

---

## Auth Middleware

```js
const jwt = require("jsonwebtoken");

function authMiddleware(req, res, next) {
  const token = req.headers.authorization;

  if (!token) {
    return res.status(401).json({
      error: "No token provided"
    });
  }

  try {
    const decoded = jwt.verify(
      token,
      process.env.JWT_SECRET
    );

    req.user = decoded;
    next();
  } catch (error) {
    return res.status(401).json({
      error: "Invalid token"
    });
  }
}

module.exports = authMiddleware;
```

---

## MVC Folder Structure

```txt
project/
│
├── controllers/
│   └── authController.js
│
├── middleware/
│   └── auth.js
│
├── routes/
│   └── authRoutes.js
│
├── models/
│
├── .env
├── .gitignore
├── package.json
└── server.js
```

---

## Route Flow

```txt
Request
   ↓
Route
   ↓
Middleware
   ↓
Controller
   ↓
Response
```

---

## Environment Variables

### .env

```env
PORT=8000
JWT_SECRET=mySuperSecretKey
```

### Load Variables

```js
require("dotenv").config();
```

### Use Variables

```js
const PORT = process.env.PORT;
const JWT_SECRET = process.env.JWT_SECRET;
```

---

## Error Handling

### 404 Handler

```js
app.use((req, res) => {
  res.status(404).json({
    error: "Route not found"
  });
});
```

### Global Error Handler

```js
app.use((err, req, res, next) => {
  console.error(err.stack);

  res.status(500).json({
    error: "Something went wrong"
  });
});
```

---

## Common Mistakes

### Wrong Export

```js
module.exports = { authMiddleware };
```

### Correct Export

```js
module.exports = authMiddleware;
```

### Wrong Import

```js
const authMiddleware =
require("../middleware/auth");
```

### Correct Import For Named Export

```js
const { authMiddleware } =
require("../middleware/auth");
```

---

## Status Codes

| Code | Meaning      |
| ---- | ------------ |
| 200  | Success      |
| 201  | Created      |
| 400  | Bad Request  |
| 401  | Unauthorized |
| 403  | Forbidden    |
| 404  | Not Found    |
| 500  | Server Error |

---

## Interview Questions

### Why JWT instead of Sessions?

* Stateless
* Faster
* Scalable
* No database lookup per request

### Why bcrypt?

* Passwords are never stored in plain text
* One-way hashing
* Secure against database leaks

### What should never be stored in JWT?

* Passwords
* Credit card details
* Sensitive personal information

Only store:

```js
{
  userId,
  email
}
```

---

## Assignment

### Build Complete Authentication System

Routes:

```txt
POST /auth/register
POST /auth/login
GET  /auth/profile
```

Features:

* JWT Authentication
* Password Hashing
* Protected Routes
* MVC Structure
* .env Configuration
* Error Handling

```
```
