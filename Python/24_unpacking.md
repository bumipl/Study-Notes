# 24 Unpacking (Tuple/List Destructuring)

Assign elements of an iterable to multiple variables in one statement.

## Core Concepts
- Left-hand variables count must match number of elements unless using `*`.
- Works with any iterable (tuples, lists, strings, etc.).

## Example (Ready to Run)
```python
coordinates = (1, 2, 3)
x, y, z = coordinates
print(y)  # 2
```

## With Lists
```python
values = [10, 20, 30]
a, b, c = values
```

## Extended Unpacking
```python
head, *middle, tail = [1, 2, 3, 4, 5]
print(head, middle, tail)  # 1 [2,3,4] 5
```

## Swapping Variables
```python
a, b = 5, 10
a, b = b, a
print(a, b)  # 10 5
```

## Exercises
1. Unpack first, second, and rest of a list of 6 numbers.
2. Swap two user inputs without a temporary variable.

## Key Takeaways
- Improves readability; reduces indexing noise.
- Use starred expressions for flexible-length captures.
