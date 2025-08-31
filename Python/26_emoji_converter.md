# 26 Emoji Converter (Dictionary Lookup)

Transform short text emoticons into Unicode emojis.

## Core Concepts
- Split input into tokens (words) using `.split(' ')`.
- Replace tokens via dictionary `.get(key, fallback)`.
- Reassemble output with spaces.

## Example (Ready to Run)
```python
emojis = {":)": "😀", ":(": "😔"}
message = input("> ")
words = message.split(' ')
output = []
for word in words:
    output.append(emojis.get(word, word))
print(' '.join(output))
```

## Function Version
```python
def convert_emojis(text):
    mapping = {":)": "😀", ":(": "😔", ":p": "😜", "XD": "😁"}
    return ' '.join(mapping.get(token, token) for token in text.split())

user = input('> ')
print(convert_emojis(user))
```

## Explanation
- Using a function encapsulates logic for reuse.
- `text.split()` without argument splits on any whitespace.

## Exercises
1. Add more emojis like `;)`, `:D`.
2. Make conversion case-insensitive for `xd` vs `XD`.

## Key Takeaways
- Dictionaries are powerful for symbolic replacement.
- Functional extraction improves testability.
