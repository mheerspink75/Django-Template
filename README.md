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
---
or

### Install from scratch
```
virtualenv custom_env_name

source custom_env_name/scripts/activate

pip install django

django-admin.py startproject custom_project_name1

cd custom_project_name1

pip freeze > requirements.txt

touch runtime.txt

runtime.txt > python-3.7.4

py manage.py startapp custom_app_name1
```
Add 'custom_app_name1' to installed apps in settings.py
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
Migrate the database and run the dev server
```
py manage.py migrate

py manage.py runserver
```

Add templates/ and static/ folders and files structure.

Code custom_project_name1/urls, custom_app_name1/urls, custom_app_name1/views, code templates/ and static/ files.

```
C:.
\---custom_directory_folder_name -master  
    |   .gitignore
    |   manage.py
    |   README.md
    |   requirements.txt
    |   runtime.txt
    |
    +---custom_app_name1            <- App Folder
    |   |   admin.py         
    |   |   apps.py
    |   |   models.py
    |   |   tests.py
    |   |   urls.py                 <- App URL and path routing
    |   |   views.py                <- ( /custom_app_name1/templates/pages ) -> render method
    |   |   __init__.py
    |   |
    |   +---migrations
    |   |       __init__.py
    |   |
    |   +---static                  <- Required Folder Name -> ( /static ) -> Static files (CSS, JavaScript, Images) -> STATICFILES_DIRS = (os.path.join(BASE_DIR, 'static')
    |   |   \---css                 <- Custom folder and file are names ok inside the required folder
    |   |           style.css
    |   |
    |   \---templates               <- Required Folder Name -> ( /templates ) -> 'DIRS': [os.path.join(BASE_DIR, 'templates')]
    |       |   base.html           <- Required File -> ( templates/base.html ) at top level
    |       |
    |       \---custom_app_name1    <- Required Folder Name ->  ( Same name as app folder is required )
    |           \---pages           <- Custom folder and file are names ok inside the required folder
    |               |   about.html
    |               |   home.html
    |               |
    |               \---components
    |                       navbar.html
    |                       sidebar.html
    |
    \---custom_project_name1        <- Project folder
            settings.py             <- Project settings
            urls.py                 <- Project URL and path routing
            wsgi.py
            __init__.py

```
Add templates/ path to TEMPLATES 'DIRS' in settings.py
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
Add STATIC_ROOT, STATIC_URL, and STATICFILES_DIRS to settings.py
```
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.11/howto/static-files/
STATIC_ROOT  =   os.path.join(BASE_DIR, 'staticfiles')
STATIC_URL = '/static/'

# Extra lookup directories for collectstatic to find static files
STATICFILES_DIRS = (
    os.path.join(BASE_DIR, 'custom_app_name1/static'),
)
```

Run the dev server, migrate the database, collect staticfiles
```
py manage.py runserver

py manage.py migrate

py manage.py collectstatic

```
