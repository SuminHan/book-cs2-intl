# Problem Set

### Required

**1.** Write a function `countZero` defined by:
- input parameter: an integer list `numbers`
- return value: the number of occurrences of `0` in `numbers`

```python
def countZero(numbers):
    # ADD ADDITIONAL CODE HERE!

print(countZero([0,4,0,-2,4,0]))          # 3
print(countZero([1,0,-2,4,0,0,-7,0,5]))   # 4
```

**2.** Write a function `countRange` defined by:
- input parameter: an integer list `numbers` and two integers `lower, upper`
- return value: the number of integers in `numbers` within `[lower, upper]`
  (i.e. `lower <= x <= upper`)

```python
def countRange(numbers, lower, upper):
    # ADD ADDITIONAL CODE HERE!

print(countRange([0,6,2,1,3,4,7], 2, 5))                      # 3
print(countRange([8,9,10,2,4,5,9,7,2,3,7], 3, 7))             # 5
```

**3.** Write a function `countSecondQuadrant` defined by:
- input parameter: a list of points in the plane, each represented as
  `[x,y]`
- return value: the number of points in the second quadrant
  - *What does `p[i][0] < 0 and p[i][1] > 0` mean?*

```python
def countSecondQuadrant(p):
    # ADD ADDITIONAL CODE HERE!

points = [[2,1],[7,5],[-5,2],[-3,5],[-7,4],[-2,-1],
          [-2,-4],[-4,-2],[-6,-4],[4,-4],[6,-2]]

print(countSecondQuadrant(points))  # 3
```

**4.** Write a function `countWithinCircle` defined by:
- input parameter: a list of points in the plane (as in problem 3) and a
  positive integer `r`
- return value: the number of points `(x,y)` with \\(x^2+y^2 \le r^2\\)

```python
def countWithinCircle(p, r):
    # ADD ADDITIONAL CODE HERE!

points = [[2,1],[7,5],[-5,2],[-3,5],[-7,4],[-2,-1],
          [-2,-4],[-4,-2],[-6,-4],[4,-4],[6,-2]]

print(countWithinCircle(points, 3))  # 2
print(countWithinCircle(points, 5))  # 4
print(countWithinCircle(points, 8))  # 9
```

**5.** Write a boolean function `withinRect` defined by:
- input parameter: six integers `top, bottom, left, right, x, y` —
  `top,bottom,left,right` represent an axis-aligned rectangle (e.g.
  `(top,bottom,left,right) = (2,-4,-5,6)`)
- return value: a boolean — `True` if `(x,y)` is inside the rectangle
  (boundary included), `False` otherwise

```python
def withinRect(top, bottom, left, right, x, y):
    # ADD ADDITIONAL CODE HERE!

print(withinRect(2,-4,-5,6, -5,2))  # True
print(withinRect(2,-4,-5,6, 6,-1))  # True
print(withinRect(2,-4,-5,6, 0,1))   # True
print(withinRect(2,-4,-5,6, -6,0))  # False
print(withinRect(2,-4,-5,6, 0,3))   # False
```

Using `withinRect` above, write a function `countWithinRect` defined by:
- input parameter: `top,bottom,left,right` (an axis-aligned rectangle) and a
  list of points in the plane (as in problem 3)
- return value: the number of points within the rectangle (boundary
  included)

```python
def countWithinRect(top, bottom, left, right, p):
    counter = 0
    for i in range(len(p)):
        if withinRect(top, bottom, left, right, p[i][0], p[i][1]):
            # ADD ADDITIONAL CODE HERE!

            ...

points = [[2,1],[7,5],[-5,2],[-3,5],[-7,4],[-2,-1],
          [-2,-4],[-4,-2],[-6,-4],[4,-4],[6,-2]]

print(countWithinRect(2,-4,-5,6, points))  # 7
```

**6.** Write a function `countLeapYear` defined by:
- input parameter: a list `numbers` of positive integers, each representing
  a year
- return value: the number of leap years in `numbers`
  - *Use the `leapYear` boolean function from Week 5.*

```python
def countLeapYear(numbers):
    # ADD ADDITIONAL CODE HERE!

print(countLeapYear([2008,2011,2012,2000]))  # 3
print(countLeapYear([2100,2300,2400,2200]))  # 1
```

**7.** Write a function `countComposite` defined by:
- input parameter: a list `numbers` of positive integers
- return value: the number of composite numbers in `numbers`
  - *`not isPrime(p)` is true iff `p` is composite.*

