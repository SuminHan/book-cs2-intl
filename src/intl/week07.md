# Lists

You want a 3×3 grid of zeros. You already know that `[0]*3` gives
`[0, 0, 0]`, so:

```python
grid = [[0]*3] * 3
grid[0][0] = 1
print(grid)
```

You changed **one** cell. What prints?

**All three rows changed:**

```
[[1, 0, 0], [1, 0, 0], [1, 0, 0]]
```

`* 3` did not make three rows. It made three names for the same row.

```python
print(grid[0] is grid[1])    # True -- the same object
```

A list does not hold rows inside itself; it holds directions to rows.
Copying the directions three times still leaves one row.

### Make each row separately

```python
# Correct
grid = [[0]*3 for _ in range(3)]
grid[0][0] = 1
print(grid)   # [[1,0,0], [0,0,0], [0,0,0]]
```

**Why this bug is worth remembering:** the code runs. There is no error.
The grid *looks* right until you change one cell — and then it is wrong
everywhere at once.
