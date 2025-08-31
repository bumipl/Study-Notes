# 11 If Statements (Basic Conditions)

Control flow with `if`, `elif`, and `else`.

## Core Concepts
- `if` evaluates a Boolean expression.
- First matching branch executes; remaining branches are skipped.
- Indentation defines blocks (4 spaces is standard).

## Example (Ready to Run)
```python
is_hot = False  # try True
is_cold = False # try True

if is_hot:
    print("It's a hot day")
    print("Drink plenty of water!")
elif is_cold:
    print("It's a cold day")
    print("Wear warm clothes!")
else:
    print("It's a lovely day")

print("Enjoy your day")
```

## Explanation
- Only one of the branches runs (mutually exclusive chain).
- The final `print` runs regardless of condition results.

## Tips
- Keep conditions simple; extract complex logic into descriptive variables.

## Exercises
1. Ask the user for temperature and print a message (>30 hot, <10 cold, otherwise moderate).
2. Add humidity logic (e.g., high humidity modifies the message).

## Key Takeaways
- Order matters; the first true branch wins.
- Use `elif` instead of nested `if` for mutually exclusive tests.
