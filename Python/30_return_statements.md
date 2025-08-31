# 30 Return Statements

Produce a value from a function using `return`.

## Core Concepts
- `return value` exits function immediately.
- Functions without `return` implicitly return `None`.
- Can return any object (number, string, tuple, etc.).

## Example (Ready to Run)
```python
def square(number):
    return number * number

def power(base, exponent):
    return base ** exponent

print(square(3))
print(power(4, 4))
```

## Emoji Converter (Example with Return)
```python
def emoji_converter(message):
    words = message.split(' ')
    emojis = {":)": "😀", ":(": "😔", ":p": "😜", "XD": "😁"}
    output = []
    for word in words:
        output.append(emojis.get(word, word))
    return ' '.join(output)

msg = input('> ')
print(emoji_converter(msg))
```

## Explanation
- Returning allows caller to decide how to use the result.
- Avoid printing inside functions when you need testable logic.

## Exercises
1. Write `bmi(weight_kg, height_m)` returning BMI value.
2. Write function that returns both min and max of a list as a tuple.

## Key Takeaways
- Returning separates computation from presentation.
- Enables composition: outputs feed other functions.
