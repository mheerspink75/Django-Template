### Fork on Repl.it
https://repl.it/@MattHeerspink/Django-Template

or

### Install from cloned repo
Clone the repo, remove the git directory, pip install requirements.txt
```
git clone https://github.com/mheerspink75/Django-Template.git

rm -rf .git

virtualenv custom_name

custom_name/scripts/activate

pip install -r requirements.txt
```
or

### Install from scratch
```
virtualenv django_repl

django_repl/scripts/activate

pip install django

django-admin.py startproject django_app1

cd djangoapp_1

pip freeze > requirements.txt

touch runtime.txt

runtime.txt > python-3.7.4

py manage.py startapp app1
```
Add 'app1' to installed apps in settings
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'app1'
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
