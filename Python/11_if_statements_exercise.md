# 11 If Statements – Exercise (House Down Payment)

Compute a down payment based on buyer credit quality.

## Problem
- House price is fixed.
- Good credit → lower percentage.
- Otherwise → higher percentage.

## Original Code (Adjusted & Ready)
```python
house_price = 1_000_560
buyers_good_credit = True  # toggle

if buyers_good_credit:
    down_payment = house_price * 0.10  # 10%
else:
    down_payment = house_price * 0.20  # 20%

print(f"Down payment: ${down_payment:,.2f}")
```

## Improvements
- Use underscores in numeric literals for readability.
- Format currency with thousands separators and 2 decimals.

## Extended Version
```python
house_price = 1_000_560
buyers_good_credit = True
has_high_income = False

base_rate = 0.20
if buyers_good_credit and has_high_income:
    rate = 0.08
elif buyers_good_credit:
    rate = 0.10
elif has_high_income:
    rate = 0.15
else:
    rate = base_rate

down_payment = house_price * rate
print(f"Rate: {rate*100:.1f}% | Down payment: ${down_payment:,.2f}")
```

## Exercises
1. Add a variable `first_time_buyer` that reduces rate by 1 percentage point.
2. Add validation: ensure `house_price > 0`.

## Key Takeaways
- Combine multiple Booleans with `and`/`or` to refine decisions.
- Keep rates in variables for easier adjustments.