```python
def isPrime(p):
    for i in range(2, p//2 + 1):
        if p % i == 0:
            return False
    return True

def countComposite(numbers):
    # ADD ADDITIONAL CODE HERE!

num = [217, 287, 181, 143, 163, 319, 233, 399, 203]
print(countComposite(num))  # 6
```

**8.** Write a function `zigzagEntireWorld` defined by:
- input parameter: none
- return value: none
- action: make Hubo visit the entire world in a zig-zag pattern and return
  - *Use `move9steps()` and `zigzag()` below (`move9steps()` moves Hubo 9
    steps forward; `zigzag()` makes Hubo zig-zag one round).*

```python
def move9steps():
    for i in range(9):
        hubo.move()

def zigzag():
    move9steps()
    hubo.turn_left(); hubo.move(); hubo.turn_left()
    move9steps()
    hubo.turn_right(); hubo.move(); hubo.turn_right()

def zigzagEntireWorld():
    # ADD ADDITIONAL CODE HERE!

    zigzag()

zigzagEntireWorld()
```

**9.** Write a function `whirlEntireWorld` defined by:
- input parameter: none
- return value: none
- action: make Hubo visit the entire world in a spiral pattern
  - *Using `L` for "turn left" and a number for "move that many steps
    forward," Hubo's full action sequence is:*
    `1 L 1 L 2 L 2 L 3 L 3 L ... 9 L 9 L 9`

```python
def whirlEntireWorld():
    # ADD ADDITIONAL CODE HERE!

    for n in range(1, 10):
        ...

whirlEntireWorld()
```

**10.** Write a function `zigzagEntireWorld` defined by (a different
pattern from problem 8):
- input parameter: none
- return value: none
- action: make Hubo visit the entire world in the pattern below
  - *Using `L`/`R` for "turn left"/"turn right" and a number for "move that
    many steps forward," Hubo's full action sequence is:*
    `L 1 L 1 L 1 R 1 R 2 R 2 L 1 L 3 L 3 R 1 R 4 R 4`
    `L 1 L 5 L 5 R 1 R 6 R 6 L 1 L 7 L 7 R 1 R 8 R 8`

```python
def zigzagEntireWorld():
    hubo.turn_right()
    # ADD ADDITIONAL CODE HERE!

    for n in range(1, 9):
        if n % 2 == 1:
            ...

zigzagEntireWorld()
```

### Optional Problems

*Not for submission/grading, but good practice (mostly past exam problems).*

**11.** Write a function `countOutOfCircle` defined by:
- input parameter: a list `L` of points in the plane (as in Week 7 problem
  9) and a positive integer `r`
- return value: the number of points in `L` outside the circle
  \\(x^2+y^2=r^2\\)

**12.** Write a function `countLower` defined by:
- input parameter: an integer list `L`
- return value: the number of integers in `L` smaller than the average of
  all integers in `L`

**13.** Write a function `countWithinRange` defined by:
- input parameter: an integer list `L`, each element a cube's side length
- return value: the number of cubes whose volume falls within `[A-B, A+B]`,
  where `A` is the average volume of the cubes and `B` is the standard
  deviation of their volumes
  - *The standard deviation \\(\sigma\\) of numbers \\(x_1,\ldots,x_n\\) is
    \\(\sigma = \sqrt{\frac{\sum_{i=1}^n (x_i-\bar{x})^2}{n}}\\) where
    \\(\bar{x} = \frac{\sum_{i=1}^n x_i}{n}\\).*

**14.** A positive integer `q` is called a *double prime* if `q = 2p` for
some prime `p`.

Write a function `countDoublePrime` defined by:
- input parameter: a list `L` of positive integers
- return value: the number of double primes in `L`

**15.** Write a function `countTriangular` defined by:
- input parameter: a list `L` of positive integers
- return value: the number of triangular numbers in `L` (`n` is triangular
  if \\(n = m(m+1)/2\\) for some positive integer `m`)
  - *Hint: \\(n = m(m+1)/2 \Rightarrow m^2 < 2n < (m+1)^2 \Rightarrow m <
    \sqrt{2n} < m+1\\).*

**16.** Write a function `findMax` defined by:
- input parameter: a list `L` of positive integers
- return value: the maximum value in `L` among elements whose *index* is
  not prime
  - e.g. `L = [110,49,441,91,341,20]`: indices 0,1,4 are non-prime, giving
    values `110, 49, 341` — the maximum is `341`.

**17.** Write a function `colinear` defined by:
- input parameter: a list `L` of points in the plane, each represented as
  `[x,y]` (as in Week 7 problem 12)
- return value: the number of collinear triples `L[i], L[j], L[k]` (`i<j<k`)
