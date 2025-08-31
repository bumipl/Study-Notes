# 16 Guessing Game (While + Break + Else)

Implement limited-attempt guessing logic.

## Core Concepts
- Track attempts with a counter.
- `break` exits loop early.
- `while ... else` runs `else` only if loop wasn't broken.

## Example (Ready to Run)
```python
secret_number = 9
guess_count = 0
guess_limit = 3

while guess_count < guess_limit:
    guess = int(input('Guess: '))
    guess_count += 1
    if guess == secret_number:
        print('You won!')
        break
else:
    print("Sorry, you failed!")
```

## Explanation
- Loop ends either by `break` (win) or by exhausting attempts (triggers `else`).
- `else` on loops is unique to Python.

## Enhanced Version (Hints)
```python
secret = 9
for attempt in range(1, 4):
    g = int(input(f'Attempt {attempt}/3: '))
    if g == secret:
        print('Correct!')
        break
    elif g < secret:
        print('Too low')
    else:
        print('Too high')
else:
    print('Out of attempts.')
```

## Exercises
1. Add input validation (reject non-digits gracefully).
2. Randomize `secret_number` using `random.randint`.

## Key Takeaways
- Loop `else` is for the normal (non-broken) completion path.
- Counters + conditions = controlled repetition.
