# 🏗️ MVC & MVVM Comprehensive Cheatsheet

## 🔹 Introduction
**MVC (Model-View-Controller)** and **MVVM (Model-View-ViewModel)** are architectural patterns that **separate concerns** in software applications, improving maintainability and scalability.

---

## 🔹 MVC (Model-View-Controller)
### ✅ Components
| Component | Responsibility |
|-----------|---------------|
| **Model** | Handles data & business logic |
| **View** | UI representation of data |
| **Controller** | Handles user input & updates Model/View |

### 📌 MVC Workflow
1. **User interacts with the View** (UI layer).
2. **View sends input to the Controller**.
3. **Controller processes the input & updates the Model**.
4. **Model notifies the View of changes**.
5. **View updates the UI** accordingly.

### ✅ Example: Flask (Python) MVC
```python
# Model
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100))

# Controller
@app.route("/user/<id>")
def get_user(id):
    user = User.query.get(id)
    return render_template("user.html", user=user)

# View (user.html)
<h1>{{ user.name }}</h1>
```

---

## 🔹 MVVM (Model-View-ViewModel)
### ✅ Components
| Component | Responsibility |
|-----------|---------------|
| **Model** | Manages data and business logic |
| **View** | UI representation of data |
| **ViewModel** | Acts as an intermediary between View & Model |

### 📌 MVVM Workflow
1. **User interacts with the View**.
2. **View updates the ViewModel** (via data binding).
3. **ViewModel updates the Model**.
4. **Model notifies ViewModel of changes**.
5. **ViewModel updates the View automatically**.

### ✅ Example: Vue.js MVVM
```html
<!-- View -->
<div id="app">
  <p>{{ message }}</p>
  <button @click="updateMessage">Change Message</button>
</div>
```
```javascript
// ViewModel
new Vue({
  el: '#app',
  data: {
    message: 'Hello, MVVM!'
  },
  methods: {
    updateMessage() {
      this.message = 'Updated Message!';
    }
  }
});
```

---

## 🔹 MVC vs MVVM
| Feature  | MVC | MVVM |
|----------|-----|------|
| **Data Binding** | Manual updates | Automatic updates |
| **Complexity** | Moderate | Higher for large apps |
| **Best For** | Web applications | UI-driven applications |
| **Example Frameworks** | Django, Spring, Rails | Angular, Vue.js, WPF |

---

## 🔹 Best Practices
- **MVC** → Use when you need clear separation between data & UI.
- **MVVM** → Ideal for reactive UI frameworks (e.g., Vue, Angular).
- **Keep controllers lightweight** in MVC.
- **Use observables in MVVM** for automatic UI updates.
- **Follow SOLID principles** for better maintainability.

---