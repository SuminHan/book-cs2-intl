# Problem Set

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
