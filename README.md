# recipe-app-api

Recipe API project

## Tech Stack

- Docker
- Python 3
- Django

## Development

### Add a migration

For example, to add the `Recipe` model, in the `app/core/models.py` file add the following:

```python
class Recipe(models.Model):
    # Add attributes as columns with description...
```

and then run the following in your terminal:

```bash
docker-compose run --rm app sh -c "python manage.py makemigrations"
```

### Add a model to admin page

For example, to add the `Recipe` model to Django admin page, in the `app/core/admin.py` file add the following:

```python
admin.site.register(models.Recipe)
```

### Add a new app

For example, to add the `Recipe` app, run the following command:

```bash
docker-compose run --rm app sh -c "python manage.py startapp recipe"
```

Then change into the directory and remove uneeded files:

```bash
cd app/recipe
rm -rf admin.py migrations models.py tests.py
mkdir tests
touch tests/__init__.py
```

Then add the app into the `app/app/settings.py` file:

```python
INSTALLED_APPS = [
    # ...
    'recipe',
]
```

## Testing

To run tests, run the following command:

```bash
docker-compose run --rm app sh -c "python manage.py test"
```

## Linting

Just lint:

```bash
docker-compose run --rm app sh -c "python manage.py test && flake8"
```

Test and lint:

```bash
docker-compose run --rm app sh -c "python manage.py test && flake8"
```

## License

[MIT](https://choosealicense.com/licenses/mit/)
