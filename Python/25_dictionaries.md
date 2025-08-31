# 25 Dictionaries (Key-Value Mapping)

Store associations between unique keys and values.

## Core Concepts
- Defined with `{}` using `key: value` pairs.
- Keys must be hashable (e.g., str, int, tuple); values can be any type.
- Access via `dict[key]` (raises if missing) or `dict.get(key, default)`.

## Example (Ready to Run)
```python
customer = {
    "name": "John Smith",
    "age": 22,
    "is_verified": True
}

print(customer["name"])           # Direct access
print(customer.get("birthdate"))  # None (missing)
print(customer.get("birthdate", "Jan 1, 1980"))  # default value

customer["birthdate"] = "Jun 5, 2002"  # add new key
customer["name"] = "Jack Smith"        # update existing key
print(customer["name"], customer["birthdate"], customer["age"])
```

## Key Methods
- `keys()`, `values()`, `items()` for iteration.
- `in` tests key existence.
- `pop(key)`, `popitem()`, `update({...})`.

## Iteration
```python
for key, value in customer.items():
    print(key, '=>', value)
```

## Exercises
1. Build a dictionary mapping country codes to names; query by user input.
2. Count character frequency in a string.

## Key Takeaways
- Choose dicts for fast lookups by meaningful keys.
- Prefer `.get()` when a missing key is acceptable.
