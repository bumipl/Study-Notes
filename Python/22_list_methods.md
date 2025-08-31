# 22 List Methods (Mutating Operations)

Modify, query, and duplicate lists using built-in methods.

## Core Methods Demonstrated
- `append(x)` – add at end.
- `insert(i, x)` – insert at index.
- `remove(x)` – remove first occurrence.
- `pop()` – remove & return last element.
- `index(x)` – position of first occurrence (raises if absent).
- `in` – membership test → Boolean.
- `count(x)` – number of occurrences.
- `sort()` – in-place ascending sort.
- `reverse()` – reverse in place.
- `copy()` – shallow copy.
- `clear()` – remove all elements.

## Example (Ready to Run)
```python
numbers = [5, 2, 1, 7, 4]
numbers.append(20)
numbers.insert(0, 10)
numbers.remove(5)
numbers.pop()
print('Index of 10:', numbers.index(10))
print('Contains 50?', 50 in numbers)
print('Count of 2:', numbers.count(2))
numbers.sort()
print('Ascending:', numbers)
numbers.sort(); numbers.reverse()
print('Descending:', numbers)
nums_copy = numbers.copy()
numbers.append(55)
print('Original copy remains:', nums_copy)
numbers.clear()
print('Cleared list:', numbers)
```

## Safe Lookups
```python
if 7 in numbers:
    print(numbers.index(7))
```

## Exercises
1. Create a list of words; sort case-insensitively.
2. Copy a list, modify original, show independence.

## Key Takeaways
- Many list methods mutate in place and return `None`.
- Use `sorted(list)` for a non-mutating sort.
