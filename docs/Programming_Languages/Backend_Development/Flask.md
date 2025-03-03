# Flask Cheat Sheet

## 📌 Introduction
Flask is a lightweight Python web framework used to build web applications quickly and efficiently.

---

## 🚀 Installation & Setup
```sh
pip install flask
```

### Create a Simple Flask App
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello, Flask!"

if __name__ == '__main__':
    app.run(debug=True)
```

Run the application:
```sh
python app.py
```

---

## 🏗️ Project Structure
```plaintext
my_flask_app/
 ├── app.py
 ├── static/
 ├── templates/
 │   ├── index.html
 ├── config.py
 ├── requirements.txt
 ├── .env
```

---

## 🔹 Routing
```python
@app.route('/')
def home():
    return "Welcome to Flask!"

@app.route('/about')
def about():
    return "About Page"

@app.route('/user/<name>')
def user(name):
    return f"Hello, {name}!"
```

---

## 🔹 Templates
Create a template `templates/index.html`:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Flask App</title>
</head>
<body>
    <h1>Welcome to Flask!</h1>
</body>
</html>
```

### Rendering a Template
```python
from flask import render_template

@app.route('/')
def home():
    return render_template('index.html')
```

---

## 🔹 Static Files
Place static files in the `static/` directory.

### Using Static Files in Templates
```html
<link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='style.css') }}">
```

---

## 🔹 Forms & Request Handling
### Handling Form Data
```python
from flask import request

@app.route('/submit', methods=['POST'])
def submit():
    username = request.form['username']
    return f"Hello, {username}!"
```

### HTML Form
```html
<form action="/submit" method="post">
    <input type="text" name="username">
    <input type="submit">
</form>
```

---

## 🔹 Redirects & URL Handling
```python
from flask import redirect, url_for

@app.route('/admin')
def admin():
    return redirect(url_for('home'))
```

---

## 🔹 Flask with Database (SQLAlchemy)
### Install Flask SQLAlchemy
```sh
pip install flask-sqlalchemy
```

### Define a Model
```python
from flask_sqlalchemy import SQLAlchemy
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.db'
db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)
```

### Create the Database
```sh
python
>>> from app import db
>>> db.create_all()
```

---

## 🔹 Flask Sessions & Cookies
### Enable Sessions
```python
from flask import session
app.secret_key = 'supersecretkey'

@app.route('/login')
def login():
    session['user'] = 'John'
    return "User logged in!"

@app.route('/logout')
def logout():
    session.pop('user', None)
    return "User logged out!"
```

---

## 🔹 API with Flask (RESTful)
### Install Flask-RESTful
```sh
pip install flask-restful
```

### Create a REST API
```python
from flask_restful import Resource, Api
api = Api(app)

class HelloWorld(Resource):
    def get(self):
        return {'message': 'Hello, World!'}

api.add_resource(HelloWorld, '/')
```

---

## 🔹 Error Handling
```python
@app.errorhandler(404)
def page_not_found(e):
    return "Page not found", 404
```

---

## 🔹 Running Flask in Production
Use `gunicorn` to serve Flask apps:
```sh
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

---


