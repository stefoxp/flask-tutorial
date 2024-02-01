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
