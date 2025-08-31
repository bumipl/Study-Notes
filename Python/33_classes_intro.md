# 33 Classes (Intro to OOP)

Define new types bundling data (attributes) and behavior (methods).

## Core Concepts
- Class is a blueprint; objects are instances.
- Methods defined with `def` inside class; take `self` as first parameter.
- Attributes can be added dynamically but better set within methods/constructor.

## Example (Ready to Run)
```python
class Point:
    def move(self):
        print('move')
    def draw(self):
        print('draw')

point1 = Point()
point1.x = 10
point1.y = 20
print(point1.x)
point1.draw()

point2 = Point()
point2.x = 1
print(point2.x)
```

## Explanation
- `Point()` calls the class to create a new instance.
- `self` refers to the current instance inside methods.

## Exercises
1. Add method `describe()` that prints x/y if they exist using `hasattr`.
2. Create a second class `Circle` with a `radius` attribute.

## Key Takeaways
- Organize related data/behavior.
- Avoid attaching attributes outside methods when possible.
