# 21 2D Lists (Nested Lists)

Represent grid / matrix-like data using lists of lists.

## Core Concepts
- A 2D list is a list where each element is another list.
- Access with two indices: `matrix[row][col]`.
- Nested loops to traverse all items.

## Example (Ready to Run)
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(matrix[0][1])  # 2

for row in matrix:
    for item in row:
        print(item)
```

## Explanation
- `matrix[0]` is `[1,2,3]`.
- `matrix[0][1]` drills into the second element of the first row.

## Mutating Elements
```python
matrix[1][2] = 600  # change 6 to 600
```

## Exercises
1. Compute the sum of all numbers.
2. Flatten the matrix into a single list using loops.

## Key Takeaways
- Nested structures require nested access.
- Be careful with shared inner lists (avoid `[[0]*3]*3`).
