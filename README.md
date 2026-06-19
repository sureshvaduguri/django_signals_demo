# Django Signals Demo Project

## 📌 Project Title

**Django Signals Demonstration & Custom Python Class Implementation**

---

## 📖 Description

This project demonstrates the behavior of **Django Signals** with respect to:

1. Synchronous vs Asynchronous execution
2. Thread execution behavior
3. Database transaction handling

Additionally, it includes a **custom Python class (`Rectangle`)** that supports iteration as per the given requirements.

---

## 🛠️ Technologies Used

* Python 3.x
* Django
* SQLite (default database)

---

## 📂 Project Structure

```
django_signals_demo/
│── manage.py
│── django_signals_demo/
│   ├── settings.py
│   ├── urls.py
│   └── asgi.py
│
└── core/
    ├── models.py
    ├── views.py
    ├── signals.py
    ├── apps.py
    └── urls.py

rectangle.py
```

---

## ⚙️ Setup Instructions

1. Clone or extract the project:

```
cd django_signals_demo
```

2. Create virtual environment:

```
python -m venv venv
```

3. Activate environment:

* Windows:

```
venv\Scripts\activate
```

4. Install dependencies:

```
pip install django
```

5. Run migrations:

```
python manage.py migrate
```

6. Start server:

```
python manage.py runserver
```

---

## 🚀 API Endpoints

### 1. Test Signal Behavior

```
http://127.0.0.1:8000/test/
```

### 2. Test Transaction Behavior

```
http://127.0.0.1:8000/transaction/
```

---

## 🔍 Observations & Answers

### ✅ Question 1: Are Django Signals synchronous?

**Answer:** Yes, Django signals are synchronous by default.

**Proof:**
A delay (`time.sleep(3)`) inside the signal causes the view execution to wait, increasing response time.

---

### ✅ Question 2: Do signals run in the same thread?

**Answer:** Yes, signals run in the same thread.

**Proof:**
Thread IDs printed in both view and signal are identical.

---

### ✅ Question 3: Do signals run in the same database transaction?

**Answer:** Yes, signals run within the same transaction.

**Proof:**

* Signal detects object before commit
* If transaction rolls back, object is removed

---

## 🧩 Custom Python Class

### Rectangle Class

```python
class Rectangle:
    def __init__(self, length: int, width: int):
        self.length = length
        self.width = width

    def __iter__(self):
        yield {'length': self.length}
        yield {'width': self.width}
```

### ▶️ Example Usage

```
rect = Rectangle(10, 5)

for item in rect:
    print(item)
```

### ✅ Output

```
{'length': 10}
{'width': 5}
```

---

## 🎯 Key Learnings

* Django signals are synchronous by default
* Signals execute in the same thread
* Signals participate in the same database transaction
* Python iteration can be customized using `__iter__()`

---

## 📌 Notes

* This project is created for educational/demo purposes
* Minimal configuration is used for simplicity
* Console logs are essential to observe behavior

---

## 👨‍💻 Author

Chandrasuresh Reddy

---

## ✅ Submission Ready

This project is fully structured and meets all assignment requirements.
