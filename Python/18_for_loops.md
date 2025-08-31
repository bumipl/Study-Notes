# 18 For Loops & Ranges

Iterate over sequences or numeric ranges.

## Core Concepts
- `for item in iterable:` loops through each element.
- `range(start, stop, step)` generates a sequence of integers (stop excluded).

## Example A (Ready to Run)
```python
for item in range(1, 10, 2):  # 1,3,5,7,9
    print(item)
```

## Summing a List (Exercise Code)
```python
prices = [10, 20, 30]
final_price = 0
for price in prices:
    final_price += price
print(f"Total: {final_price}")
```

## Explanation
- Accumulator pattern: initialize, loop, update, use result.

## Common Patterns
```python
# Enumerating with index
tools = ['hammer', 'saw', 'drill']
for index, tool in enumerate(tools):
    print(index, tool)
```

## Exercises
1. Multiply all numbers in a list; print the product.
2. Print a half-pyramid of `#` with height 5.

## Key Takeaways
- Use `for` with known collections or generated ranges.
- Prefer `enumerate()` over manual index counters.
