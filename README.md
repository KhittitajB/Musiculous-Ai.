# Musiculous AI

Musiculous AI is a Django web application for AI-assisted music creation. Users can sign up, log in, create song drafts from prompts, manage their personal song library, and control whether a song is public or private.

This project is currently in MVP development.

## Features (Current)

- User authentication (sign up, log in, log out)
- Custom Django user model
- Public landing page
- Library pages for:
	- viewing owned songs
	- creating song drafts
	- viewing song details
	- editing song metadata
	- deleting songs
	- toggling public/private visibility
- Django admin setup for Song management

## Planned Features

- AI music generation API integration
- Audio playback and file handling improvements
- Downloadable MP3 support
- Shareable public song links
- Enhanced dashboard and UX polish

## Tech Stack

- Python
- Django
- SQLite (development)
- HTML/CSS templates

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

## Local Setup

1. Clone this repository.
2. Create and activate a virtual environment.
3. Install dependencies.

```bash
pip install django
```

4. Run migrations.

```bash
python manage.py makemigrations
python manage.py migrate
```

5. Create an admin account.

```bash
python manage.py createsuperuser
```

6. Start the development server.

```bash
python manage.py runserver
```

7. Open in browser:

```text
http://127.0.0.1:8000/
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

Active development. Core auth and library flow are implemented; AI generation pipeline is next.
