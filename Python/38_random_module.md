# 38 Random Module (Generating Pseudorandom Values)

Produce random numbers, choices, and simulate dice.

## Core Concepts
- `random.random()` → float in [0.0, 1.0).
- `random.randint(a, b)` → integer inclusive.
- `random.choice(seq)` → random element from sequence.

## Basic Examples (Ready to Run)
```python
import random

print(random.random())          # float
print(random.randint(10, 20))    # int between 10 and 20
members = ['John', 'Mary', 'Bob', 'Mosh']
print(random.choice(members))
```

## Dice Class (Ready to Run)
```python
import random

class Dice:
    def roll(self):
        first = random.randint(1, 6)
        second = random.randint(1, 6)
        return first, second

dice = Dice()
print("Dice game generated values are:")
print(dice.roll())
```

## Explanation
- Using a class encapsulates roll logic.
- Returning a tuple supports unpacking: `a, b = dice.roll()`.

## Exercises
1. Simulate rolling until you get doubles.
2. Generate a random password from letters and digits.

## Key Takeaways
- Pseudorandomness is deterministic given a seed.
- Use `secrets` module for cryptographic randomness.
