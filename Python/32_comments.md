# 32 Comments

Annotate code for clarity without affecting execution.

## Core Concepts
- Single-line comment: starts with `#`.
- Keep comments concise and relevant.
- Explain "why", not obvious "what".

## Example (Ready to Run)
```python
# This prints a greeting message
print("Hello World")
```

## Bad vs Good
```python
# BAD: increment i
# i = i + 1

# GOOD: Advance index to avoid infinite loop
# i += 1
```

## Docstrings
Use triple quotes inside functions/classes for documentation.
```python
def add(a, b):
    """Return the sum of a and b."""
    return a + b
```

## Exercises
1. Add a docstring to a function you wrote earlier.
2. Remove any redundant comments from code.

## Key Takeaways
- Comments should age well; avoid repeating the code literally.
- Prefer expressive names over excessive comments.
