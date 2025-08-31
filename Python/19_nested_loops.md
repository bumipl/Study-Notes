# 19 Nested Loops & Pattern Generation

Loops inside loops to traverse multi-level structures or build patterns.

## Core Concepts
- Each inner loop runs fully for every iteration of the outer loop.
- Runtime grows multiplicatively (be mindful of performance).

## Coordinate Example
```python
for x in range(4):
    for y in range(3):
        for z in range(2):
            print(f"({x}, {y}, {z})")
```

## Pattern Builder (Ready to Run)
```python
numbers = [2, 2, 2, 2, 5]
for x_count in numbers:
    output = ''
    for _ in range(x_count):
        output += 'x'
    print(output)
```

## Explanation
- For each number, we build a string of that many 'x'.
- Inner accumulation builds a line; printed after inner loop ends.

## More Pythonic Version
```python
numbers = [2, 2, 2, 2, 5]
for n in numbers:
    print('x' * n)
```

## Exercises
1. Given `[1,3,1,3,5]` draw a symmetrical pattern.
2. Build a multiplication table (1–5 × 1–5).

## Key Takeaways
- Nested loops useful for grids, matrices, tables.
- Often can be simplified with string multiplication or list comprehensions.
