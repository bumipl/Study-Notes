# 03 User Input

This lesson introduces interactive programs using `input()`.

## Core Concepts
- `input(prompt)` pauses execution and waits for user text.
- Always returns a `str`.
- Concatenate strings using `+` or use f-strings.

## Example Code (Ready to Run)
```python
name = input("What is your name? ")
color = input("What is your favourite color? ")
print(name + " likes " + color)
# Same with f-string:
print(f"{name} likes {color}")
```

## Explanation
- Two prompts collect information.
- The final line builds a sentence from two variables.

## Improving Robustness
```python
name = input("Name: ").strip().title()
color = input("Favourite color: ").strip().lower()
print(f"{name} likes the color {color}.")
```
- `.strip()` removes surrounding whitespace.
- `.title()` capitalizes each word.
- `.lower()` normalizes case.

## Exercises
1. Ask for first and last name separately and print full name.
2. Ask for a city and hobby, output a sentence.

## Key Takeaways
- All input is textual; convert when you need numbers.
- Clean / normalize user input for better consistency.
