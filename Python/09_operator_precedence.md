# 09 Operator Precedence

Order of evaluation when multiple operators appear in one expression.

## Core Concepts
Default precedence (highest to lowest among shown here):
1. `**`
2. Unary `+ -` (not shown in example)
3. `* / // %`
4. `+ -`
5. Parentheses override everything.

## Example Code (Ready to Run)
```python
x = (10 + 3) * 2 ** 2
print(x)  # 52
```

## Step-by-Step Evaluation
1. Parentheses: `(10 + 3)` -> `13`.
2. Exponent: `2 ** 2` -> `4`.
3. Multiplication: `13 * 4` -> `52`.

## More Examples
```python
print(2 + 3 * 4)        # 14 (3*4 first)
print((2 + 3) * 4)      # 20
print(2 ** 3 ** 2)      # 512 (right-associative: 3**2=9; 2**9=512)
```

## Explanation
- Use parentheses liberally for readability.
- Exponentiation is right-associative.

## Exercises
1. Evaluate and then run: `5 + 2 * 3 ** 2`.
2. Rewrite an expression using parentheses to change its result.

## Key Takeaways
- Ambiguity slows understanding—add parentheses to clarify intent.
- Precedence bugs are subtle; clarity beats brevity.
