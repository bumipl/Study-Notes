# 17 Text Command Game (Stateful Loop)

Interactive loop processing user commands with internal state.

## Core Concepts
- Maintain state (`started` flag).
- Normalize input with `.lower()`.
- Provide help menu.
- Use `while True` with `break` to exit.

## Complete Version (Ready to Run)
```python
command = ""
started = False

help_text = """
start - to start the car
stop  - to stop the car
help  - to show this menu
quit  - to exit
""".strip()

print("Type 'help' for commands.")
while True:
    command = input('> ').strip().lower()
    if command == 'start':
        if started:
            print('Car is already started.')
        else:
            started = True
            print('Car started... Ready to go!')
    elif command == 'stop':
        if not started:
            print('Car is already stopped.')
        else:
            started = False
            print('Car stopped.')
    elif command == 'help':
        print(help_text)
    elif command == 'quit':
        print('Goodbye!')
        break
    else:
        print("I don't understand that...")
```

## Explanation
- The flag prevents duplicate start/stop actions.
- `strip()` cleans accidental spaces.

## Enhancements
- Log command history.
- Add `status` command.

## Exercises
1. Add a fuel level that decreases when `start` is used repeatedly.
2. Disallow starting if fuel is zero.

## Key Takeaways
- State variables model real-world conditions.
- Command loops are a pattern for CLI mini-apps.
