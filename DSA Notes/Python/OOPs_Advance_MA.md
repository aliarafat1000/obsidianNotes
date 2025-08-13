
---

# ✨ Python Magic Methods in OOP

---

## 🔹 What Are Magic Methods?

- Also called **dunder methods** (double underscore).
    
- Special methods that **Python calls automatically** in certain situations.
    
- Example:
    
    - `__init__` → Called when an object is created.
        
    - `__str__` → Called when `print(object)` is used.
        

> **We don’t call them manually** — Python calls them in response to built-in operations.

---

## 📌 Common Magic Methods

|Method|Triggered By|Purpose|
|---|---|---|
|`__init__`|When creating an object|Constructor logic|
|`__str__`|`print(obj)` or `str(obj)`|String representation|
|`__add__`|`obj1 + obj2`|Addition logic|
|`__sub__`|`obj1 - obj2`|Subtraction logic|
|`__mul__`|`obj1 * obj2`|Multiplication logic|
|`__truediv__`|`obj1 / obj2`|Division logic|
|`__eq__`|`obj1 == obj2`|Equality check|
|`__gt__`|`obj1 > obj2`|Greater than check|

---

## 🔹 `__slots__` and Magic Methods

- `__slots__` defines **exactly which attributes** are allowed.
    
- Prevents creating a `__dict__` for dynamic attributes.
    
- Saves memory and **restricts adding new attributes**.
    
- For **private attributes**, use **mangled names**:  
    `'_ClassName__attr'` inside `__slots__`.
    
- **Inheritance Rule** → If child should also have slots, define `__slots__` in the child class.
    

---

## 🛠 Full Example

```python
class Car:
    total_car = 0
    __slots__ = ['_Car__brand', '_Car__model']  # Private attributes allowed

    def __init__(self, brand, model):
        self.__brand = brand
        self.__model = model
        Car.total_car += 1

    def full_name(self):
        return f'{self.__brand} {self.__model}'

    # Magic Methods
    def __str__(self):
        """String representation when print(obj) is used"""
        return f'Straight from magic method {self.__brand} {self.__model}'

    def __add__(self, other):
        """Custom behavior for + operator"""
        return Car(self.__brand + other.__brand,
                   self.__model + other.__model)

    def __mul__(self, other):
        """Custom behavior for * operator"""
        return Car(self.__brand * 2 + other.__brand * 2,
                   self.__model + other.__model)


class ElectricCar(Car):
    __slots__ = ['battery_size']  # Preserve slots restriction

    def __init__(self, brand, model, battery_size):
        super().__init__(brand, model)
        self.battery_size = battery_size

    def fuel_type(self):
        return "Electric Charge"


# Usage
my_tesla = ElectricCar('Tesla', 'Model Y', '85 KWH')
print(my_tesla)  # Calls __str__

my_car = Car('Tata', 'Harrier')

yo = my_tesla + my_car   # Calls __add__
print(yo.full_name())

yes = my_tesla * my_car  # Calls __mul__
print(yes.full_name())
```

---

## 💡 Key Takeaways

- **Magic methods** let you integrate objects with Python’s built-in operators and functions.
    
- `__slots__` optimizes memory and controls allowed attributes.
    
- Private attributes in `__slots__` require **name mangling**.
    
- To **inherit slots**, explicitly define them in child classes.
    
- You can redefine arithmetic and comparison operators to give objects custom behaviors.
    

---

