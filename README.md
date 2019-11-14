### Fork on Repl.it

Repl: https://repl.it/@MattHeerspink/Django-Template

Page: https://django-template--mattheerspink.repl.co/

---

<h1>Test<h1/>

<p><iframe height="400px" width="100%" src="https://repl.it/@MattHeerspink/Django-Template?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe></p>


---
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
---
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
    +---custom_app_name1            <-
    |   |   admin.py         
    |   |   apps.py
    |   |   models.py
    |   |   tests.py
    |   |   urls.py                 <-
    |   |   views.py                <-
    |   |   __init__.py
    |   |
    |   +---migrations
    |   |       __init__.py
    |   |
    |   +---static                  <-
    |   |   \---css
    |   |           style.css
    |   |
    |   \---templates               <-
    |       |   base.html           <-
    |       |
    |       \---custom_app_name1    <-
    |           \---pages
    |               |   about.html
    |               |   home.html
    |               |
    |               \---components
    |                       navbar.html
    |                       sidebar.html
    |
    \---custom_project_name1        <-
            settings.py
            urls.py                 <-
            wsgi.py
            __init__.py

```
Add templates/ path to 'DIRS'
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

Run the dev server and migrate the database
```
py manage.py runserver

py manage.py migrate

```
