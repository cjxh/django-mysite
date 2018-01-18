# django-mysite
Creating a django app from scratch. Practice with migrations.

## Set up application
1. Using PyCharm, `Create New Project` > `Django`. 
2. Specify `Location` (i.e. `\SampleProjects\py\mysite`) and `Application name` (i.e. `polls`)
3. Under `Project Interpreter`, create a new Virtualenv (use Python 3.6.2).

## Project Structure
There will be a `manage.py` file as well as two directories `mysite` and `polls`.
- `manage.py` is a command-line utility to interact with Django project.
- `mysite` is a container for your project. 
- `mysite/__init__.py`: empty file, tells Python this dir is a Python package.
- `mysite/settings.py`: Django project configurations.
- `mysite/urls.py`: URL declarations for Django project.
- `mysite/wsgi.py`: defines an entry-point for WSGI-compatible web servers for project.
- `polls` contains all the files required for the Django application.
- `polls/__init__.py`
- `polls/models.py`
- `polls/views.py`
- `polls/migrations`
To add an app to the project, run `./manage.py startapp <app_name>`

## [Set up DB](https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-django-application-on-ubuntu-16-04)
1. Install postgresql.
2. Create a DB and a DB user.
`$ brew info services` for help on how to start your postgresql server.
`$ brew services start postgresql`
`$ psql`
`postgres=# CREATE DATABASE myproject;`
`postgres=# CREATE USER myprojectuser WITH PASSWORD 'password';`
`postgres=# ALTER ROLE myprojectuser SET client_encoding TO 'utf8';`
`postgres=# ALTER ROLE myprojectuser SET default_transaction_isolation TO 'read committed';` blocks reads from uncommitted transactions
`postgres=# ALTER ROLE myprojectuser SET timezone TO 'UTC';`
`postgres=# GRANT ALL PRIVILEGES ON DATABASE myproject TO myprojectuser;` to give db user access rights to the db

## Configure Django DB Settings
In `~/<path-to-project>/mysite/settings.py`, replace the following:
```
. . .

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}

. . .
```

## Launch Django Server
Run `./manage.py runserver` in the console, then visit `localhost:8000`.
