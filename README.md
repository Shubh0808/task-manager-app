# ⚡ Task Manager App

A full-stack task management web application with real user authentication,
MongoDB database integration, REST API backend, and live deployment.

---

## 🌐 Live Demo

| Service  | URL |
|----------|-----|
| 🖥️ Frontend | https://task-manager-app-black-three.vercel.app |
| ⚙️ Backend API | https://task-manager-app-72l2.onrender.com |
| 📁 GitHub | https://github.com/Shubh0808/task-manager-app |

---

## 📸 Features

- ✅ User Signup & Login (Real Authentication)
- ✅ JWT Token based session management
- ✅ Password encryption using bcrypt
- ✅ Create, Read, Update, Delete Tasks (CRUD)
- ✅ Task status tracking (Pending → In Progress → Completed)
- ✅ Protected routes (only logged in users see their tasks)
- ✅ Responsive & beautiful UI
- ✅ Fully deployed live on internet

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| HTML5 | Structure & markup |
| CSS3 | Styling & animations |
| JavaScript (Vanilla) | Logic & API calls |
| Vercel | Frontend deployment |

### Backend
| Technology | Purpose |
|-----------|---------|
| Node.js | JavaScript runtime |
| Express.js | Web framework & REST API |
| MongoDB | NoSQL Database |
| Mongoose | MongoDB object modeling |
| bcryptjs | Password hashing |
| JSON Web Token | Authentication tokens |
| dotenv | Environment variables |
| cors | Cross-origin requests |
| nodemon | Development auto-reload |
| Render | Backend deployment |

---

## 📁 Project Structure
task-manager-app/
│
├── backend/
│   ├── config/
│   │   └── db.js              # MongoDB connection
│   ├── middleware/
│   │   └── authMiddleware.js  # JWT auth middleware
│   ├── models/
│   │   ├── User.js            # User schema
│   │   └── Task.js            # Task schema
│   ├── routes/
│   │   ├── authRoutes.js      # Signup and Login routes
│   │   └── taskRoutes.js      # CRUD task routes
│   ├── .env                   # Environment variables (not in git)
│   ├── package.json           # Dependencies
│   └── server.js              # Entry point
│
├── frontend/
│   ├── index.html             # Signup page
│   ├── login.html             # Login page
│   ├── dashboard.html         # Main dashboard
│   ├── style.css              # All styles
│   └── app.js                 # Frontend logic and API calls
│
├── .gitignore                 # Git ignore rules
└── README.md                  # Project documentation

---

## 🔌 API Endpoints

### Auth Routes
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/auth/signup` | Register new user | No |
| POST | `/api/auth/login` | Login user | No |

### Task Routes
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/tasks` | Get all user tasks | Yes |
| POST | `/api/tasks` | Create new task | Yes |
| PUT | `/api/tasks/:id` | Update task status | Yes |
| DELETE | `/api/tasks/:id` | Delete a task | Yes |

---

## 🔐 Authentication Flow

User signs up → password gets hashed by bcrypt
User logs in → bcrypt compares passwords
Server generates JWT token valid for 30 days
Token stored in localStorage on frontend
Every API request sends token in Authorization header
Backend middleware verifies token before allowing access


---

## 🗄️ Database Schema

### User Model
```json
{
  "name": "String (required)",
  "email": "String (required, unique)",
  "password": "String (hashed, required)",
  "createdAt": "Date (auto)",
  "updatedAt": "Date (auto)"
}
```

### Task Model
```json
{
  "user": "ObjectId (ref: User)",
  "title": "String (required)",
  "description": "String (optional)",
  "status": "pending | in-progress | completed",
  "createdAt": "Date (auto)",
  "updatedAt": "Date (auto)"
}
```

---

## 🚀 Run Locally

### Prerequisites
- Node.js v18 or higher
- MongoDB local or Atlas
- Git

### Step 1 — Clone the repository
```bash
git clone https://github.com/Shubh0808/task-manager-app.git
cd task-manager-app
```

### Step 2 — Setup Backend
```bash
cd backend
npm install
```

### Step 3 — Create .env file inside backend folder
MONGO_URI=mongodb://localhost:27017/taskmanager
JWT_SECRET=mysupersecretkey123
PORT=5000

### Step 4 — Start Backend server
```bash
npm run dev
```

### Step 5 — Open Frontend
```bash
cd ../frontend
start index.html
```

### Step 6 — Open in browser
Backend API  → http://localhost:5000
Frontend App → frontend/index.html

---

## ☁️ Deployment Guide

### Backend deployed on Render
1. Go to https://render.com
2. Connect your GitHub repository
3. Set Root Directory to backend
4. Set Build Command to npm install
5. Set Start Command to node server.js
6. Add these environment variables:
   - MONGO_URI = your MongoDB Atlas connection string
   - JWT_SECRET = your secret key
   - PORT = 5000
7. Click Deploy

### Frontend deployed on Vercel
1. Go to https://vercel.com
2. Connect your GitHub repository
3. Set Root Directory to frontend
4. Click Deploy

---

## 🔒 Security Features

- Passwords are never stored as plain text
- bcrypt uses salt rounds for extra security
- JWT tokens expire after 30 days
- Protected API routes verify token on every request
- .env file is gitignored so secrets never go to GitHub
- CORS configured to allow only trusted origins

---

## 🧪 Testing the API

### Test Signup
```powershell
Invoke-WebRequest -Uri "http://localhost:5000/api/auth/signup" -Method POST -Headers @{"Content-Type"="application/json"} -Body '{"name":"Test User","email":"test@test.com","password":"123456"}'
```

### Test Login
```powershell
Invoke-WebRequest -Uri "http://localhost:5000/api/auth/login" -Method POST -Headers @{"Content-Type"="application/json"} -Body '{"email":"test@test.com","password":"123456"}'
```

---

## 👨‍💻 Developer

**Shubh**
- GitHub: [@Shubh0808](https://github.com/Shubh0808)

---

## 📄 License

This project is open source and available under the MIT License.