# 22 Exercise – Remove Duplicates

Build a new list containing only unique elements while preserving order.

## Problem
Given a list with duplicates, produce a list of unique values in first-seen order.

## Example (Ready to Run)
```python
numbers = [5, 2, 1, 7, 4, 2, 3, 3, 55, 44, 44]
uniqs = []
for n in numbers:
    if n not in uniqs:
        uniqs.append(n)
print(uniqs)
```

## Explanation
- Membership test `n not in uniqs` ensures only first encounter is added.
- Order preserved because we append in traversal order.

## Alternatives
```python
# Using dict.fromkeys (preserves order since Python 3.7+)
unique_list = list(dict.fromkeys(numbers))

# Using set (order NOT guaranteed prior to Python 3.7, and loses original order):
unique_unordered = list(set(numbers))
```

## Extended Version (Function)
```python
def unique(sequence):
    seen = set()
    out = []
    for item in sequence:
        if item not in seen:
            seen.add(item)
            out.append(item)
    return out
```

## Exercises
1. Modify to count duplicates removed.
2. Accept list of strings case-insensitively (treat 'A' and 'a' same).

## Key Takeaways
- `set` is fast for membership but plain list keeps order logic simple.
- Know when order matters before choosing data structure.
