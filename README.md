### Fork on Repl.it

Repl: https://repl.it/@MattHeerspink/Django-Template

Page: https://django-template--mattheerspink.repl.co/

or

### Install from cloned repo
Clone the repo, remove the git directory, pip install requirements.txt
```
git clone https://github.com/mheerspink75/Django-Template.git

rm -rf .git

virtualenv custom_env_name

source custom_env_name/scripts/activate

pip install -r requirements.txt

py manage.py migrate

py manage.py runserver
```
or

### Install from scratch
```
virtualenv custom_env_name

custom_env_name/scripts/activate

pip install django

django-admin.py startproject custom_project_name1

cd custom_project_name1

pip freeze > requirements.txt

touch runtime.txt

runtime.txt > python-3.7.4

py manage.py startapp custom_app_name1
```
Add 'custom_app_name1' to installed apps in settings
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'custom_app_name1'
]
```
Add 'DIRS' path to Templates
```
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [os.path.join(BASE_DIR, 'templates')],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```
Add STATICFILES_DIRS
```
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/2.2/howto/static-files/

STATIC_URL = '/static/'

STATICFILES_DIRS = (
    os.path.join(BASE_DIR, 'static'),
)
```
Migrate the database and run the dev server
```
py manage.py migrate

py manage.py runserver

```
