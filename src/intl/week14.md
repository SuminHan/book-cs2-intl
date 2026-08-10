# Multi-Dimensional Lists

## 13.1. Opener: Three Rules on a Grid

A 2-D list of cells. Each is alive (`#`) or dead (`.`). Every step, every
cell looks at its 8 neighbours and follows three rules:

- Alive with 2 or 3 living neighbours → stays alive.
- Alive with anything else → dies.
- Dead with exactly 3 living neighbours → becomes alive.

That is the whole program. No randomness, no AI, nothing else. What can
three rules possibly do?

### Watch this shape

```
step 0        step 1        step 2        step 3        step 4
.#....        ......        ......        ......        ......
..#...        #.#...        ..#...        .#....        ..#...
###...        .##...        #.#...        ..##..        ...#..
......        .#....        .##...        .##...        .###..
```

Step 4 is the same shape as step 0 — moved one square down and one square
right.

**It walks. Nobody wrote "walk."** (This is the classic *glider* from
Conway's Game of Life.)

### Why this is your week

Everything you need is what you are learning right now:

- a **2-D list** to hold the grid
- **nested `for` loops** to visit every cell
- an **`if`** for the three rules
- and **a second grid** — because if you edit the first one while reading
  it, you will be reading cells that have already changed

That last point is this week's real trap, and it is the same trap as
Week 11: do not modify the thing you are walking through.

## 13.2. Topics Covered

- Creating a 2D list by assigning values directly
- Accessing elements in a 2D list using indices
- Lists store references, not the data itself

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## 13.3. Problem Set

**1. `countZero(a)`** — count of zeros in a 3D array.
```python
def countZero(a):
    depth = len(a)
    height = len(a[0])
    width = len(a[0][0])
    # ADD ADDITIONAL CODE HERE!
print(countZero([[[1,2],[0,0]],[[0,0],[0,0]]]))  # 6
```

**2. `isSorted(a)`** — are all rows *and* all columns of a 2D array sorted
in non-decreasing order?

**3. `withinRect(top,bottom,left,right, x,y)` / `countWithinRect(...)`** —
first checks if `(x,y)` is inside/on an axis-aligned rectangle; second
counts how many points from a list fall inside it.
```python
print(withinRect(2,-4,-5,6, -5,2))  # True
print(countWithinRect(2,-4,-5,6, points))  # 7
```

**4. `closestPair(p)`** — smallest distance between any two points in a
list of `[x,y]` points.
```python
def distSquared(p1, p2):
    return ((p2[0]-p1[0])**2 + (p2[1]-p1[1])**2) ** 0.5
def closestPair(p):
    n = len(p)
    min_d = distSquared(p[0], p[1])  # start with the first pair, then improve
    # ADD ADDITIONAL CODE HERE!
points = [[4,-4],[7,5],[2,1],[-2,-1],[-3,5]]
print(closestPair(points))  # 4.47213595499958
```

**5. `check(M)`** — does *every* row of 2D list `M` contain *at least one*
negative number? (Both a "for all" over rows and a "for some" within each
row.)
```python
M1 = [[1,9,-1,0,2], [-3,7,1,1,4], [3,9,1,-9,-2]]
print(check(M1))  # True
```

**6. `countMines(mineField)` (1D)** — for a 1D boolean minefield, produce a
list where each position holds the count of mines among itself and its two
adjacent neighbors.
```python
def withinBoundary(size, i):
    return 0 <= i < size
def countMines(mineField):
    # ADD ADDITIONAL CODE HERE!
T, F = True, False
print(countMines([T, F, F, T, T, T, T, F, T, F]))  # [1,1,1,2,3,3,2,2,1,1]
```

**7. `countMines(mineField)` (2D)** — same idea, extended to 2D with all 8
neighbors + self (9 cells).
```python
def withinBoundary(height, width, i, j):
    return 0 <= i < height and 0 <= j < width
def countMines(mineField):
    # ADD ADDITIONAL CODE HERE!
```

---
*Source: 2025 offering, `week14_MDL_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
