# 14 Weight Converter (Conditional Logic + Input)

Convert between pounds (lbs) and kilograms (kg) with user choice.

## Core Concepts
- Normalize user input with `.lower()`.
- Branch logic for unit selection.
- Basic numeric conversion formulas.

## Example (Ready to Run)
```python
weight = input("Weight: ")
unit = input("(L)bs or (K)g: ").strip().lower()

if unit == "l":
    kg = float(weight) * 0.45359237
    print(f"Your weight in kg: {kg:.2f}")
elif unit == "k":
    lbs = float(weight) * 2.20462262185
    print(f"Your weight in lbs: {lbs:.2f}")
else:
    print("Invalid unit. Please enter L or K.")
```

## Explanation
- `strip()` cleans spaces; `lower()` standardizes comparison.
- Constants represent exact conversion factors.

## Improved Version with Validation
```python
raw_weight = input("Weight: ")
raw_unit = input("Unit (L/K): ").strip().lower()
try:
    w = float(raw_weight)
    if w <= 0:
        raise ValueError("Weight must be positive")
    if raw_unit == 'l':
        print(f"= {w * 0.45359237:.2f} kg")
    elif raw_unit == 'k':
        print(f"= {w * 2.20462262185:.2f} lbs")
    else:
        print("Unit must be L or K")
except ValueError as e:
    print("Error:", e)
```

## Exercises
1. Let user enter value like `72kg` or `160lbs` (parse automatically).
2. Add rounding option (ask user for number of decimals).

## Key Takeaways
- Normalize early to simplify branching.
- Validate numeric input to prevent crashes.
