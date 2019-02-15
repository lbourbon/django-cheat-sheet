# Django-cheat-sheet
Cheat sheet for django

## Cmd
django-admin startproject [project name]
	
(se clonando repositório: git clone github_url)

-> cd [nome do projeto]

python3 -m venv venv

. venv/bin/activate

pip install django OU

(se tiver requirements pip install -r requirements.dev.txt, lembrar de criar SECRET_KEY no .env)

python manage.py runserver

python manage.py makemigrations   //cria um arquivo de migração

python manage.py migrate          //executa a migração

python manage.py createsuperuser  //cria superuser p admin


## Apps
python manage.py startapp [app name]

Include app name in INSTALLED_APPS in settings.py

## Custom User Model
If you’re starting a new project, it’s highly recommended to set up a custom user model, even if the default User model is sufficient for you. This model behaves identically to the default user model, but you’ll be able to customize it in the future if the need arises:

<code>
from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
</code>

Don’t forget to point AUTH_USER_MODEL to it. Do this before creating any migrations or running manage.py migrate for the first time.

Also, register the model in the app’s admin.py:
<code>
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import User
	
admin.site.register(User, UserAdmin)
</code>

## Shell
python manage.py shell

from <app>.models import <Model>


all_objects = Model.objects.all()

my_object = Model.objects.get(pk=<id>)

## Settings.py
<code>
LANGUAGE_CODE = 'pt-br'

TIME_ZONE = 'America/Sao_Paulo'
</code>
### arquivos estáticos (css, js)
<code>
STATIC_URL = '/static/'

STATICFILES_DIR = ['static']
</code>
#### Obs: incluir no html:
```html
{% load static %}  // topo
<link rel="stylesheet" href="{% static 'style.css' %}">
<script src="{% static 'behavior.js' %}"></script>
```

## Template Tags
### base.html
```html
<!doctype html>
<html lang="pt-BR">
<head>
	<meta charset="UTF-8">
	<meta name="viewport"
	      content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css">
	<title>{% block title %} {% endblock %}</title>
</head>
<body>
<div class="container">
	{% block main %}
	{% endblock %}
</div>
</body>
</html>
```
### outros.html
```html
{% extends 'base.html'%}
{% load bootstrap %}
{% block title %} <Escolher Título>  {% endblock %}
{% block main%}
  <Adicionar conteúdo do <body>>
{% endblock %}
```
