# Task Management System

**A Django-based task management web application with user authentication, personal task tracking, search, filtering, and automated tests.**

[![Django](https://img.shields.io/badge/Django-6.0.2-092E20?logo=django&logoColor=white)](https://www.djangoproject.com/)
![Python](https://img.shields.io/badge/Python-3.12%2B-3776AB?logo=python&logoColor=white)
![Database](https://img.shields.io/badge/Database-SQLite-003B57?logo=sqlite&logoColor=white)
![Tests](https://img.shields.io/badge/Tests-Django%20TestCase-0A9EDC)

## Overview

Task Management System is a web application built with Python and Django. It allows users to register, sign in, and manage personal tasks through a responsive dashboard.

The project demonstrates a complete Django workflow, including authentication, CRUD operations, relational data, forms, templates, search and filtering, access control, and automated testing. It was developed as a Computer Science final project.

## Key Features

### User accounts and access control

- User registration, login, and logout.
- Protected pages for authenticated users.
- Personal task ownership: regular users can access only their own tasks.
- Staff users can view and manage all tasks.
- Django Admin interface for administrative management.

### Task management

- Create, view, update, and delete tasks.
- Set task priority: Low, Medium, or High.
- Track task progress and completion status.
- Add optional due dates.
- Search tasks by title and description.
- Filter tasks by status and priority.
- View task statistics on the personal dashboard.

### Interface

- Django templates with HTML and CSS.
- Responsive layout for different screen sizes.
- Safe wrapping of long task content.

## Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.12+ | Main programming language |
| Django 6.0.2 | Web framework |
| SQLite | Local development database |
| Django ORM | Database models and queries |
| Django Authentication | Registration, login, and access control |
| HTML5 / CSS3 | User interface |
| Django Templates | Server-rendered pages |
| Django TestCase | Automated application tests |
| GitHub Actions | Continuous integration |

## Architecture

The application follows Django's Model-View-Template (MVT) pattern:

```text
Browser request
      |
      v
    URL route
      |
      v
     View
    /    \
   v      v
 Model  Form / validation
   |      |
   v      v
Database  Template
             |
             v
        HTML response
```

## Project Structure

```text
Task-Management-System/
├── .github/
│   └── workflows/       # GitHub Actions workflow
├── config/              # Django project settings and URL configuration
├── docs/
│   └── QA_CHECKLIST.md  # Manual QA checklist
├── tasks/               # Main application
│   ├── migrations/      # Database migrations
│   ├── templates/       # Django HTML templates
│   ├── admin.py         # Django Admin configuration
│   ├── forms.py         # Forms and validation
│   ├── models.py        # Task data model
│   ├── tests.py         # Automated tests
│   ├── urls.py          # Application routes
│   └── views.py         # Application views
├── static/
│   └── tasks/           # CSS and static assets
├── .env.example         # Example environment configuration
├── .gitignore
├── manage.py
├── requirements.txt
└── README.md
```

## Local Setup — Windows

### Requirements

- Windows 10 or 11.
- Python 3.12 or newer.
- `pip` (included with standard Python installations).

### 1. Clone the repository

```powershell
git clone https://github.com/lacelyn5/Task-Management-System.git
cd Task-Management-System
```

You can also download the repository as a ZIP archive and extract it.

### 2. Create a virtual environment

```powershell
py -m venv .venv
```

### 3. Activate the virtual environment

**Command Prompt:**

```bat
.venv\Scripts\activate.bat
```

**PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

If PowerShell prevents script activation, use Command Prompt or follow Microsoft's guidance for the execution policy. Do not change system-wide security settings just for this project.

### 4. Install dependencies

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

### 5. Configure environment variables (optional)

The repository contains `.env.example` with the supported local settings:

- `DJANGO_SECRET_KEY`
- `DJANGO_DEBUG`
- `DJANGO_ALLOWED_HOSTS`

To create your local `.env` file in PowerShell:

```powershell
Copy-Item .env.example .env
```

Or in Command Prompt:

```bat
copy .env.example .env
```

For local development, review the example values and replace the placeholder secret key with a new random value. The `.env` file is excluded from Git; do not commit real secrets.

### 6. Apply database migrations

```powershell
python manage.py migrate
```

### 7. Create an administrator account (optional)

```powershell
python manage.py createsuperuser
```

### 8. Start the development server

```powershell
python manage.py runserver
```

Open the application:

**http://127.0.0.1:8000/**

Django Admin:

**http://127.0.0.1:8000/admin/**

## Running Tests

Run the automated Django test suite from the project root, with the virtual environment activated:

```powershell
python manage.py test
```

The tests cover areas including:

- Registration and authentication.
- Task creation and default values.
- User ownership and access isolation.
- CRUD permissions and staff access.
- Search and combined filtering.
- Long task text handling.
- Dashboard statistics.

A separate [manual QA checklist](docs/QA_CHECKLIST.md) is provided for browser and responsive-layout checks. It is a checklist for manual verification, not a claim that every check has been executed.

You can also run Django's project consistency checks:

```powershell
python manage.py check
python manage.py makemigrations --check --dry-run
```

## Main Data Model

Each `Task` record includes:

- Title.
- Description.
- Completion status.
- Priority.
- Optional due date.
- Owner (the authenticated user who created the task).

The task owner is assigned automatically when a task is created.

## Security and Access Control

- Task management pages require authentication.
- Regular users can retrieve, edit, and delete only their own task records.
- Attempts to access another user's task are denied.
- Staff users can manage all tasks.
- Django CSRF protection is enabled for POST forms.
- Password validation uses Django's built-in validators.
- Registration prevents duplicate email addresses (case-insensitive).
- Local databases, `.env` files, caches, and secrets are excluded from Git.

## Continuous Integration

The repository includes a GitHub Actions workflow that runs on pushes and pull requests to `main`.

The workflow installs the project dependencies, runs Django's system check, verifies migration consistency, applies migrations, and executes the automated test suite.

See the [Actions tab](https://github.com/lacelyn5/Task-Management-System/actions) for workflow runs and their results.

## Future Improvements

Potential next steps for the application include:

- Email reminders for upcoming due dates.
- Task categories and tags.
- File attachments.
- Calendar view.
- Team collaboration features.
- PostgreSQL support.
- Public deployment with production settings.
- Pagination for larger task lists.

These are possible enhancements and are not presented as existing features.

## Development Notes

The supplied settings and SQLite configuration are intended for local development. Before deploying publicly, configure a secure production secret key, set `DJANGO_DEBUG=False`, configure allowed hosts, and use an appropriately managed production database and hosting environment.

---

**Created by Maksim Kernazhytski**
