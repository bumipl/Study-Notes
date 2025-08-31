# 39 Pathlib & Directories

Interact with filesystem paths using `pathlib.Path`.

## Core Concepts
- `Path()` with no args = current directory.
- `Path('some_dir')` references relative path.
- `glob(pattern)` yields matching paths.

## Example (Ready to Run)
```python
from pathlib import Path

path = Path()
for file in path.glob('*.md'):
    print(file)
```

## Explanation
- Iterates all Markdown files in current directory.
- `exists()`, `mkdir()`, `rmdir()` available for path management.

## Additional Operations
```python
p = Path('ecommerce')
print('Exists?', p.exists())
```

## Exercises
1. List all `.py` files recursively: `path.glob('**/*.py')`.
2. Create a directory if missing: `Path('output').mkdir(exist_ok=True)`.

## Key Takeaways
- `pathlib` offers an object-oriented alternative to `os.path`.
- Globbing simplifies file pattern searches.
