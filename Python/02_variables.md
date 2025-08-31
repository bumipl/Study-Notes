# 02 Variables & Basic Types

This lesson covers creating variables and storing different basic data types.

## Core Concepts
- A variable is a named reference to a value in memory.
- Python is dynamically typed (no need to declare types explicitly).
- Common primitive types: `str`, `int`, `float`, `bool`.

## Example Code (Ready to Run)
```python
full_name = "John Smith"   # string
age = 20                    # integer
is_new = True               # boolean

print(full_name)
print(age)
print(is_new)
print(type(full_name), type(age), type(is_new))
```

## Explanation
- `type(value)` returns the runtime type.
- Variable names should be descriptive and use snake_case.
- Booleans are capitalized: `True` / `False`.

## Common Mistakes
- Forgetting quotes around strings.
- Using `true` instead of `True` (case-sensitive).

## Exercises
1. Create a variable `height_cm = 183` and print it.
2. Create `is_student = False` and print `"Student?"` plus the value.

## Key Takeaways
- Variables make code reusable and easier to change.
- Python infers the type automatically.
