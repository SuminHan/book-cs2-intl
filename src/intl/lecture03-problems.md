# Problem Set

### Required

**1.** Write a function `maximum` defined by:
- input parameter: two integers `n1, n2`
- return value: the maximum value among `n1` and `n2`

```python
def maximum(n1, n2):
    # ADD ADDITIONAL CODE HERE!

print(maximum(5, 7))  # 7
print(maximum(7, 5))  # 7
print(maximum(5, 5))  # 5
```

**2.** Write a function `countZeros` defined by:
- input parameter: five integers `n1, n2, n3, n4, n5`
- return value: the number of `0`s among `n1, n2, n3, n4, n5`

```python
def countZeros(n1, n2, n3, n4, n5):
    counter = 0
    if n1 == 0:
        counter = counter + 1
    if n2 == 0:
        counter = counter + 1
    # ADD ADDITIONAL CODE HERE!

print(countZeros(1, 0, 3, 0, 0))  # 3
print(countZeros(0, 2, 2, 0, 4))  # 2
print(countZeros(1, 2, 3, 0, 4))  # 1
print(countZeros(1, 2, 3, 5, 4))  # 0
```

**3.** Write a function `smaller` defined by:
- input parameter: two integers `n1, n2`
- return value: a string — `"left"` if `n1` is less than `n2`, `"right"` if
  `n2` is less than `n1`, `"equal"` otherwise

```python
def smaller(n1, n2):
    # ADD ADDITIONAL CODE HERE!

print(smaller(5, 7))  # left
print(smaller(7, 5))  # right
print(smaller(5, 5))  # equal
```

**4.** Write a function `quadrant` defined by:
- input parameter: two integers `x, y` (the x/y coordinates of a point)
- return value: a string — `"First Quadrant"` if `x,y > 0`, `"Second
  Quadrant"` if `x < 0, y > 0`, `"Third Quadrant"` if `x,y < 0`, `"Fourth
  Quadrant"` if `x > 0, y < 0`, `"On the Boundary"` otherwise

```python
# ADD FUNCTION HERE!

print(quadrant(10, 5))   # First Quadrant
print(quadrant(-5, 3))   # Second Quadrant
print(quadrant(-5, -7))  # Third Quadrant
print(quadrant(3, -5))   # Fourth Quadrant
print(quadrant(0, -3))   # On the Boundary
```

**5.** Write a function `round` defined by:
- input parameter: a float `x >= 0`
- return value: the integer nearest to `x` (rounding) — e.g. `2.4` → `2`,
  `2.5` → `3`, `2.6` → `3`
  - *Make use of the value `x - int(x)`.*

```python
def round(x):
    fraction = x - int(x)
    # ADD ADDITIONAL CODE HERE!

print(round(2.4))  # 2
print(round(2.5))  # 3
print(round(2.6))  # 3
```

**6.** Write a function `ceiling` defined by:
- input parameter: a float `x >= 0`
- return value: the integer \\(\lceil x \rceil\\) (ceiling) — e.g. `2.0` →
  `2`, `2.1` → `3`, `2.6` → `3`

```python
# ADD FUNCTION HERE!

print(ceiling(2.0))              # 2
print(ceiling(2.0000000000001))  # 3
print(ceiling(2.99))             # 3
```

**7.** Write a function `quadratic` defined by:
- input parameter: three integers `a, b, c`
- return value: the number of real roots of \\(ax^2+bx+c=0\\)
  - *Note: `a` and `b` may be 0; assume `a=b=c=0` is never given as input.*

```python
def quadratic(a, b, c):
    if a == 0:
        # ADD ADDITIONAL CODE HERE!

    else:
        D = b**2 - 4*a*c
        # ADD ADDITIONAL CODE HERE!

print(quadratic(0, 0, 1))   # 0
print(quadratic(0, 1, 1))   # 1
print(quadratic(1, -2, 1))  # 1
print(quadratic(1, 1, 1))   # 0
print(quadratic(1, -4, 1))  # 2
```

**8.** Write a function `minX` defined by:
- input parameter: three integers `a, b, c` where `a > 0` and `b < 0`
- return value: the integer `x` that minimizes \\(ax^2+bx+c\\) (the smallest
  such integer, if there's a tie)
  - e.g. if `a=1, b=-9, c=2`, then `x=4` is returned (not `4.5` or `5`).
  - *Focus on `x0 = int(-b/(2*a))` and `x0 + 1`.*

```python
def f(a, b, c, x):
    return a*x**2 + b*x + c

def minX(a, b, c):
    x0 = int(-b / (2*a))
    # ADD ADDITIONAL CODE HERE!

print(minX(1, -9, 2))   # 4
print(minX(9, -5, 0))   # 0
print(minX(9, -15, 0))  # 1
print(minX(7, -13, 3))  # 1
```

**9.** Write a function `rock_paper_scissors` defined by:
- input parameter: two strings `first, second`, each one of `"R"`, `"P"`,
  `"S"` (Rock/Paper/Scissors)
- return value: a string — `"First"` if `first` wins, `"Second"` if `second`
  wins, `"Tie"` if the game is tied

```python
def rock_paper_scissors(first, second):
    if first == second:
        return "Tie"
    # ADD ADDITIONAL CODE HERE!

    # if first == "R" ...

print(rock_paper_scissors("R","R"))  # Tie
print(rock_paper_scissors("R","S"))  # First
print(rock_paper_scissors("R","P"))  # Second
print(rock_paper_scissors("S","S"))  # Tie
print(rock_paper_scissors("S","P"))  # First
print(rock_paper_scissors("S","R"))  # Second
print(rock_paper_scissors("P","P"))  # Tie
print(rock_paper_scissors("P","R"))  # First
print(rock_paper_scissors("P","S"))  # Second
```

**10.** Write a function `better` defined by:
- input parameter: six integers representing the medal standings of two
  countries — `gold1,silver1,bronze1` for the first, `gold2,silver2,bronze2`
  for the second
- return value: a string — `"First"` if the first country's result is
  better, `"Second"` if the second's is better, `"Tie"` if tied — ranked in
  gold-silver-bronze order (**not** by total medal count)

```python
def better(gold1, silver1, bronze1, gold2, silver2, bronze2):
    if gold1 > gold2:
        return "First"
    if gold1 < gold2:
        return "Second"
    # ADD ADDITIONAL CODE HERE!

print(better(10,4,24, 1,35,25))    # First
print(better(1,35,25, 10,4,24))    # Second
print(better(10,18,0, 10,4,24))    # First
print(better(10,4,24, 10,18,0))    # Second
print(better(10,20,5, 10,20,4))    # First
print(better(10,20,4, 10,20,5))    # Second
print(better(10,20,5, 10,20,5))    # Tie
```

### Optional Problems

**11.** Write a function `area` defined by:
- input parameter: six positive integers `x1,y1,l1,x2,y2,l2`, where
  `x1,y1,l1` represent a square centered at `(x1,y1)` with side length `l1`,
  and `x2,y2,l2` represent another square centered at `(x2,y2)` with side
  length `l2` (assume `l1 >= l2`)
- return value: the area of the intersection of the two squares

**12.** A positive integer `n` is a *triangular number* if there exists a
positive integer `m` such that \\(n = m(m+1)/2\\).

Write a function `triangular` defined by:
- input parameter: a positive integer `n`
- return value: the positive integer `m` such that \\(n=m(m+1)/2\\), or
  `None` if `n` is not a triangular number
  - *Hint: \\(n = m(m+1)/2 \Rightarrow m^2 < 2n < (m+1)^2 \Rightarrow m <
    \sqrt{2n} < m+1\\).*
