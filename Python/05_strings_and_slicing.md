# 05 Strings & Slicing

Work with text: indexing, slicing, copying substrings.

## Core Concepts
- Indexing starts at 0.
- Negative indices count from the end (`-1` is last char).
- Slice syntax: `s[start:stop]` (stop excluded) or `s[start:]` / `s[:stop]`.
- Full slice `s[:]` copies the string.

## Example Code (Ready to Run)
```python
course = "Python's for Beginners"
print(course[0])      # First character
print(course[-1])     # Last character
print(course[0:6])    # Substring (0..5)
print(course[1:])     # From index 1 to end
print(course[:5])     # From start to index 4

bike = "Cross bike"
clone = bike[:]       # Copy
print(clone)

name = "Jennifer"
print(name[1:-1])     # 'ennife'
```

## Multiline Strings
```python
email = '''Hi John,
This is our first email.
Regards,
Support Team'''
print(email)
```

## Explanation
- Strings are immutable (operations create new strings).
- Slicing never modifies the original.

## Exercises
1. Given `word = "Programming"`, print: first 3 chars, last 3 chars, middle section without first & last.
2. Reverse a string using slicing.

## Key Takeaways
- Slicing is powerful for extracting patterns.
- Immutability keeps original data safe from accidental changes.
