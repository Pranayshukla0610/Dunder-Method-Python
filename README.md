# Dunder-Method-Python
# 🐍 Python Dunder Methods (Magic Methods) – Complete Guide

## 📌 Introduction

Dunder methods (short for **Double UNDERscore methods**) are special methods in Python that start and end with double underscores:

```python
__init__, __str__, __add__, __len__
```

👉 These methods allow you to **define how objects behave** with built-in operations like:

* `+` (addition)
* `len()`
* `print()`
* `==` (comparison)

---

## 🚀 Why Dunder Methods?

Without dunder methods:

* Objects behave like plain memory references

With dunder methods:

* You can make objects behave like **numbers, strings, lists, etc.**

👉 Example:

```python
a + b
```

Internally becomes:

```python
a.__add__(b)
```

---

## 🧠 Key Concept

> Dunder methods = Operator overloading + Custom behavior

---

# 🔹 1. Object Initialization

## ✅ `__init__`

Used to initialize an object

```python
class Person:
    def __init__(self, name):
        self.name = name

p = Person("Pranay")
```

---

## ✅ `__new__` (Advanced)

* Called **before `__init__`**
* Used for object creation

```python
class Demo:
    def __new__(cls):
        print("Creating instance")
        return super().__new__(cls)
```

---

# 🔹 2. String Representation

## ✅ `__str__`

User-friendly output

```python
class Person:
    def __str__(self):
        return "This is a Person"

print(Person())
```

---

## ✅ `__repr__`

Developer-friendly output

```python
class Person:
    def __repr__(self):
        return "Person()"
```

---

# 🔹 3. Arithmetic Operators

## ✅ `__add__` (+)

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __add__(self, other):
        return Number(self.value + other.value)

a = Number(5)
b = Number(10)
print((a + b).value)  # 15
```

---

## Other Arithmetic Methods

| Operator | Method         |
| -------- | -------------- |
| `-`      | `__sub__`      |
| `*`      | `__mul__`      |
| `/`      | `__truediv__`  |
| `//`     | `__floordiv__` |
| `%`      | `__mod__`      |
| `**`     | `__pow__`      |

---

# 🔹 4. Comparison Operators

```python
class Number:
    def __init__(self, value):
        self.value = value

    def __eq__(self, other):
        return self.value == other.value
```

| Operator | Method   |
| -------- | -------- |
| `==`     | `__eq__` |
| `!=`     | `__ne__` |
| `<`      | `__lt__` |
| `>`      | `__gt__` |
| `<=`     | `__le__` |
| `>=`     | `__ge__` |

---

# 🔹 5. Length and Indexing

## ✅ `__len__`

```python
class MyList:
    def __init__(self, data):
        self.data = data

    def __len__(self):
        return len(self.data)

print(len(MyList([1,2,3])))  # 3
```

---

## ✅ `__getitem__`

```python
class MyList:
    def __init__(self, data):
        self.data = data

    def __getitem__(self, index):
        return self.data[index]

obj = MyList([10,20,30])
print(obj[1])  # 20
```

---

# 🔹 6. Iteration

## ✅ `__iter__` and `__next__`

```python
class Counter:
    def __init__(self, max):
        self.max = max
        self.current = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.max:
            self.current += 1
            return self.current
        else:
            raise StopIteration

for i in Counter(3):
    print(i)
```

---

# 🔹 7. Boolean and Call Behavior

## ✅ `__bool__`

```python
class Test:
    def __bool__(self):
        return False

print(bool(Test()))  # False
```

---

## ✅ `__call__`

Makes object behave like a function

```python
class Hello:
    def __call__(self):
        print("Called!")

h = Hello()
h()  # Called!
```

---

# 🔹 8. Context Manager

## ✅ `__enter__` and `__exit__`

```python
class FileManager:
    def __enter__(self):
        print("Start")
        return self

    def __exit__(self, exc_type, exc_value, traceback):
        print("End")

with FileManager():
    print("Inside")
```

---

# 🔹 9. Inheritance & `super()`

## ✅ Why `super()`?

```python
class A:
    def __init__(self):
        print("A")
        super().__init__()

class B:
    def __init__(self):
        print("B")
        super().__init__()

class C(A, B):
    def __init__(self):
        print("C")
        super().__init__()

c = C()
```

### Output:

```
C
A
B
```

👉 `super()` ensures:

* All parent classes run
* Follows **MRO (Method Resolution Order)**

---

# 🔥 Common Mistakes

❌ Not using `super()` in multiple inheritance
❌ Forgetting `self`
❌ Returning wrong type in `__add__`
❌ Confusing `__str__` vs `__repr__`

---

# 🧪 Practice Questions

1. Create a class that overloads `+` to add two vectors
2. Implement custom `len()` for a class
3. Create an object that behaves like a function using `__call__`
4. Build your own iterator class
5. Override `==` to compare objects

---

# 🏁 Conclusion

Dunder methods are the **backbone of Python OOP magic** ✨

👉 They allow:

* Operator overloading
* Custom object behavior
* Cleaner, more Pythonic code

---

## ⭐ If you found this helpful:

Give this repo a star and start building your own custom Python objects!

---
