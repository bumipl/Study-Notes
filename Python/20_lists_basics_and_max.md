# 20 Lists (Basics & Finding Max)

Dynamic ordered collection of items.

## Core Concepts
- Lists are mutable: you can add, remove, or change items.
- Indexing starts at 0.
- Iterate to compute aggregates (e.g., max, sum).

## Example: Modify & Print
```python
names = ["John", "Mosh", "Bartek", "Sarah", "Martha"]
names[0] = "Jonathan"
print(names)
```

## Find Largest Number (Ready to Run)
```python
numbers = [3, 6, 2, 99, 8, 4, 101, 10]
largest = numbers[0]
for n in numbers:
    if n > largest:
        largest = n
print("Largest:", largest)
```

## Pythonic Alternatives
```python
print(max(numbers))
print(sorted(numbers)[-1])
```

## Explanation
- Initialize `largest` with first element to avoid magic values.
- Compare each item; update when finding a larger one.

## Exercises
1. Write manual `min` finder.
2. Compute both min and max in one pass.

## Key Takeaways
- Manual scans teach logic behind built-ins.
- Use built-ins (`max`, `min`) in production for clarity.
