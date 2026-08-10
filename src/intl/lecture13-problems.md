# Problem Set

**1. Counting zeros in a 3D array.** Write a function `countZero` that
takes as input a list of integers representing a three-dimensional array
and counts the number of zeros contained in the array.

```python
def countZero(a):
    depth = len(a)
    height = len(a[0])
    width = len(a[0][0])
    # ADD ADDITIONAL CODE HERE!
print(countZero([[[1,2],[0,0]],[[0,0],[0,0]]]))                # 6
print(countZero([[[1,2],[0,0]],[[0,0],[0,0]],[[0,0],[0,0]]]))  # 10
```

**2. Checking sorted order in a 2D array.** Write a function `isSorted`
that takes as input a list of integers representing a two-dimensional array
and checks whether all elements in the array are sorted in ascending order
both row-wise and column-wise.

```python
def isSorted(a):
    # ADD ADDITIONAL CODE HERE!
test1 = [[2,3,7,9,11,12],
         [5,6,8,10,12,15],
         [7,7,8,10,12,15],
         [8,9,10,10,13,17]]
test2 = [[2,3,7,9,11,12],
         [5,6,8,10,12,15],
         [7,7,8,10,12,18],
         [8,9,10,10,13,17]]
print(isSorted(test1))  # True
print(isSorted(test2))  # False
```

**3-1. Point in Rectangle: checking if a point is inside a rectangle.**
Write a function `withinRect` that takes as parameters the values `top`,
`bottom`, `left`, `right` representing a rectangle in the 2D plane whose
sides are parallel to the x-axis and y-axis, along with the coordinates
`x`, `y` of a point. The function should return `True` if the point lies
inside or on the boundary of the rectangle, and `False` otherwise. For
example, `(top,bottom,left,right) = (2,-4,-5,6)` represents one such
rectangle.

```python
def withinRect(top, bottom, left, right, x, y):
    # ADD ADDITIONAL CODE HERE!
print(withinRect(2,-4,-5,6, -5,2))  # True
print(withinRect(2,-4,-5,6, 6,-1))  # True
print(withinRect(2,-4,-5,6, 0,1))   # True
print(withinRect(2,-4,-5,6, -6,0))  # False
print(withinRect(2,-4,-5,6, 0,3))   # False
```

**3-2. Counting points inside a rectangle.** Using `withinRect` above,
write a function `countWithinRect` that takes as input integer values
`top`, `bottom`, `left`, `right` representing a rectangle parallel to the
coordinate axes, along with a list `p` containing the coordinates of points
in the plane. The function should count and return the number of points
from the list that lie inside or on the boundary of the rectangle.

```python
def countWithinRect(top, bottom, left, right, p):
    # ADD ADDITIONAL CODE HERE!
points = [[2,1],[7,5],[-5,2],[-3,5],[-7,4],[-2,-1],[-2,-4],[-4,-2],[-6,-4],[4,-4],[6,-2]]
print(countWithinRect(2,-4,-5,6, points))  # 7
```

**4. Closest pair of points.** Write a function `closestPair` that takes as
input a list of points in the 2D plane, where each point is represented as
a list `[x,y]`. The function should compute and return the distance
between the two closest points among them.

```python
def distSquared(p1, p2):
    return ((p2[0]-p1[0])**2 + (p2[1]-p1[1])**2) ** 0.5
def closestPair(p):
    n = len(p)
    best = distSquared(p[0], p[1])  # start with the first pair, then improve
    # ADD ADDITIONAL CODE HERE!
points = [[4,-4],[7,5],[2,1],[-2,-1],[-3,5]]
print(closestPair(points))  # 4.47213595499958
```

**5. Checking for negative numbers in each row.** Write a function `check`
that takes as input a two-dimensional list of integers `M` and checks
whether *every* row contains *at least one* negative number (both a "for
all" and a "for some" condition need to be satisfied).

```python
def check(M):
    # ADD ADDITIONAL CODE HERE!
M1 = [[1,9,-1,0,2],
      [-3,7,1,1,4],
      [3,9,1,-9,-2]]
M2 = [[1,9,1,0,2],
      [-3,7,1,1,4],
      [3,9,-1,-9,2]]
print(check(M1))  # True
print(check(M2))  # False
```

**6. 1D mine-field array.** Write a function `countMines` that takes as
input a list of boolean values, where `T` represents a location with a mine
and `F` a location without one. The function should produce a mine-field
array where each position holds the total number of mines among its
neighboring positions — here, neighbors are the position itself plus the
two immediately adjacent positions (left and right).

*Use a helper function `withinBoundary` to check whether an index is
within the valid range of the list, to avoid accessing out-of-bounds
elements.*

```python
def withinBoundary(size, i):
    return i >= 0 and i < size
def countMines(mineField):
    # ADD ADDITIONAL CODE HERE!
T = True
F = False
mineField1 = [T, F, F, T, T, T, T, F, T, F]
mineField2 = [T, F, T, T, T, F, F]
print(countMines(mineField1))  # [1,1,1,2,3,3,2,2,1,1]
print(countMines(mineField2))  # [1,2,2,3,2,1,0]
```

**7. 2D mine-field array.** Extend problem 6 to two dimensions. Write a
function `countMines` that takes as input a two-dimensional list of boolean
values, where `T` indicates a cell with a mine and `F` a cell without one,
and produces a mine-field array showing, for each cell, the number of
neighboring mines — here, neighbors are the cell itself plus the eight
immediately adjacent cells (up, down, left, right, and the four diagonals),
9 cells in total.

```python
def withinBoundary(height, width, i, j):
    return i >= 0 and i < height and j >= 0 and j < width
def countMines(mineField):
    # ADD ADDITIONAL CODE HERE!
def main():  # for test
    T = True
    F = False
    mineField = [
        [T, F, F, F, F, T],
        [F, F, F, F, F, T],
        [T, T, F, T, F, T],
        [T, F, F, F, F, F],
        [F, F, T, F, F, F],
        [F, F, F, F, F, F]]
    mines = countMines(mineField)
    for i in range(len(mines)):
        print(mines[i])
main()
```
Output:
```
[1, 1, 0, 0, 2, 2]
[3, 3, 2, 1, 4, 3]
[3, 3, 2, 1, 3, 2]
[3, 4, 3, 2, 2, 1]
[1, 2, 1, 1, 0, 0]
[0, 1, 1, 1, 0, 0]
```
