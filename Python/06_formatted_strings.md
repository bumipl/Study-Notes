# 06 Formatted Strings (f-Strings)

Readable string interpolation using curly braces with an `f` prefix.

## Core Concepts
- Prefix a string with `f` to embed expressions: `f"Hello {name}"`.
- Any valid Python expression can go inside `{}`.
- More concise and safer than manual concatenation.

## Example Code (Ready to Run)
```python
first = "Bartłomiej"
last = "Szala"
# Classic concatenation
message = first + '[' + last + '] is a coder'
print(message)

# f-string version
msg = f'{first} [{last}] is a coder'
print(msg)

# Expressions inside braces
length_info = f'First name has {len(first)} characters'
print(length_info)
```

## Formatting Numbers
```python
price = 1234.56789
print(f'Price: {price:.2f}')      # 2 decimals
print(f'Price: {price:,.2f}')     # Thousands separator
```

## Explanation
- `len(first)` executes before formatting.
- Cleaner than `'{} [{}] is a coder'.format(first, last)`.

## Exercises
1. Build `full_name` from `first` and `last` using an f-string.
2. Format a float with 3 decimals and a thousands separator.

## Key Takeaways
- f-Strings improve readability.
- Prefer f-strings over `+` concatenation for clarity.
