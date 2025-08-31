# 31 Exception Handling

Gracefully handle runtime errors using `try` / `except` blocks.

## Core Concepts
- Wrap risky code in `try`.
- Catch specific exceptions with `except SomeError:`.
- Order from most specific to most general.

## Example (Ready to Run)
```python
try:
    age = int(input('Age: '))
    income = 20000
    risk = income / age
    print('Age entered:', age)
except ZeroDivisionError:
    print('Age cannot be 0')
except ValueError:
    print('Invalid value (please enter a number)')
```

## Explanation
- `int()` may raise `ValueError` if input not numeric.
- Division by zero raises `ZeroDivisionError`.

## Adding `else` and `finally`
```python
try:
    age = int(input('Age: '))
except ValueError:
    print('Invalid age')
else:
    print('Converted successfully')
finally:
    print('Execution complete')
```

## Exercises
1. Ask for two numbers and divide; handle invalid input & zero divisor.
2. Log error messages to a list for later review.

## Key Takeaways
- Catch only exceptions you can handle meaningfully.
- Avoid blanket `except:` (it hides real issues).
