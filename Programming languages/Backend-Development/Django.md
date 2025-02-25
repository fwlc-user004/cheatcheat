# Django Cheat Sheet

## 📌 Introduction
Django is a high-level Python web framework that promotes rapid development and clean, pragmatic design.

---

## 🚀 Installation & Setup
```sh
pip install django
django-admin startproject myproject
cd myproject
python manage.py runserver
```

---

## 🏗️ Project Structure
```plaintext
myproject/
 ├── manage.py
 ├── myproject/
 │   ├── __init__.py
 │   ├── settings.py
 │   ├── urls.py
 │   ├── wsgi.py
 ├── app/
 │   ├── migrations/
 │   ├── __init__.py
 │   ├── admin.py
 │   ├── apps.py
 │   ├── models.py
 │   ├── tests.py
 │   ├── views.py
 │   ├── urls.py
```

---

## 🔹 Creating an App
```sh
python manage.py startapp myapp
```

Register it in `settings.py`:
```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'myapp',
]
```

---

## 🔹 Models
### Creating a Model
```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=200)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
```

### Apply Migrations
```sh
python manage.py makemigrations
python manage.py migrate
```

---

## 🔹 Admin Panel
### Create Superuser
```sh
python manage.py createsuperuser
```

### Register Model in `admin.py`
```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)
```

Run the server and access the admin panel:
```sh
python manage.py runserver
# Go to http://127.0.0.1:8000/admin/
```

---

## 🔹 Views & URLs
### Create a View in `views.py`
```python
from django.http import HttpResponse

def home(request):
    return HttpResponse("Hello, Django!")
```

### Define URL in `urls.py`
```python
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]
```

---

## 🔹 Templates
### Create a Template in `templates/home.html`
```html
<!DOCTYPE html>
<html>
<head>
    <title>My Django App</title>
</head>
<body>
    <h1>Welcome to Django!</h1>
</body>
</html>
```

### Update View to Use Template
```python
from django.shortcuts import render

def home(request):
    return render(request, 'home.html')
```

---

## 🔹 Static Files
Enable static files in `settings.py`:
```python
STATIC_URL = '/static/'
```

Use in Templates:
```html
{% load static %}
<img src="{% static 'images/logo.png' %}" alt="Logo">
```

---

## 🔹 Forms
### Create a Form in `forms.py`
```python
from django import forms

class ContactForm(forms.Form):
    name = forms.CharField(max_length=100)
    email = forms.EmailField()
    message = forms.CharField(widget=forms.Textarea)
```

### Use in View
```python
from .forms import ContactForm

def contact(request):
    form = ContactForm()
    return render(request, 'contact.html', {'form': form})
```

---

## 🔹 ORM Queries
### Create an Object
```python
post = Post(title="Django Guide", content="This is a Django tutorial.")
post.save()
```

### Query Objects
```python
all_posts = Post.objects.all()
first_post = Post.objects.first()
specific_post = Post.objects.get(id=1)
```

### Update an Object
```python
post = Post.objects.get(id=1)
post.title = "Updated Title"
post.save()
```

### Delete an Object
```python
post = Post.objects.get(id=1)
post.delete()
```

---

## 🔹 User Authentication
### Enable Authentication in `settings.py`
```python
LOGIN_REDIRECT_URL = '/'
LOGOUT_REDIRECT_URL = '/'
```

### Login & Logout URLs
```python
from django.contrib.auth import views as auth_views

urlpatterns = [
    path('login/', auth_views.LoginView.as_view(), name='login'),
    path('logout/', auth_views.LogoutView.as_view(), name='logout'),
]
```

---



