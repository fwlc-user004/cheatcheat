# 🚀 Django Cheat Sheet

This cheat sheet provides a quick reference guide for setting up and working with Django projects, including models, views, templates, and APIs.

## 🏗️ Project Setup
```bash
django-admin startproject myproject  # Create a new Django project
cd myproject
python manage.py startapp myapp  # Create a new Django app
python manage.py runserver  # Start the development server
```
🔹 **Ensure Django is installed** before running the commands above:
```bash
pip install django
```

---

## 🗃️ Models (Database Schema)
```python
from django.db import models

class Post(models.Model):
    title = models.CharField(max_length=100)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)

    def __str__(self):
        return self.title
```

🔹 **Apply Database Migrations**
```bash
python manage.py makemigrations  # Create migration files
python manage.py migrate  # Apply migrations to the database
```

---

## 🔐 Creating a Superuser
```bash
python manage.py createsuperuser  # Follow prompts to create an admin user
```

---

## 🎛️ Admin Panel Configuration
```python
from django.contrib import admin
from .models import Post

admin.site.register(Post)  # Register the model to show in Django Admin
```

🔹 **Access Admin Panel:**  
Run the server and visit 👉 `http://127.0.0.1:8000/admin`

---

## 🌍 Views (Handling Requests)
```python
from django.shortcuts import render
from .models import Post

def home(request):
    posts = Post.objects.all()
    return render(request, 'home.html', {'posts': posts})
```

---

## 🛤️ URL Routing
```python
from django.urls import path
from .views import home

urlpatterns = [
    path('', home, name='home'),
]
```

---

## 🎨 Templates (HTML Rendering)
📂 **home.html**  
```html
{% for post in posts %}
    <h2>{{ post.title }}</h2>
    <p>{{ post.content }}</p>
{% endfor %}
```

---

## 🔍 Database Management via Django Shell
```bash
python manage.py shell
```
```python
from myapp.models import Post
Post.objects.create(title="Hello", content="Django is awesome!")
Post.objects.all()  # Retrieve all posts
```
🔹 **Exit the shell** using:
```bash
exit()
```

---

## 📝 Forms (User Input)
```python
from django import forms
from .models import Post

class PostForm(forms.ModelForm):
    class Meta:
        model = Post
        fields = ['title', 'content']
```

---

## 📡 Django REST Framework (DRF)
🔹 **Install DRF**
```bash
pip install djangorestframework
```
🔹 **Add `rest_framework` to `INSTALLED_APPS` in `settings.py`**
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```

🔹 **Create a Serializer**
```python
from rest_framework import serializers
from .models import Post

class PostSerializer(serializers.ModelSerializer):
    class Meta:
        model = Post
        fields = '__all__'
```

🔹 **Basic API View**
```python
from rest_framework.response import Response
from rest_framework.decorators import api_view
from .models import Post
from .serializers import PostSerializer

@api_view(['GET'])
def post_list(request):
    posts = Post.objects.all()
    serializer = PostSerializer(posts, many=True)
    return Response(serializer.data)
```

🔹 **Add API URL**
```python
from django.urls import path
from .views import post_list

urlpatterns = [
    path('api/posts/', post_list, name='post-list'),
]
```

---

## ✅ Running Tests
```bash
python manage.py test
```
🔹 **Example of a simple test case:**
```python
from django.test import TestCase
from .models import Post

class PostModelTest(TestCase):
    def test_create_post(self):
        post = Post.objects.create(title='Test Post', content='Testing content')
        self.assertEqual(post.title, 'Test Post')
```

---

## ⚡ Extra Useful Commands
```bash
python manage.py showmigrations  # Show applied and pending migrations
python manage.py check  # Check for potential project errors
python manage.py collectstatic  # Collect static files (for production)
python manage.py flush  # Clear all database data
```

---
