<p align="center"> 
    <img src="https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi" alt="FastAPI"/>
    <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React"/>
    <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite"/> 
    <img src="https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase"/> 
    <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL"/> 
</p>
    <h1 align="center"> ToDo List App</h1>
    <p align="center"><strong>Full Stack CRUD Application</strong></p> 
    <p align="center"> 
    <a href="#why-this-stack">Tech Stack</a> |
    <a href="#quick-start">Quick Start</a> |
    <a href="#api-endpoints">API Endpoints</a> |
    <a href="#screenshots">Screenshots</a>
</p>

### Why This Stack?

| Technology | Purpose | Benefits |
|------------|---------|----------|
| **FastAPI** | Backend Framework | Fast performance<br> Auto-generated OpenAPI docs<br> Async support |
| **Supabase** | Database & Auth | Managed PostgreSQL<br> Built-in RLS<br> Email/password auth |
| **React** | Frontend UI | Component reusability<br> Virtual DOM<br> Rich ecosystem |
| **React Router** | Client Routing | Protected routes<br> Nested layouts<br> SPA navigation |

---

##  Quick Start

### Prerequisites

Before you begin, ensure you have installed:

- [Python 3.8+](https://www.python.org/downloads/) - For running FastAPI backend
- [Node.js 16+](https://nodejs.org/) - For running React frontend
- [npm](https://www.npmjs.com/) - Package managers
- [Git](https://git-scm.com/downloads) - For cloning the repository

---
### Configuration & Setup

### Step 1: Clone the Repository


`git clone https://github.com/TUP-e/cmsc128-Lab1_CRUD_Nice` </br>
`cd cmsc128-Lab1_CRUD_Nice`


### Step 2: Backend Setup (FastAPI)
at the repo root execute 
`cd backend`

|OS|Command|
|-----|-----|
| Windows | `python -m venv venv` </br> `venv\Scripts\activate`|
| Mac/Linux | `python3 -m venv venv` </br> `source venv/bin/activate`|

Also install the python dependencies with `pip install -r requirements.txt`


Create a .env file in the backend/ folder: </br>
`SUPABASE_URL=https://your-project-id.supabase.co` </br>
`SUPABASE_KEY=your-public-anon-key` </br>
`JWT_SECRET=your-jwt-secret`

Optional: </br>
`FRONTEND_URL=http://localhost:5173` </br>
`DEMO_MODE=true`


### Step 3: Frontend Setup (React + Vite)
at the repo root execute </br>
`cd frontend` or `cd ../frontend` from the previous step


Create a .env file in the frontend/ folder: </br>
`VITE_API_URL=http://localhost:8000`

then install node dependencies `npm install`

### Local Ports
`http://localhost:8000` - FastAPI server </br>
`http://localhost:8000/docs` - Swagger UI Documentation and Testing </br>
`http://localhost:8000/tasks` - Task list for the authenticated user (JSON) </br>
`http://localhost:5173` - Frontend UI renders React App

Note: Your frontend port may vary (5173, 5174, etc.). Check the terminal output after running npm run dev.

## Startup Commands
for running backend server : </br>
(run inside backend\ directory)
`source venv/Scripts/activate`
`uvicorn app.main:app --reload --port 8000` </br>
for running the frontend UI : </br>
(run inside frontend\ directory)
`npm run dev` requires a running backend


## Features

### Authentication
- Register with email and password
- Login with email and password
- Forgot password / reset password flow via email
- Protected routes redirect unauthenticated users to `/login`
- Session persisted with a JWT stored client-side

> Note: With `DEMO_MODE=true`, the password reset link is returned in the API response for easy testing.

### Task Management
- Create tasks with title, due date, priority, and tag
- Edit existing tasks inline
- Mark tasks as done / undone
- Soft delete tasks with a 5-second undo toast
- Sort by created date, due date, priority, or tag
- Filter by priority, tag, and completion status

### Profile
- Update display name and email
- Change password (requires current password)
- View current account info in a dedicated `/profile` page

### Home Layout
- Two-column layout: task list on the left, user sidebar on the right
- Sidebar shows display name, email, and quick links to Profile / Log Out
- Responsive: stacks into a single column on narrow screens


## API Endpoints
### REST API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/auth/register` | Register a new user |
| `POST` | `/auth/login` | Log in and receive a JWT |
| `POST` | `/auth/forgot-password` | Send a password reset email |
| `POST` | `/auth/reset-password` | Reset password with token |
| `GET` | `/tasks` | Get all tasks for the authenticated user |
| `GET` | `/tasks/{id}` | Get single task by ID |
| `POST` | `/tasks` | Create a new task |
| `DELETE` | `/tasks/{id}` | Soft delete a task |
| `POST` | `/tasks/{id}/restore` | Restore a deleted task |


### Example API Calls
#### Create a Task 

```
Request:
POST /tasks
Authorization: Bearer <jwt>
Content-Type: application/json

{
  "title": "Study CMSC 128",
  "due_date": "2026-09-07T20:00:00",
  "priority": "High",
  "tag": "School"
}

Response:
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Study CMSC 128",
  "due_date": "2026-09-07T20:00:00",
  "priority": "High",
  "tag": "School",
  "is_done": false,
  "created_at": "2026-09-07T12:00:00",
  "deleted_at": null
}
```
### Screenshots
| App Overview |
|--------------|
|![Alt Text](./screenshots/P1.png)|
|![Alt Text](./screenshots/P2.png)|
|![Alt Text](./screenshots/P3.png)|
|![Alt Text](./screenshots/P4.png)|
|![Alt Text](./screenshots/P5.png)|
|![Login page](./screenshots/LoginPage.png)|
|![Home page](./screenshots/HomePage.png)|
|![Duplicate registration error](./screenshots/Duplicate%20Registration.png)|
|![Password changing](./screenshots/Password%20Changing.png)|