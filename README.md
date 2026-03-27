### Notes API with Authentication

A secure RESTful Notes API built with Node.js, Express, MongoDB, and JWT authentication.
This application allows users to register, log in, and manage their personal notes with full ownership-based authorization.

# Tech Stack

- Node.js
- Express.js
- MongoDB + Mongoose
- JWT (jsonwebtoken)
- bcrypt (password hashing)
- Passport.js (GitHub OAuth)

# Project Structure

project-root/
│
├── config/
│   └── connection.js
│   └── passport.js
│
├── models/
│   ├── User.js
│   └── Note.js
│
├── routes/
│   ├── userRoutes.js
│   └── noteRoutes.js
│
├── utils/
│   └── auth.js
│
├── .env
├── .gitignore
├── server.js
└── README.md

## Installation & Setup

# Install dependencies
npm install

# Run server
node server.js

Server runs on:

http://localhost:3001

# Authentication

All note routes require a JWT token.

Header format:

Authorization: Bearer YOUR_TOKEN

 API Endpoints

 User Routes

Register User

POST /api/users/register

Body:

{
  "username": "",
  "email": "",
  "password": ""
}
* Login User

POST /api/users/login

# Notes Routes (Protected)
Create Note

POST /api/notes

Get All Notes (User Only)

GET /api/notes

Update Note (Owner Only)

PUT /api/notes/:id

Delete Note (Owner Only)

DELETE /api/notes/:id

# Authorization Logic

Each note is linked to a user via:

user: {
  type: Schema.Types.ObjectId,
  ref: 'User',
  required: true
}
Rules:

Users can only see their own notes

Users cannot update/delete others' notes

Unauthorized access returns:

403 Forbidden

## Testing (Postman)

Register/Login user → get token

Add token to headers

Test all CRUD operations

Verify authorization with multiple users