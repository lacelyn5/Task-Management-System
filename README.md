# Task Management System

A web-based task management application built with **Python and Django** as my Computer Science engineering final project.

The system allows users to register, sign in and manage personal tasks through a responsive dashboard. It demonstrates a complete Django workflow: authentication, CRUD, relational data, forms, templates, search/filtering, authorization and automated testing.

## Key features

- User registration, login and logout
- Protected pages for authenticated users
- Personal task dashboard with statistics
- Create, read, update and delete tasks (CRUD)
- Low / Medium / High priority
- Optional due dates
- Completed / In Progress status
- Search by title and description
- Filter by status and priority
- User data isolation: normal users can access only their own tasks
- Staff users can view and manage all tasks
- Django Admin panel
- Responsive interface and safe wrapping of long task content
- Automated Django test suite
- GitHub Actions continuous integration

## Tech stack

- Python 3.12+
- Django 6.0.2
- SQLite
- Django ORM
- Django built-in authentication
- HTML5 / CSS3
- Django Templates
- Django TestCase
- GitHub Actions

## Architecture

The application follows Django's **MVT (Model-View-Template)** pattern.

```text
URL -> View -> Model / Database -> Template -> HTML response
```

## Project structure

```text
Task-Management-System/
├── .github/workflows/    # CI test workflow
├── config/               # Django project configuration
├── docs/QA_CHECKLIST.md  # Manual QA test plan
├── tasks/                # Main application
│   ├── migrations/
│   ├── templates/
│   ├── admin.py
│   ├── forms.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── static/               # CSS and static files
├── manage.py
├── requirements.txt
├── .env.example
└── README.md
```

## Local setup

### 1. Clone the repository

```bash
git clone https://github.com/lacelyn5/Task-Management-System.git
cd Task-Management-System
```

### 2. Create a virtual environment

Windows:

```bash
py -m venv .venv
.venv\Scripts\activate
```

macOS / Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Optional environment configuration

Copy `.env.example` to `.env` and change the secret key if desired.

Windows:

```bat
copy .env.example .env
```

macOS / Linux:

```bash
cp .env.example .env
```

The `.env` file is ignored by Git.

### 5. Apply migrations

```bash
python manage.py migrate
```

### 6. Create an administrator account (optional)

```bash
python manage.py createsuperuser
```

### 7. Run the application

```bash
python manage.py runserver
```

Application: `http://127.0.0.1:8000/`  
Admin panel: `http://127.0.0.1:8000/admin/`

## Run the tests

```bash
python manage.py test
```

The test suite covers authentication, registration, task defaults, ownership isolation, CRUD permissions, staff access, search, combined filters, long text and dashboard statistics.

A separate [manual QA checklist](docs/QA_CHECKLIST.md) is provided for browser and responsive checks. It is a proposed checklist, not a fabricated record of test execution.

For a repository consistency check:

```bash
python manage.py check
python manage.py makemigrations --check --dry-run
```

## Main data model

A `Task` contains:

- title
- description
- completion status
- priority
- due date
- owner

Each task belongs to an authenticated user. The owner is assigned automatically when a task is created.

## Security and access control

- Task management pages require authentication.
- Normal users can retrieve, edit and delete only their own task records.
- Unauthorized access to another user's task returns HTTP 404.
- Staff users can manage all tasks.
- Django CSRF protection is enabled on POST forms.
- Password validation uses Django's built-in validators.
- Registration prevents duplicate email addresses (case-insensitive).
- Local databases, `.env` files, caches and secrets are excluded from Git.

## CI

Every push and pull request to `main` runs GitHub Actions to:

1. install dependencies;
2. run `python manage.py check`;
3. verify there are no missing migrations;
4. apply migrations;
5. run the automated test suite.

## Future improvements

- Email reminders
- Task categories and tags
- File attachments
- Calendar view
- Team collaboration
- PostgreSQL
- Public deployment
- Pagination for large task lists

## About this project

This project was created as a **Computer Science engineering final project**. It demonstrates frontend/backend integration, database operations, authentication, authorization, CRUD logic and automated testing in a complete Django application.

## Development note

The supplied settings and SQLite configuration are for **local development**. Do not deploy publicly with `DJANGO_DEBUG=True` or the development fallback secret key.
