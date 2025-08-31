# 07 String Methods & Membership

Using built-in string methods to transform and query text.

## Core Concepts
- Functions tied to an object are called methods.
- Common methods: `.upper()`, `.lower()`, `.find()`, `.replace()`.
- Membership operator: `'sub' in text` returns `True/False`.

## Example Code (Ready to Run)
```python
course = 'Python for Beginners'
print(len(course))              # Length of the string
print(course.upper())           # New uppercase string
print(course.lower())           # New lowercase string
print(course.find('r'))         # Index of first 'r' (or -1 if not found)
print(course.replace('Beginners','Advanced'))
print('Python' in course)       # True (case-sensitive)
print('python' in course)       # False (different case)
```

## Additional Useful Methods
```python
s = '  hello WORLD  '
print(s.strip())     # Remove leading/trailing whitespace
print(s.title())     # Capitalize each word
print(s.startswith('  h'))
print(s.endswith('LD  '))
```

## Explanation
- Methods do not mutate the original string (strings are immutable).
- `.find()` returns index or `-1` (unlike JavaScript which returns -1 as well; Python raises no exception).
- `in` is ideal for quick containment checks.

## Exercises
1. Ask user for a sentence; print it in title case.
2. Count how many times the letter `e` appears.

## Key Takeaways
- Learn a few high-frequency methods; look up others as needed.
- Membership tests are clean and expressive.
