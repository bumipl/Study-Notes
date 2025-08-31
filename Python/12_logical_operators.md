# 12 Logical Operators (and / or / not)

Combine Boolean expressions to form richer conditions.

## Operators
- `and` → True if both operands are True.
- `or`  → True if at least one operand is True.
- `not` → Inverts a Boolean value.

## Example (Ready to Run)
```python
has_high_income = True
has_good_credit = True

if has_high_income and has_good_credit:
    print("Eligible for loan (strong applicant)")

has_high_income2 = True
has_good_credit2 = False
if has_high_income2 or has_good_credit2:
    print("Eligible for loan (meets one condition)")

has_criminal_record = True
has_good_credit3 = True
if has_good_credit3 and not has_criminal_record:
    print("Eligible for loan")
else:
    print("Not eligible (background issue)")
```

## Truth Table Summary
| A | B | A and B | A or B |
|---|---|---------|--------|
| T | T | T       | T      |
| T | F | F       | T      |
| F | T | F       | T      |
| F | F | F       | F      |

## Short-Circuiting
- `and`: stops early if left side is False.
- `or`: stops early if left side is True.

## Exercises
1. Add condition: good credit AND (high income OR large savings).
2. Implement a rule: reject if `blacklisted_user`.

## Key Takeaways
- Combine logic to reduce nested `if` complexity.
- Short-circuiting can prevent unnecessary work.
