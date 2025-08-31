# 36 Modules (Importing Code)

Organize code across multiple files.

## Core Concepts
- A module = any `.py` file.
- Import entire module or specific objects.
- Prevent name clashes and improve structure.

## Example (Ready to Run)
```python
import conventers            # whole module
from conventers import kg_to_lbs  # specific function

print(conventers.lbs_to_kg(100))
print(conventers.kg_to_lbs(70))
```

## Explanation
- First form: access via qualified name `module.function`.
- Second form: direct access to imported symbol.

## Exercise Variant
```python
from conventers import find_max
nums = [1, 3, 6, 2, 500, 22]
print(find_max(nums))
```

## Best Practices
- Avoid `from module import *` (pollutes namespace).
- Group imports: standard lib, third-party, local.

## Exercises
1. Create `math_extra.py` with a `triple(n)` function; import and use it.
2. Explore `dir(module)` to inspect attributes.

## Key Takeaways
- Modules keep code modular and maintainable.
- Explicit imports improve clarity.
