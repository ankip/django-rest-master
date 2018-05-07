# Django REST Swagger
Swagger/OpenAPI Documentation Generator for Django REST Framework
---

**Note:** you are viewing documentation for version 2, using Django REST Framework 3.5+ and CoreAPI. Documentation for previous versions is available [here](http://django-rest-swagger.readthedocs.io/en/stable-0.3.x/).

---

## Installation

`$ pip install django-rest-swagger`


Add `'rest_framework_swagger'` to `INSTALLED_APPS` in Django settings.

**settings.py**
```python
INSTALLED_APPS = [
    ...
    'rest_framework_swagger',
    ...
]
```

## Quick start

To quickly get started, use the `get_swagger_view` shortcut. This will produce
a schema view which uses common settings. For more advanced usage, please see
the schemas section.

#### Example

**views.py**
```python
from django.conf.urls import url
from rest_framework_swagger.views import get_swagger_view

schema_view = get_swagger_view(title='Pastebin API')

urlpatterns = [
    url(r'^$', schema_view)
]
```

#### View in the browser
![Screenshot](/img/ui-screenshot.png)


## Example app
An example based on the [Django REST Tutorial](http://www.django-rest-framework.org/tutorial/1-serialization/) ships with the project. It and can be optionally locally using Docker, or deployed for free on heroku.

Log in credentials are:
```
username: amy
password: amy
```

### Docker Instructions

Ensure [Docker](https://www.docker.com/) Docker is installed on your system.

First, clone the repository.

To quickly get up and running using the Docker image, simply run:

`$ ./run_example.sh`

The initial run may take several minutes to build. Once complete, the 
application will be available at `http://localhost:8000`

## Changes in 2.0
Version 2.0 is fundamentally different from previous versions and leverages the new schema generation features introduced in Django REST Framework 3.4. Introspection is performed by the framework and uses CoreAPI to store definitions. This is a breaking change from previous versions which were responsible for introspection as well as overrides.

New:

- SwaggerUI and the OpenAPI spec are renderer classes (simpler configuration)
- SwaggerUI 2.1.6
- Improved performance
- Allow multiple instances of Swagger UI in a single Django project
- Allow rendering the OpenAPI JSON spec independently
- Improved control of authentication mechanisms

Deprecated:

- YAML docstrings
