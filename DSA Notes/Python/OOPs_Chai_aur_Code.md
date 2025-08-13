
---

# 🐍 Python OOP — All Concepts in One Example

---

## 1️⃣ Basic Class and Object

A **class** is a blueprint for creating objects.  
An **object** is an instance of a class.

- `__init__` → Constructor method, called automatically when an object is created.
    
- `self` → Refers to the **instance itself** (used to access attributes/methods of the object).
    

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

my_car = Car('Toyota', 'Liva')
print(my_car.brand)  # Toyota
print(my_car.model)  # Liva
```

---

## 2️⃣ Class Method and `self`

Methods are functions defined inside a class.  
Use `self` to access instance variables inside methods.

```python
class Car:
    def __init__(self, brand, model):
        self.brand = brand
        self.model = model

    def full_name(self):
        return f"{self.brand} {self.model}"

my_car = Car('Toyota', 'Liva')
print(my_car.full_name())  # Toyota Liva
```

---

## 3️⃣ Inheritance

Inheritance allows one class (**child**) to reuse attributes/methods of another class (**parent**).

- `super()` → Calls the parent class’s method (e.g., `__init__`).
    

```python
class ElectricCar(Car):
    def __init__(self, brand, model, battery_size):
        super().__init__(brand, model)
        self.battery_size = battery_size
```

---

## 4️⃣ Encapsulation

Hiding internal details from outside access.

- Prefix with `__` → makes an attribute **private**.
    
- Use **getter** and **setter** to control access.
    

```python
class Car:
    def __init__(self, brand, model):
        self.__brand = brand
        self.__model = model

    def get_brand(self):
        return self.__brand

    def set_brand(self, new_brand):
        self.__brand = new_brand
```

---

## 5️⃣ Polymorphism

Same method name, different implementations.

```python
class Car:
    def fuel_type(self):
        return "Petrol or Diesel"

class ElectricCar(Car):
    def fuel_type(self):
        return "Electric Charge"
```

---

## 6️⃣ Class Variables

Belong to the **class**, shared by all instances.

```python
class Car:
    total_cars = 0

    def __init__(self, brand, model):
        Car.total_cars += 1

print(Car.total_cars)
```

---

## 7️⃣ Static Method

Belongs to the **class**, not the object.  
Does not use `self`.

```python
class Car:
    @staticmethod
    def general_description():
        return "Cars are means of transport but not very efficient in densely populated areas"

print(Car.general_description())
```

---

## 8️⃣ Property Decorator

Makes a method behave like an **attribute** (read-only if no setter is defined).

```python
class Car:
    def __init__(self, model):
        self.__model = model

    @property
    def model(self):
        return self.__model
```

---

## 9️⃣ `isinstance()` Function

Checks if an object is an instance of a class.

```python
print(isinstance(my_tesla, ElectricCar))  # True
print(isinstance(my_tesla, Car))          # True
```

---

## 🔟 Multiple Inheritance

A class can inherit from **multiple classes**.

```python
class Battery:
    def battery_info(self):
        return "This is a battery"

class Engine:
    def engine_info(self):
        return "This is an engine"

class ElectricCarTwo(Battery, Engine, Car):
    pass

my_new_tesla = ElectricCarTwo('Tesla', 'Model Y')
print(my_new_tesla.battery_info())  # This is a battery
print(my_new_tesla.engine_info())   # This is an engine
```

---

## 📌 Full Example

```python
class Car:
    total_car = 0
    
    def __init__(self, brand, model):
        self.__brand = brand
        self.__model = model
        Car.total_car += 1

    def get_brand(self):
        return self.__brand + " !"

    def full_name(self):
        return f'{self.__brand} {self.__model}'
    
    def fuel_type(self):
        return "Petrol or Diesel"
    
    @staticmethod
    def general_description():
        return "Cars are means of transport but not very efficient in densely populated areas"
    
    @property
    def model(self):
        return self.__model


class ElectricCar(Car):
    def __init__(self, brand, model, battery_size):
        super().__init__(brand, model)
        self.battery_size = battery_size

    def fuel_type(self):
        return "Electric Charge"


class Battery:
    def battery_info(self):
        return "This is battery"

class Engine:
    def engine_info(self):
        return "This is engine"

class ElectricCarTwo(Battery, Engine, Car):
    pass


# Multiple Inheritance Demo
my_new_tesla = ElectricCarTwo('Tesla', 'Model Y')
print(my_new_tesla.battery_info())
print(my_new_tesla.engine_info())

# Objects
my_tesla = ElectricCar('Tesla', 'Model S', '85 KWH')
my_car = Car('Toyota', 'Liva')
my_new_car = Car('Tata', 'Indica')

Car('Tata', 'Nixon')  # Temporary object, lost after this line

# Tests
print(my_new_car.full_name())
print(my_new_car.model)
print(isinstance(my_new_car, ElectricCar))
print(isinstance(my_tesla, ElectricCar))
print(isinstance(my_tesla, Car))
```

---

## 💡 Key Takeaways

- **Encapsulation** → Hide variables, control access.
    
- **Inheritance** → Reuse code, extend functionality.
    
- **Polymorphism** → Same method name, different behavior.
    
- **Class Variables** → Shared by all instances.
    
- **Static Methods** → Belong to the class, not the object.
    
- **Property Decorator** → Create read-only or computed attributes.
    
- **Multiple Inheritance** → Inherit from more than one class.
    
- **Garbage Collection** → If no variable holds the object, it can be destroyed. Such objects are only available in that line itself, after that it becomes eligible for garbage collector / collection.
    

---
