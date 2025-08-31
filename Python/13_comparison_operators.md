# 13 Comparison Operators & Validation

Check relationships between values and validate user input length.

## Operators
- `<`, `<=`, `>`, `>=`, `==`, `!=`.
- Return Boolean results.

## Username Length Validator (Ready to Run)
```python
name = input("Username: ")

if len(name) < 3:
    print("Username is too short (min 3 characters)")
elif len(name) > 50:
    print("Username is too long (max 50 characters)")
else:
    print("Name looks good ✅")
```

## Temperature Example
```python
temperature = 8
if temperature >= 30:
    print("It's a hot day")
elif temperature < 10:
    print("It's a cold day")
else:
    print("It's neither hot nor cold")
```

## Explanation
- `len()` returns number of characters.
- Condition order matters—shortest / longest boundaries must be explicit.

## Exercises
1. Validate password length (8–64 characters).
2. Compare two input numbers and print the larger.

## Key Takeaways
- Use comparison operators to enforce constraints.
- Always give users clear feedback for invalid input.
