# Musiculous AI

Musiculous AI is a Django web application for AI-assisted music creation. Users can sign up, log in, create song drafts from prompts, manage songs in a personal library, and control whether songs are public or private.

This project is currently in MVP development.

## Domain Model

Current domain entities in implementation:

- User (custom auth user in login app)
- Song (owned by a User)
- Library behavior (implemented as "all songs owned by the current user")

Design note for assessors:

- The current MVP implements Library as an ownership-based view/query rather than a separate Library table.
- Folder support is planned and will be added as a separate domain entity in a future iteration.

## Features (Current MVP)

- User authentication (sign up, log in, log out)
- Custom Django user model
- Public landing page
- Library pages for owned songs:
  - viewing songs
  - creating song drafts
  - viewing song details
  - editing song metadata
  - deleting songs
  - toggling public/private visibility
- Django admin setup for Song management

## Planned Features

- AI music generation API integration
- Folder support inside library
- Audio playback and file handling improvements
- Downloadable MP3 support
- Shareable public song links
- Enhanced dashboard and UX polish

## Tech Stack

- Python
- Django
- SQLite (development)
- HTML/CSS templates

## Dependencies

Required to run this project:

- Django
- Pillow (required because Song uses ImageField)

## Project Structure

```text
musiculous/
  README.md
  musiculousAI/
    manage.py
    db.sqlite3
    musiculousAI/     # project settings and root urls
    login/            # authentication app
    library/          # song and library app
```

## Local Setup (Windows)

1. Clone this repository.
2. Open terminal and enter project folder containing manage.py.
3. Create and activate virtual environment.

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

4. Install dependencies.

```powershell
pip install django pillow
```

5. (Optional) freeze dependencies.

```powershell
pip freeze > requirements.txt
```

6. Run migrations.

```powershell
python manage.py makemigrations
python manage.py migrate
```

7. Create an admin account.

```powershell
python manage.py createsuperuser
```

8. Start the development server.

```powershell
python manage.py runserver
```

9. Open in browser.

```text
http://127.0.0.1:8000/
```

## Local Setup (Using requirements.txt)

If requirements.txt exists, use:

```powershell
pip install -r requirements.txt
```

## Main Routes (MVP)

- `/` -> public landing page
- `/auth/signup/` -> sign up
- `/auth/login/` -> login
- `/auth/logout/` -> logout confirmation
- `/library/` -> authenticated user library
- `/admin/` -> Django admin panel

## Security Notes

- Password validation uses Django built-in validators.
- Private song actions enforce ownership checks in views.
- Authentication is required for library write operations.

## Status

Active development. Core auth and library flow are implemented. Folder entity and AI generation pipeline are next.
