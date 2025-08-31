# 40 pip & PyPI (Package Management)

Install and manage third-party libraries.

## Core Concepts
- PyPI (Python Package Index) hosts open-source packages.
- `pip` is the standard installer.
- Use virtual environments to isolate dependencies.

## Basic Commands
```bash
# Install a package
pip install requests

# Show installed packages
pip list

# Show info
pip show requests

# Freeze exact versions (for requirements.txt)
pip freeze > requirements.txt

# Install from requirements file
pip install -r requirements.txt
```

## Example Usage
```python
import requests
resp = requests.get('https://httpbin.org/get')
print(resp.status_code)
```

## Best Practices
- Pin versions for reproducibility (`package==1.2.3`).
- Avoid running `pip` as root; use virtual env.

## Exercises
1. Install `rich` and print colored text.
2. Create `requirements.txt` with 2 packages, reinstall in fresh env.

## Key Takeaways
- External packages accelerate development.
- Always document dependencies for collaborators.
