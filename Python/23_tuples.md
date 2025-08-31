# 23 Tuples (Immutable Sequences)

Like lists but immutable: cannot add, remove, or change elements.

## Core Concepts
- Defined with parentheses: `(1, 2, 3)`.
- Support indexing, iteration, `count()`, `index()`.
- More memory-efficient & hashable (usable as dict keys) if elements are hashable.

## Example (Ready to Run)
```python
numbers = (1, 2, 3)
print(numbers.count(1))  # occurrences of 1
print(numbers.index(2))  # position of value 2
print(numbers[2])        # third element
```

## Why Use Tuples?
- Guarantee data integrity (cannot be modified accidentally).
- Often used for fixed-size records (e.g., coordinates).

## Single-Element Tuple
```python
single = (42,)  # note trailing comma
```

## Exercises
1. Create tuple of 3 colors; loop & print them.
2. Attempt modification and observe the exception.

## Key Takeaways
- Use tuples when structure & size should not change.
- Slight performance gain in some use cases versus list.
