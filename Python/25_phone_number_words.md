# 25 Exercise – Phone Number to Words

Map digit characters to word equivalents using a dictionary.

## Example (Ready to Run)
```python
digits_mapping = {
    "1": "One",
    "2": "Two",
    "3": "Three",
    "4": "Four",
    "5": "Five",
    "6": "Six",
    "7": "Seven",
    "8": "Eight",
    "9": "Nine",
    "0": "Zero"
}

phone = input("Phone number: ")
output = []
for ch in phone:
    output.append(digits_mapping.get(ch, "!"))
print(' '.join(output))
```

## Explanation
- `.get(ch, "!")` returns `!` when character not in mapping.
- Collect into a list then `' '.join(...)` for efficient concatenation.

## Enhanced Version (Validation)
```python
if not phone.isdigit():
    print("Please enter digits only")
else:
    print(' '.join(digits_mapping[d] for d in phone))
```

## Exercises
1. Handle spaces and dashes (`-`) gracefully (skip them).
2. Add support for `+` at the beginning of international numbers.

## Key Takeaways
- Dictionaries excel at symbol-to-word translation tasks.
- Use joining on lists instead of repeated string `+=` for efficiency.
