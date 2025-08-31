# 10 Math Functions & `math` Module

Use built-in helpers and the standard `math` library.

## Core Concepts
- Built-ins: `round()`, `abs()`.
- `math` module adds many functions (floor, ceil, sqrt, etc.).
- Import with `import math`.

## Example Code (Ready to Run)
```python
import math

print(math.floor(2.9))  # 2
x = 2.9
print(round(x))         # 3 (nearest int)
print(abs(-2.9))        # 2.9 (absolute value)
```

## Additional Useful Functions
```python
import math
print(math.ceil(2.1))   # 3
print(math.sqrt(16))    # 4.0
print(math.factorial(5))# 120
```

## Explanation
- `round()` uses bankers rounding for .5 (to nearest even).
- `abs()` always returns a non-negative number.
- `math.floor()` always goes down; `math.ceil()` always goes up.

## Exercises
1. Ask user for a float and show floor, ceil, and rounded value.
2. Compute hypotenuse: given `a` and `b`, use `math.sqrt(a*a + b*b)`.

## Key Takeaways
- Use the standard library—don’t reimplement basics.
- Import only what you need for clarity: `from math import sqrt` (optional style).
