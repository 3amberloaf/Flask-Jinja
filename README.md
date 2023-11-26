# Introduction

This program focuses on using Flask, SQLAlchemy, Alembic, and Docker. 

# Overview 
A remote interpreter is established using the Dockerfile
(docker-compose flask service) and the database model is populated using the faker library. The address field should appear when a user is selected from the /users route. The seed must be set to 4321 in the [conftest.py](tests/conftest.py) file order to generate the same data set that I use for my
tests, which sets the first record as "Jason Brown" and the address, "9335 Gloria Street Suite 675 Mathisport, PR
63759". To ensure the program ran successfully, the teacher test will check for this address.

# Basic Steps

Your users/1 page should look like this [Screenshot](readme_images/address_field_added.png).

You need to run the [tests/test_add_user.py](tests/test_add_user.py) file with pytest, so that it
creates the users.

You will need to make the following changes to make this work:

1. Run the command to create a migration: flask db migrate -m "added address field"
2. Run the command to apply the migration: flask db upgrade
3. Set the seed in [tests/conftest.py Fixture](tests/conftest.py) to 4321

# Install Commands

1. pip(3) install -r requirements.txt
2. flask db upgrade
3. flask --debug run or flask run (no debugging)
4. pytest

## Fix Mac Permission Error after docker compose up --build  command - Run these on the terminal

* chmod +x ./development.sh
* chmod +x ./production.sh

# Docker Commands

* docker compose up --build <- builds the image in development mode and shares the volume
* docker compose up <- runs the previously built image without redoing the build process
* docker build -t myapp . <- builds it to run with gunicorn in production mode
* docker run -itp 80:8080 myapp <- runs the website / flask in console output mode
* docker exec -it <containerid> bash <- logs into container (replace <containerid> with the container id)
* docker run -itp 80:8080 myapp pytest <-runs pytest in the container image

# Flask Migrate / Alembic Commands - Must delete the migrations and instance folder / database. These will reset it

* flask db migrate -m "Initial migration." <-change the message to whatever describes the schema change
* flask db upgrade <- applies the migrations

# Libraries

* https://flask.palletsprojects.com/en/2.2.x/
* https://www.sqlalchemy.org/
* https://alembic.sqlalchemy.org/en/latest/
* https://github.com/miguelgrinberg/flask-migrate

# Extra Clarification 

* [Flask Routing](https://hackersandslackers.com/flask-routes)
* [Simple Faker tutorial](https://zetcode.com/python/faker/)
* [Faker in  Depth](https://towardsdatascience.com/faker-library-in-python-an-intriguing-expedient-for-data-scientists-7dd06f953050)
* [Jinja Templates  In Depth](https://realpython.com/primer-on-jinja-templating/)
* [Flask SQL ALchemy Tutorial](https://pythonbasics.org/flask-sqlalchemy/) <-this a general tutorial and some of our
  file names and directory structure is different.
* [Flask Blueprints](https://realpython.com/flask-blueprint/)

