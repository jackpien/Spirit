# Spirit

[![Build Status](https://img.shields.io/travis/nitely/Spirit.svg?style=flat-square)](https://travis-ci.org/nitely/Spirit)
[![Coverage Status](https://img.shields.io/coveralls/nitely/Spirit.svg?style=flat-square)](https://coveralls.io/r/nitely/Spirit)
[![pypi](https://img.shields.io/pypi/v/django-spirit.svg?style=flat-square)](https://pypi.python.org/pypi/django-spirit)
[![licence](https://img.shields.io/pypi/l/django-spirit.svg?style=flat-square)](https://raw.githubusercontent.com/nitely/Spirit/master/LICENSE)

Spirit is a Python based forum built using the Django framework.

To see it in action, please visit [The Spirit Project](http://spirit-project.com/).

Forked by Jack Pien

## Adding into existing Django project

Inspired by [this forum post](http://community.spirit-project.com/topic/318/tutorial-for-not-advanced-django-users/)

Assuming you have a fresh Django 1.8 project (via django-admin startproject your_dj_project)
* Add spirit folder to your project
* cp Spirit/examples/project/settings/<files> to your_dj_project/your_dj_project/ (where settings.py lives)
   1. base.py
   1. dev.py
   1. prod.py
* cd your_dj_project/your_dj_project (where settings.py lives)
* mv settings.py settings_old.py
* create new settings.py

```
from .dev import *

ROOT_URLCONF = '[your_dj_project].urls'
WSGI_APPLICATION = '[your_dj_project].wsgi.application'
```

* Update your_dj_project/your_dj_project/urls.py

```
import spirit.urls


urlpatterns = [
...
    url(r'^forum/', include(spirit.urls)),
...
]
```

* python manage.py migrate
* python manage.py createcachetable
* python manage.py collectstatic

## Compatibility

* Python 2.7, 3.3, 3.4 (recommended) and 3.5
* Django 1.8 LTS
* PostgreSQL (recommended), MySQL, Oracle Database and SQLite

## Installing (Advanced)

Check out the [example project](https://github.com/nitely/Spirit/tree/master/example).

## Upgrading

Detailed upgrade instructions are listed in [Upgrading Spirit](https://github.com/nitely/Spirit/wiki/Upgrading)

## Testing

The `runtests.py` script enable you to run the test suite of spirit.

- Type `./runtests.py` to run the test suite using the settings from the `spirit` folder.
- Type `./runtests.py example` to run the test suite using the settings from the `example` folder.

## License

MIT
