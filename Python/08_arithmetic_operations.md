# 08 Arithmetic Operations

Perform mathematical calculations with Python operators.

## Core Concepts
- Basic operators: `+`, `-`, `*`, `/`, `//`, `%`, `**`.
- `/` always returns `float`.
- `//` integer (floor) division.
- `%` gives the remainder.
- `**` exponentiation.

## Example Code (Ready to Run)
```python
print(10 + 3)   # 13
print(10 / 3)   # 3.333...
print(10 * 3)   # 30
print(10 // 3)  # 3 (floor division)
print(10 % 3)   # 1 (remainder)
print(10 ** 3)  # 1000 (power)

x = 10
x = x + 3
print(x)        # 13

b = 7
b -= 3          # Same as b = b - 3
print(b)        # 4
```

## Compound Assignment
- `+=`, `-=`, `*=`, `/=`, `//=`, `%=` combine update + operator.

## Explanation
- Floor division `//` truncates toward negative infinity for negatives.
- `%` is useful for cycle-based logic (even/odd: `n % 2 == 0`).

## Exercises
1. Compute area of a circle with radius input by user.
2. Convert minutes to hours + remaining minutes using `//` & `%`.

## Key Takeaways
- Choose operator based on required result (int vs float).
- Modulo helps with periodic logic and validation tasks.
