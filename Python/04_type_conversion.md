# 04 Type Conversion

Convert strings (from input) into numeric types for calculations.

## Core Concepts
- User input: always a string.
- `int()`, `float()`, `bool()`, `str()` are constructors that convert types.
- Invalid conversions raise `ValueError`.

## Example A: Age Calculator
```python
birth_year = input('Birth year: ')
print('Raw type of birth_year:', type(birth_year))

age = 2024 - int(birth_year)
print('Computed age:', age)
print('Type of age:', type(age))
```

## Example B: Pounds to Kilograms
```python
pounds = input("What is your weight in pounds? ")
weight_in_kg = float(pounds) / 2.2046
print(f"Your weight in kg is: {weight_in_kg:.2f}")
```

## Defensive Version (Error Handling)
```python
raw = input("Weight in pounds: ")
try:
    pounds = float(raw)
    kg = pounds / 2.2046
    print(f"= {kg:.2f} kg")
except ValueError:
    print("Please enter a numeric value.")
```

## Explanation
- `int('10') -> 10`, `float('3.14') -> 3.14`.
- Formatting with `:.2f` limits output to 2 decimals.

## Exercises
1. Convert Celsius to Fahrenheit.
2. Ask for minutes and convert to seconds.

## Key Takeaways
- Always validate before converting user input in real programs.
- Use formatted strings for clean numeric output.
