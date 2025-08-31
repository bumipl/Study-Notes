# 35 Inheritance

Create subclasses that reuse and extend behavior of a base class.

## Core Concepts
- Child class lists parent in parentheses: `class Dog(Mammal):`.
- Inherits methods/attributes of parent unless overridden.
- Promotes code reuse and hierarchical modeling.

## Example (Ready to Run)
```python
class Mammal:
    def walk(self):
        print('walk')

class Dog(Mammal):
    def bark(self):
        print('bark bark bark')

class Cat(Mammal):
    def meow(self):
        print('meow meow meow')

dog1 = Dog()
cat1 = Cat()

dog1.walk()
dog1.bark()
cat1.meow()
```

## Explanation
- `Dog` and `Cat` inherit `walk()` from `Mammal`.
- Each subclass adds species-specific behavior.

## Extending with Constructor
```python
class Animal:
    def __init__(self, species):
        self.species = species

class Dog(Animal):
    def __init__(self, name):
        super().__init__('Canis familiaris')
        self.name = name
```

## Exercises
1. Add `Bird` subclass with `fly()`.
2. Override a method to add extra logging.

## Key Takeaways
- Use inheritance for "is-a" relationships.
- Favor composition over deep inheritance trees.
