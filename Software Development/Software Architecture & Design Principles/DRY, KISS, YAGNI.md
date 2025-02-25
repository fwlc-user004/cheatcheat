# 🛠️ DRY, KISS, YAGNI Comprehensive Cheatsheet

## 🔹 Introduction
These **three software engineering principles** help create **clean, efficient, and maintainable code**:
- **DRY (Don't Repeat Yourself)** → Avoid code duplication.
- **KISS (Keep It Simple, Stupid)** → Keep the design simple.
- **YAGNI (You Ain’t Gonna Need It)** → Only build what you need.

---

## 🔹 DRY (Don't Repeat Yourself)
**"Every piece of knowledge must have a single, unambiguous representation in a system."**

✅ **Example (Bad Practice - Code Duplication)**
```python
class User:
    def get_user_email(self):
        return self.email

def send_email(user):
    email = user.get_user_email()
    print(f"Sending email to {email}")
```

❌ **Fix (Encapsulate Reusable Logic)**
```python
class User:
    def get_email(self):
        return self.email

def send_email(user):
    print(f"Sending email to {user.get_email()}")
```

### ✅ DRY Best Practices
- **Refactor duplicate logic into functions or classes.**
- **Use loops instead of repeated code blocks.**
- **Apply design patterns like MVC to structure code.**

---

## 🔹 KISS (Keep It Simple, Stupid)
**"Simplicity improves code readability and maintainability."**

✅ **Example (Bad Practice - Overcomplicated Code)**
```python
if user.is_logged_in():
    if user.has_permission():
        if not user.is_suspended():
            access_granted = True
```

❌ **Fix (Simplified Logic)**
```python
access_granted = user.is_logged_in() and user.has_permission() and not user.is_suspended()
```

### ✅ KISS Best Practices
- **Avoid unnecessary complexity.**
- **Use clear and straightforward logic.**
- **Favor readability over clever tricks.**

---

## 🔹 YAGNI (You Ain’t Gonna Need It)
**"Don’t add functionality until it is necessary."**

✅ **Example (Bad Practice - Unnecessary Features)**
```python
class User:
    def get_email(self):
        return self.email
    
    def get_social_media_profiles(self):
        return []  # Not needed in the current project
```

❌ **Fix (Only Implement Required Features)**
```python
class User:
    def get_email(self):
        return self.email
```

### ✅ YAGNI Best Practices
- **Don’t build extra features "just in case".**
- **Add functionality only when there is a concrete need.**
- **Focus on delivering working software over excessive planning.**

---

## 🔹 Summary Table
| Principle | Definition | Best Practices |
|-----------|------------|----------------|
| **DRY**  | Avoid duplication | Refactor repetitive code, use functions/classes |
| **KISS** | Keep code simple | Avoid unnecessary complexity, favor readability |
| **YAGNI** | Don’t add unnecessary features | Implement only what is needed |

---

## 🔹 Best Practices for Applying DRY, KISS, and YAGNI
- **Write modular and reusable code.**
- **Avoid premature optimization.**
- **Refactor continuously to keep the codebase clean.**
- **Review code regularly to ensure adherence to these principles.**

---