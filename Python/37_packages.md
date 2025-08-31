# 37 Packages (Directory Namespaces)

Group related modules in a directory with an `__init__.py` file.

## Core Concepts
- Package = folder containing `__init__.py`.
- Import using dotted paths: `package.module`.
- Organizes larger codebases into logical sections.

## Example (Ready to Run)
```python
from ecommerce import shipping
shipping.calc_shipping()
```

## Alternative Forms
```python
# import ecommerce.shipping
# ecommerce.shipping.calc_shipping()

# from ecommerce.shipping import calc_shipping
# calc_shipping()
```

## Explanation
- Importing the package runs `ecommerce/__init__.py` (if present).
- Access functions through module namespace.

## Exercises
1. Add another module `tax.py` and define `calc_tax(amount)`.
2. Import it alongside `shipping` and call both.

## Key Takeaways
- Packages scale module organization.
- Use clear directory names for discoverability.
