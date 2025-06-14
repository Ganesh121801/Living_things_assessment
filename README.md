# Task Management App

A comprehensive full-stack application designed for efficient task tracking, featuring secure authentication, complete task CRUD functionality, and seamless Excel export. The frontend is built using React.js with Tailwind CSS, while user authentication is handled through a Node.js backend. Task management is powered by Django REST Framework and SQLite.

---

## Key Features

* **Secure Authentication**: User registration and login via Node.js, integrated with Django backend.
* **Task Operations**:

  * Add, edit, and delete tasks with fields like title, description, estimated effort (in days), and due date.
  * Each user accesses only their personal tasks.
  * Form-level validations for empty fields and valid dates.
* **Excel Export**: Download task data as an Excel file through Django.
---

## Folder Structure

```
task-management-app/
├── frontend/               # React frontend
│   ├── src/
│   │   ├── components/
│   │   │   ├── Login.jsx
│   │   │   ├── Register.jsx
│   │   │   └── Tasks.jsx
│   │   ├── App.jsx
│   │   └── index.css
├── backend1/               # Node.js backend for authentication
│   ├── index.js
│   ├── users.db
│   └── package.json
├── backend2/               # Django backend for task APIs
│   ├── manage.py
│   ├── tasks/
│   │   ├── models.py
│   │   ├── serializers.py
│   │   ├── urls.py
│   │   └── views.py
│   └── task_manager/
│       ├── settings.py
│       └── urls.py
└── README.md
```

---

# Requirements

* Node.js (v18 or newer)
* Python (v3.8+)
* SQLite (pre-installed with Python)
* npm (included with Node.js)
* pip (Python package installer)
* Git (for cloning the repository)

---

## Setup Guide

### Clone the Repository

```bash
git clone <repository-url>
cd task-management-app
```

### Set Up Node.js Authentication Server

```bash
cd backend1
npm install
```

Create a `.env` file inside the `backend1` directory and add:

```
JWT_SECRET=your-secret-key
```

Replace `your-secret-key` with a secure value of your choice.

Start the server:

```bash
npm start
```

Runs at: `http://localhost:3000`

---

### Set Up Django Task Management API

```bash
cd ../backend2
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
```

Install dependencies:

```bash
pip install django djangorestframework django-cors-headers openpyxl python-decouple
```

Run migrations:

```bash
python manage.py migrate
```

(Optional) Create admin account:

```bash
python manage.py createsuperuser
```

Start Django server:

```bash
python manage.py runserver
```

Runs at: `http://localhost:8000`

---

# Start the React Frontend

```bash
cd ../frontend
npm install
npm start
```

Runs at: `http://localhost:3001`

---

## 🧑‍💻 How to Use

1. Ensure all three servers (React, Node.js, Django) are up and running.
2. Visit `http://localhost:3001` to access the frontend.
3. Go to `/register` to create a new account.
4. Login through `/login` using your credentials.
5. Navigate to `/tasks` to:

   * Add new tasks
   * Edit or delete existing tasks
   * Export your task list as an Excel file
6. Use the **Logout** button to end the session.

---

##  API Overview

### Node.js Auth Server (Port 3000)

* `POST /api/register` – Register new users
* `POST /api/login` – Authenticate and receive a token

### Django Task API Server (Port 8000)

* `POST /api/register/` – Sync registration
* `POST /api/login/` – Login and receive token
* `GET /api/tasks/` – Fetch user's task list
* `POST /api/tasks/` – Add a new task
* `PUT /api/tasks/:id/` – Update an existing task
* `DELETE /api/tasks/:id/` – Remove a task
* `GET /api/tasks/export/` – Download tasks in Excel format

