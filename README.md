# Django-cheat-sheet
Cheat sheet for django


## Cmd
django-admin startproject <project name>

python manage.py runserver

python manage.py makemigrations   //cria um arquivo de migração

python manage.py migrate          //executa a migração

## Shell
python manage.py shell
from <app>.models import <Model>

all_objects = Model.objects.all()

my_object = Model.objects.get(pk=<id>)

## Settings.py
LANGUAGE_CODE = 'pt-br'

TIME_ZONE = 'America/Sao_Paulo'

### arquivos estáticos (css, js)
STATIC_URL = '/static/'

STATICFILES_DIR = ['static']
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
