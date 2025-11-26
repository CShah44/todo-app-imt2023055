# 📝 To-Do List CLI Application

A simple command-line interface application for managing your to-do tasks, built with Python and containerized with Docker.

[![Python](https://img.shields.io/badge/Python-3.9-blue.svg)](https://www.python.org/)
[![Docker](https://img.shields.io/badge/Docker-Enabled-2496ED.svg)](https://www.docker.com/)
[![Jenkins](https://img.shields.io/badge/Jenkins-CI%2FCD-D24939.svg)](https://www.jenkins.io/)

---

## ✨ Features

- ➕ **Add new tasks** - Create tasks with descriptions and timestamps
- 👁️ **View all tasks** - Display all tasks with completion status
- ✅ **Mark tasks as completed** - Track your progress
- 🗑️ **Delete individual tasks** - Remove specific tasks by ID
- 🧹 **Clear all tasks** - Start fresh with one command
- 💾 **Persistent storage** - Tasks saved in JSON format

---

## 📁 Project Structure

```
todo-app/
├── todo.py              # Main application file
├── tests/
│   └── test_todo.py     # Unit tests (15 test cases)
├── Dockerfile           # Docker configuration
├── Jenkinsfile          # Jenkins pipeline configuration
├── requirements.txt     # Python dependencies
├── README.md            # This file
└── .gitignore          # Git ignore file
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9 or higher
- Docker Desktop (for containerization)
- Jenkins (for CI/CD pipeline)

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/CShah44/todo-app-imt2023055.git
   cd ToDo-List-CLI-App
   ```

2. **Install dependencies (if any):**
   ```bash
   pip install -r requirements.txt
   ```

---

## 💻 Running Locally

### Run the application:

```bash
python todo.py
```

### Application Menu:

```
===========================================================
TO-DO LIST CLI APPLICATION
===========================================================
1. Add Task
2. View All Tasks
3. Complete Task
4. Delete Task
5. Clear All Tasks
6. Exit
===========================================================
```

---

## 🧪 Running Tests

Run all unit tests with verbose output:

```bash
python -m unittest discover -s tests -p "test_*.py" -v
```

### Test Coverage:

- ✅ Add task functionality
- ✅ Empty task validation
- ✅ Multiple task handling
- ✅ Task completion
- ✅ Task deletion with reindexing
- ✅ Clear all tasks
- ✅ Data persistence
- ✅ Task properties validation

---

## 🐳 Docker

### Build the Docker image:

```bash
docker build -t todo-app .
```

### Run the container:

```bash
docker run -it todo-app
```

### Run with Docker Hub image:

```bash
docker run -it greatwarrior44/imt2023055-todo-app:latest
```

---

## 🔄 CI/CD Pipeline

This project uses **Jenkins** for continuous integration and deployment automation.

### Pipeline Stages:

1. **📥 Checkout** - Pulls code from GitHub
2. **🔨 Build** - Verifies Python environment and application structure
3. **🧪 Test** - Runs unit tests to ensure code quality
4. **🐳 Build Docker Image** - Creates containerized application
5. **📤 Push to Docker Hub** - Uploads image to Docker repository
6. **✅ Verify** - Confirms successful image creation

### Pipeline Configuration:

The `Jenkinsfile` is configured to:

- Automatically trigger on code commits
- Run on both Windows and Unix environments
- Use Docker Hub credentials securely
- Tag images with build numbers and 'latest'

---

## 🛠️ Technologies Used

- **Language:** Python 3.9
- **Testing:** Python unittest
- **Containerization:** Docker
- **CI/CD:** Jenkins
- **Version Control:** Git & GitHub
- **Container Registry:** Docker Hub

---

## 📊 Project Workflow

```
GitHub → Jenkins → Build → Test → Docker Image → Docker Hub
   ↓         ↓        ↓       ↓          ↓            ↓
  Code    Pipeline  Verify  Pass    Containerize   Deploy
```

---

## 📦 Docker Hub

Docker images are available at: [<username>/todo-app](https://hub.docker.com/repository/docker/greatwarrior44/imt2023055-todo-app/)

Pull the latest image:

```bash
docker pull greatwarrior44/imt2023055-todo-app:latest
```

---

## 👨‍💻 Author

**Chaitya Shah**  
Created for SE Lab Assignment  
GitHub: [@CShah44](https://github.com/CShah44)

---
