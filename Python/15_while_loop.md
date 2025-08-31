# 15 While Loop (Basic Iteration)

Repeat a block while a condition remains True.

## Core Concepts
- `while condition:` keeps looping until condition becomes False.
- Update loop variables to avoid infinite loops.

## Example (Ready to Run)
```python
i = 1
while i <= 5:
    print('*' * i)
    i = i + 1
print("Done")
```

## Explanation
- Starts at 1, prints 1 to 5 stars.
- After 5, condition fails and loop exits.

## Infinite Loop Risk
If you forget to increment `i`, the loop never ends.

## Exercises
1. Count down from 10 to 1 then print "Launch!".
2. Ask for password until correct (limited attempts).

## Key Takeaways
- Always ensure loop progress.
- Use `while` for unknown iteration counts.
