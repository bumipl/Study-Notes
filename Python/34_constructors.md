# 34 Constructors (`__init__` Method)

Initialize object state at creation time.

## Core Concepts
- `__init__` runs automatically when a new instance is created.
- Set required attributes inside `__init__`.
- `self` is the new object being initialized.

## Point Example (Ready to Run)
```python
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def draw(self):
        print(f'Point at ({self.x}, {self.y})')

p = Point(10, 20)
p.x = 11  # mutation
print(p.x)
```

## Person Exercise (Ready to Run)
```python
class Person:
    def __init__(self, name):
        self.name = name
    def talk(self):
        print(f'Hi, I am {self.name}')

john = Person('John Smith')
john.talk()

bob = Person('Bob Taylor')
bob.talk()
```

## Explanation
- Required data enforced by constructor parameters.
- Provides safer, predictable initialization.

## Exercises
1. Add validation: raise `ValueError` if name is empty.
2. Add method `rename(new_name)` updating attribute.

## Key Takeaways
- Use constructors to guarantee object completeness.
- Keep initialization lightweight.
