# 29 Keyword Arguments

Call functions using `name=value` pairs for clarity and order independence.

## Core Concepts
- Positional args depend on order.
- Keyword args specify which parameter each value belongs to.
- You can mix: positional first, then keyword.

## Example (Ready to Run)
```python
def greet_user(first_name, last_name):
    print(f'Hi there {first_name} {last_name}!')
    print('Welcome aboard\n')

def calc_cost(total, shipping, discount):
    print(f'Costs: total={total}, shipping={shipping}, discount={discount}')

print('Start')
greet_user(last_name='Smith', first_name='John')
greet_user(first_name='Katy', last_name='Perry')
calc_cost(total=50, shipping=5, discount=0.1)
print('Finish')
```

## Explanation
- Order no longer matters when all arguments are keyword style.
- Improves readability for functions with many parameters.

## Exercises
1. Add a `tax` parameter with default value; call with and without specifying.
2. Rewrite a previous positional call into keyword form.

## Key Takeaways
- Keyword args self-document calls.
- Use when there are many similar numeric arguments.
