# Manual QA checklist

This checklist is a **test plan**, not a claim that all checks have passed.
Run the project locally before marking any items complete.

## Authentication and authorization

- [ ] New user can register with a valid username, email and strong password.
- [ ] Duplicate email address (case-insensitive) shows a validation error.
- [ ] User can log in with valid credentials and log out.
- [ ] A guest opening `/` is redirected to the login page.
- [ ] A guest cannot create, edit or delete tasks.
- [ ] User A cannot see User B's tasks in their dashboard or search results.
- [ ] User A receives HTTP 404 when trying to edit or delete User B's task.

## Task management

- [ ] A new task saves with the correct owner and default priority.
- [ ] Optional description and due date can be left empty.
- [ ] An existing task can be edited (title, description, priority, deadline and completion status).
- [ ] Clicking Delete first opens a confirmation page; only confirming removes a task.
- [ ] Search matches task titles and descriptions.
- [ ] Status and priority filters work alone and in combination.
- [ ] Task statistics reflect all of the current user's tasks even when filters are active.

## UI / responsive testing

- [ ] A long uninterrupted title stays inside a task card.
- [ ] A long uninterrupted description wraps instead of overflowing.
- [ ] Layout remains usable on narrow mobile screens.
- [ ] A very long task description doesn't break the edit form.

## Suggested browser checks

Use Chrome or Firefox at desktop width and mobile viewport (~375 px).
Record actual results and a screenshot for any failure.

## Automated checks

```bash
python manage.py check
python manage.py makemigrations --check --dry-run
python manage.py test
```

Automated Django tests are in [`../tasks/tests.py`](../tasks/tests.py).
