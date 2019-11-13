```
virtualenv django_repl

django_repl/scripts/activate

pip install django

django-admin.py startproject django_app1

cd djangoapp_1

py manage.py startapp app1
```
Add 'herokuapp' to installed apps in settings.py
```
py manage.py migrate

py manage.py runserver

```