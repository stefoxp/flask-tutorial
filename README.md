# Tutorial ufficiale

> da https://flask.palletsprojects.com/en/3.0.x/tutorial/

## Project Layout

```bash
py -m pip freeze > requirements.txt
```

## Application Setup

```bash
# lancia l'applicazione
py -m flask --app flaskr run --debug
```

per visualizzare il risultato: http://127.0.0.1:5000/hello

## Define and Access the Database

```bash
# Run the init-db command
py -m flask --app flaskr init-db
```

## Blueprints and Views

## Templates

Per visualizzare la pagina di registrazione: http://127.0.0.1:5000/auth/register

## Static Files

## Blog Blueprint

## Make the Project Installable

```bash
# install your project in the virtual environment
py -m pip install -e .
```

## Test Coverage

```bash
py -m pip install coverage
```

To run the tests, use the pytest command

```bash
pytest
```

To measure the code coverage of your tests, use the coverage command to run pytest instead of running it directly.

```bash
coverage run -m pytest
# You can either view a simple coverage report in the terminal:
coverage report
# An HTML report allows you to see which lines were covered in each file:
coverage html
```

## Deploy to Production

This part of the tutorial assumes you have a server that you want to deploy your application to. 
It gives an overview of how to create the distribution file and install it, 
but won’t go into specifics about what server or software to use. You can set up a new environment on
your development computer to try out the instructions below.

### Build and Install

```bash
py -m pip install build
py -m build --wheel
```

You can find the file in dist/flaskr-1.0.0-py3-none-any.whl. The file name is in the format of {project name}-{version}-{python tag} -{abi tag}-{platform tag}.

Copy this file to another machine, set up a new virtualenv, then install the file with pip

```bash
py -m pip install flaskr-1.0.0-py3-none-any.whl
```

Since this is a different machine, you need to run init-db again to create the database in the instance folder

```bash
py -m flask --app flaskr init-db
```

When Flask detects that it’s installed (not in editable mode), it uses a different directory for the instance folder. 
You can find it at .venv/var/flaskr-instance instead.

### Configure the Secret Key

You can use the following command to output a random secret key:

```bash
py -c 'import secrets; print(secrets.token_hex())'
```

Create the config.py file in the instance folder, which the factory will read from if it exists. Copy the generated value into it.

.venv/var/flaskr-instance/config.py

SECRET_KEY = '192b9bdd22ab9ed4d12e236c78afcb9a393ec15f71bbf5dc987d54727823bcbf'

### Run with a Production Server

When running publicly rather than in development, you should not use the built-in development server (flask run). 
The development server is provided by Werkzeug for convenience, but is not designed to be particularly efficient, stable, or secure.

Instead, use a production WSGI server. For example, to use Waitress, first install it in the virtual environment:

```bash
py -m pip install waitress
```

You need to tell Waitress about your application, but it doesn't use --app like flask run does. You need to tell it 
to import and call the application factory to get an application object.

```bash
waitress-serve --call 'flaskr:create_app'
```

Serving on http://0.0.0.0:8080

Waitress is just an example, chosen for the tutorial because it supports both Windows and Linux. 
There are many more WSGI servers and deployment options that you may choose for your project.
