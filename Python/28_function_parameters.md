# 28 Function Parameters

Pass data into functions via parameters.

## Core Concepts
- Parameters defined in function signature.
- Arguments supplied in call (positional by default).

## Example (Ready to Run)
```python
def greet_user(first_name, last_name):
    print(f'Hi there {first_name} {last_name}!')
    print('Welcome aboard')
    print('We wish you a good trip!')

print('Start')
greet_user('Bartłomiej', 'Szala')
greet_user('Weronika', 'Dąbrowska')
print('Finish')
```

## Explanation
- Each call substitutes argument values into the function body.
- Parameters behave like local variables inside the function.

## Exercises
1. Add a `greeting` parameter with default value.
2. Create `full_name(first, last)` returning a formatted name.

## Key Takeaways
- Parameterization increases flexibility.
- Use descriptive parameter names.
