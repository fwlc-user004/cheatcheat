# 🔥 SOLID Principles Cheatsheet

## 🔹 Introduction
SOLID is a set of **five design principles** that improve **code maintainability, scalability, and readability** in object-oriented programming.

---

## 🔹 1. Single Responsibility Principle (SRP)
**"A class should have only one reason to change."**

✅ **Example (Bad Practice - Multiple Responsibilities)**
```python
class Report:
    def generate(self):
        return "Report Data"
    def save_to_file(self, filename):
        with open(filename, "w") as f:
            f.write(self.generate())
```
❌ **Fix (Separation of Concerns)**
```python
class Report:
    def generate(self):
        return "Report Data"

class FileSaver:
    def save_to_file(self, filename, data):
        with open(filename, "w") as f:
            f.write(data)
```

---

## 🔹 2. Open/Closed Principle (OCP)
**"Software entities should be open for extension but closed for modification."**

✅ **Example (Bad Practice - Modification Required for New Features)**
```python
class PaymentProcessor:
    def process_payment(self, type, amount):
        if type == "credit":
            self.process_credit(amount)
        elif type == "paypal":
            self.process_paypal(amount)
```
❌ **Fix (Using Polymorphism - Extend Without Modifying)**
```python
class PaymentProcessor:
    def process_payment(self, payment_method):
        payment_method.pay()

class CreditPayment:
    def pay(self):
        print("Processing Credit Card Payment")

class PayPalPayment:
    def pay(self):
        print("Processing PayPal Payment")
```

---

## 🔹 3. Liskov Substitution Principle (LSP)
**"Subtypes must be substitutable for their base types."**

✅ **Example (Bad Practice - Violating Substitution Rule)**
```python
class Bird:
    def fly(self):
        print("Flying")

class Penguin(Bird):
    def fly(self):
        raise Exception("Penguins can't fly!")
```
❌ **Fix (Separate Behaviors Properly)**
```python
class Bird:
    pass

class FlyingBird(Bird):
    def fly(self):
        print("Flying")

class Penguin(Bird):
    def swim(self):
        print("Swimming")
```

---

## 🔹 4. Interface Segregation Principle (ISP)
**"Clients should not be forced to depend on methods they do not use."**

✅ **Example (Bad Practice - Large Interfaces)**
```python
class Worker:
    def work(self): pass
    def eat(self): pass
```
❌ **Fix (Separate Interfaces)**
```python
class Workable:
    def work(self): pass

class Eatable:
    def eat(self): pass

class Human(Workable, Eatable):
    def work(self): print("Working")
    def eat(self): print("Eating")
```

---

## 🔹 5. Dependency Inversion Principle (DIP)
**"High-level modules should not depend on low-level modules. Both should depend on abstractions."**

✅ **Example (Bad Practice - Hard Dependency on Concrete Class)**
```python
class MySQLDatabase:
    def connect(self):
        print("Connecting to MySQL")

class Application:
    def __init__(self):
        self.db = MySQLDatabase()
```
❌ **Fix (Depend on Abstractions, Not Implementations)**
```python
class Database:
    def connect(self): pass

class MySQLDatabase(Database):
    def connect(self):
        print("Connecting to MySQL")

class Application:
    def __init__(self, db: Database):
        self.db = db
```

---

## 🔹 Best Practices
- **Apply SRP** to avoid classes doing too much.
- **Use OCP** to extend behavior without modifying core logic.
- **Ensure LSP compliance** by designing consistent subclasses.
- **Follow ISP** to prevent bloated interfaces.
- **Use DIP** to decouple high-level modules from low-level dependencies.

---