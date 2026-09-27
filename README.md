# Master of Jokes

A joke-sharing web app built with **Flask** and **SQLite**. Users sign up, post jokes, rate and comment on other people's jokes, and have public profile pages.

Built as a 5-person team project for a software engineering course at Indiana University.

## Features

- **Accounts:** register, log in and log out, with passwords hashed using Werkzeug
- **Jokes:** create, edit and delete your own jokes, and browse the feed
- **Ratings:** rate other users' jokes, with each joke's average rating shown (one rating per user per joke)
- **Comments:** comment on jokes and delete your own comments
- **User profiles:** a public profile page per user showing their jokes and activity stats (jokes, ratings, comments, engagement score)

## My contributions

I (Niki Mohseny) owned the **social features** of the app:

- **User profiles:** the `/profile/<username>` route, the aggregate stats queries (ratings, averages, engagement score), the profile template, and the `created` user field with its schema migration (`migrate_add_user_created.py`)
- **Ratings:** the `rating` table, the unique-per-user constraint, the rate endpoint, average-rating display and migration (`migrate_add_ratings.py`)
- **Comments:** the `comment` table, add/delete comment endpoints with ownership checks, the comment UI and migration (`migrate_add_comments.py`)

## Tech stack

Python · Flask · Jinja2 · SQLite · HTML/CSS · pytest

## Project structure

```
flaskr/
├── __init__.py      # app factory
├── auth.py          # register / login / logout / profile routes
├── jokes.py         # joke CRUD, ratings, comments
├── db.py            # SQLite connection + `init-db` CLI command
├── schema.sql       # user, post, rating, comment tables
├── templates/       # Jinja2 templates
└── static/          # CSS
tests/               # pytest suite (auth, db, app factory)
populate_db.py       # seeds the database with sample users and jokes
```

## Running locally

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -e .

flask --app flaskr init-db       # create the database
python populate_db.py            # optional: load sample data
flask --app flaskr run --debug   # http://127.0.0.1:5000
```

## Tests

```bash
pip install pytest
pytest
```

## Team

Luis Burrola · Esme McDermott · Niki Mohseny · Colin Thompson · Sreeram Tirumala
