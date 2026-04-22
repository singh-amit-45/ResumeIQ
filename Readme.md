# 🧠 ResumeIQ

An AI-powered interview preparation platform that analyzes your resume against a job description and generates a personalized interview report — including technical & behavioral questions, skill gap analysis, a preparation plan, and an AI-optimized resume PDF.

---

## 🚀 Features

- 📄 **Resume Parsing** — Upload your resume as a PDF and extract its content automatically
- 🤖 **AI-Powered Analysis** — Uses Google Gemini AI to match your resume with the job description
- 📊 **Match Score** — Get a percentage score showing how well your profile fits the role
- ❓ **Interview Questions** — Auto-generated technical and behavioral questions with answers and intentions
- 🔍 **Skill Gap Analysis** — Identifies missing skills with severity levels (low / medium / high)
- 📅 **Preparation Plan** — Day-by-day study plan tailored to your skill gaps
- 📥 **Resume PDF Generator** — Download an AI-optimized resume PDF based on the job description
- 🔐 **Authentication** — Secure register/login/logout with JWT and cookie-based sessions
- 📁 **Report History** — View all your previously generated interview reports

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| React 19 | UI framework |
| React Router 7 | Client-side routing |
| Axios | HTTP requests |
| Sass | Styling |
| Vite | Build tool & dev server |

### Backend
| Technology | Purpose |
|---|---|
| Node.js + Express 5 | REST API server |
| MongoDB + Mongoose | Database & ORM |
| Google Gemini AI (`@google/genai`) | AI report & resume generation |
| Multer | PDF file uploads |
| pdf-parse | Resume PDF text extraction |
| Puppeteer | Generate downloadable resume PDFs |
| bcryptjs | Password hashing |
| JSON Web Token (JWT) | Authentication |
| Zod | Schema validation |

---

## 📁 Project Structure

```
ResumeIQ/
├── backend/
│   ├── controllers/
│   │   ├── auth.controller.js
│   │   └── interview.controller.js
│   ├── models/
│   │   ├── user.model.js
│   │   ├── blacklist.model.js
│   │   └── interviewReport.model.js
│   ├── routes/
│   │   ├── auth.routes.js
│   │   └── interview.routes.js
│   ├── services/
│   │   └── ai.service.js
│   ├── app.js
│   ├── server.js
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── pages/
    │   ├── components/
    │   └── main.jsx
    ├── index.html
    └── package.json
```

---

## ⚙️ Getting Started

### Prerequisites

- Node.js v18+
- MongoDB (local or Atlas)
- Google Gemini API key

---

### 🔧 Backend Setup

1. **Clone the repository**
```bash
git clone https://github.com/singh-amit-45/ResumeIQ.git
cd ResumeIQ/backend
```

2. **Install dependencies**
```bash
npm install
```

3. **Create a `.env` file** in the `backend` folder:
```env
PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
GEMINI_API_KEY=your_google_gemini_api_key
```

4. **Start the backend server**
```bash
npm run dev
```

The backend will run at `http://localhost:3000`

---

### 🎨 Frontend Setup

1. **Navigate to the frontend folder**
```bash
cd ../frontend
```

2. **Install dependencies**
```bash
npm install
```

3. **Start the frontend dev server**
```bash
npm run dev
```

The frontend will run at `http://localhost:5173`

---

## 📡 API Endpoints

### Auth Routes — `/api/auth`

| Method | Endpoint | Description | Access |
|---|---|---|---|
| POST | `/register` | Register a new user | Public |
| POST | `/login` | Login a user | Public |
| POST | `/logout` | Logout and invalidate token | Public |
| GET | `/me` | Get current logged-in user | Private |

### Interview Routes — `/api/interview`

| Method | Endpoint | Description | Access |
|---|---|---|---|
| POST | `/generate` | Generate interview report (upload resume PDF) | Private |
| GET | `/all` | Get all reports of logged-in user | Private |
| GET | `/:interviewId` | Get a specific interview report | Private |
| GET | `/resume/:interviewReportId` | Download AI-generated resume PDF | Private |

---

## 🧩 Interview Report Structure

Each generated report includes:

```json
{
  "title": "Software Engineer",
  "matchScore": 85,
  "technicalQuestions": [
    {
      "question": "...",
      "intention": "...",
      "answer": "..."
    }
  ],
  "behavioralQuestions": [...],
  "skillGaps": [
    { "skill": "Docker", "severity": "high" }
  ],
  "preparationPlan": [
    { "day": 1, "focus": "DSA", "tasks": ["..."] }
  ]
}
```

---

## 🔐 Authentication Flow

1. User registers or logs in → JWT token is set in an HTTP cookie
2. Protected routes read the token from the cookie
3. On logout, the token is added to a **blacklist** in MongoDB and the cookie is cleared

---

## 📦 Build for Production

**Frontend:**
```bash
cd frontend
npm run build
```

**Backend:**
```bash
cd backend
node server.js
```

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m "Add your feature"`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the **ISC License**.

---

## 👨‍💻 Author

**Amit Singh**  
GitHub: [@singh-amit-45](https://github.com/singh-amit-45)

---

> ⭐ If you found this project helpful, please give it a star on GitHub!
