# Break / Continue

## 1. Opener: Find Where the Target Is

Return the position of the first `target` in a grid, or `(-1,-1)` if it is
not there.

```python
def find_position(M, target):
    pos = (-1, -1)
    for i in range(len(M)):
        for j in range(len(M[i])):
            if M[i][j] == target:
                pos = (i, j)
                break
    return pos
```

You test it: `find_position([[1,2],[3,4]], 9)` gives `(-1,-1)`. Correct. Ship it?

### Now a grid that has the target

```python
find_position([[7,1],[2,7],[7,3]], 7)
```

**Expected:** `(0, 0)` — 7 is right there in the corner.

**Execution result:** `(2, 0)`

Why: `break` leaves *one* loop — the inner one. The outer loop keeps going,
finds 7 again on the next row, and overwrites the answer. You get the
*last* match, not the first.

The test you ran had no target in it at all, so the inner loop never broke
and the bug never showed.

### Two fixes, one lesson

```python
# Leave the whole function at once
            if M[i][j] == target:
                return (i, j)     # not break
```

**The lesson:** `break` is smaller than it looks. It escapes exactly one
loop, and inside nested loops that is almost never what you meant.

*Choosing the input that exposes it — that was the real skill.*

## 2. Topics Covered

- `break` — exits the innermost loop only
- `continue` — skips the rest of the current iteration

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*
