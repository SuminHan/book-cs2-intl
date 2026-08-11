# Problem Set

**1.** Write a function `sumSquares` defined by:
- input parameter: an integer list `a` (of length `n`)
- return value: \\(a_0^2 + a_1^2 + a_2^2 + \cdots + a_{n-1}^2\\) — the sum of
  squares of the elements of `a`
  - e.g. `sumSquares([4,3,12])` returns `169` (\\(=4^2+3^2+12^2\\)).

```python
def sumSquares(a):
    n = len(a)
    total = 0
    # ADD ADDITIONAL CODE HERE!

print(sumSquares([3,5,4]))               # 50
print(sumSquares([2,5,4,0,1,-1,5,1]))    # 73
```

**2.** Write a function `computePolynomial` defined by:
- input parameter: an integer list `a` (of length `n`) and an integer `x`
- return value: \\(a_0 + a_1 x + a_2 x^2 + \cdots + a_{n-1}x^{n-1}\\)

```python
def computePolynomial(a, x):
    n = len(a)
    total = 0
    # ADD ADDITIONAL CODE HERE!

print(computePolynomial([3,5,4], 5))            # 128
print(computePolynomial([2,0,4,0,1,-1,5,1], 3)) # 5708
```

**3.** Write a function `harmonicMean` defined by:
- input parameter: a list `a` of `n` positive integers
- return value: the harmonic mean of the values in `a`,
  \\(\dfrac{n}{\frac{1}{a_0}+\frac{1}{a_1}+\cdots+\frac{1}{a_{n-1}}}\\)
  - *First write code to compute the sum of reciprocals, then return `n /
    sum`.*

```python
def harmonicMean(a):
    n = len(a)
    # ADD ADDITIONAL CODE HERE!

numbers = [2, 4, 3, 10, 7, 2, 5, 6]
print(harmonicMean(numbers))  # 3.648208469055375
```

**4.** Write a function `geometricMean` defined by:
- input parameter: a list `a` of `n` positive integers
- return value: the geometric mean of the values in `a`,
  \\(\sqrt[n]{a_0 \cdot a_1 \cdots a_{n-1}}\\)
  - *First compute `prod = a[0]*a[1]*...*a[n-1]`, then return `prod**(1/n)`.*

```python
def geometricMean(a):
    n = len(a)
    prod = 1
    # ADD ADDITIONAL CODE HERE!

print(geometricMean([3,2,6,4,7]))           # 3.987421134470927
print(geometricMean([2,4,3,10,7,2,5,6]))    # 4.221167313317658
```

**5.** Write a function `reverse` defined by:
- input parameter: a list of integers
- return value: a new list, same length, with the order reversed
  - e.g. `reverse([1,5,3,7,6])` returns `[6,7,3,5,1]`.

```python
def reverse(a):
    n = len(a)
    b = [None] * n
    for i in range(n):
        b[i] = a[??]  # ADD ADDITIONAL CODE HERE!
    return b

print(reverse([3,1,5,2,4]))          # [4,2,5,1,3]
print(reverse([7,6,3,1,5,8,2,4]))    # [4,2,8,5,1,3,6,7]
```

**6.** Write a function `square` defined by:
- input parameter: a list of integers
- return value: a new list, same length, with each element squared
  - e.g. `square([1,3,5,6,7])` returns `[1,9,25,36,49]`.
  - *The overall structure is very similar to `reverse` above.*

```python
def square(a):
    # ADD ADDITIONAL CODE HERE!

L = [7,6,3,1,5,8,2,4]
print(square(L))  # [49,36,9,1,25,64,4,16]
print(L)          # [7,6,3,1,5,8,2,4]  -- L itself unchanged
```

**7.** Write a function `accumulate` defined by:
- input parameter: an integer list `a`
- return value: a list `b`, same length, of running sums —
  `b[i] = a[0]+a[1]+...+a[i]` for each `i`
  - e.g. `accumulate([1,2,1,3,1])` returns `[1,3,4,7,8]`.
  - *Use the fact that `b[i] == b[i-1]+a[i]` for `i = 1,2,...`.*

```python
def accumulate(a):
    n = len(a)
    b = [None] * n
    b[0] = a[0]
    # ADD ADDITIONAL CODE HERE!

    for i in range(1, n):  # note that i starts from 1, not 0
        ...

print(accumulate([1,2,3,4,5]))        # [1,3,6,10,15]
print(accumulate([7,6,3,1,5,8,2,4]))  # [7,13,16,17,22,30,32,36]
```

**8.** Fibonacci numbers form the sequence `1, 1, 2, 3, 5, 8, 13, 21, 34, 55,
89, 144, ...`.

Write a function `fibonacci` defined by:
- input parameter: an integer `n`
- return value: a list `b` of the first `n` Fibonacci numbers
  - e.g. `fibonacci(5)` returns `[1,1,2,3,5]`.
  - *Use the fact that `b[i] == b[i-1]+b[i-2]` for `i = 2,3,...`.*

```python
def fibonacci(n):
    b = [None] * n
    b[0] = 1
    b[1] = 1
    # ADD ADDITIONAL CODE HERE!

    for i in range(??):  # note that i starts from 2
        ...

print(fibonacci(5))   # [1,1,2,3,5]
print(fibonacci(10))  # [1,1,2,3,5,8,13,21,34,55]
```

**9.** Write a function `area` defined by:
- input parameter: a list of points representing a polygon, given in
  counter-clockwise order — each point is a list `[x,y]` of two integers
  - e.g. `[[3,1],[6,3],[4,4],[7,6],[2,7],[0,5],[2,3],[1,2]]` represents an
    8-sided polygon.
- return value: the area of the polygon
  - *Use the Shoelace formula:*
    \\(\text{area} = \frac{1}{2}\left|\sum_{i=0}^{n-1} x_i \cdot
    (y_{(i+1)\bmod n} - y_{(i-1)\bmod n})\right|\\)
  - *What does `p[i][0] * (p[(i+1)%n][1] - p[(i-1)%n][1])` mean, where `p`
    is the input polygon?*
  - *Use `abs(x)` for \\(|x|\\).*

```python
def area(p):
    n = len(p)
    total = 0
    # ADD ADDITIONAL CODE HERE!

    for i in range(n):
        ...

points = [[3,1],[6,3],[4,4],[7,6],[2,7],[0,5],[2,3],[1,2]]
print(area(points))  # 22.0
```

**10.** Write a function `perimeter` defined by:
- input parameter: a list of points representing a polygon, as in the
  previous problem
- return value: the perimeter of the polygon
  - *As in the previous problem, use the expression `p[(i+1)%n]`.*

```python
# ADD FUNCTION HERE!

points = [[3,1],[6,3],[4,4],[7,6],[2,7],[0,5],[2,3],[1,2]]
print(perimeter(points))  # 23.85332583138582
```

**11.** Write a function `findMin` defined by:
- input parameter: a list of integers
- return value: the minimum value among the elements
  - *This is the max/min pattern from Week 6.*

```python
def findMin(a):
    best = a[0]
    # ADD ADDITIONAL CODE HERE!

    for i in range(1, len(a)):
        if a[i] < best:
            ...

print(findMin([7,8,3,4,3,6]))        # 3
print(findMin([3,5,7,2,7,2,3,8,6]))  # 2
```

**12.** Write a function `closestPair` defined by:
- input parameter: a list of points in the plane, each represented as
  `[x,y]` as in problem 9
  - e.g. `[[4,-4],[7,5],[2,1]]` represents the points `(4,-4)`, `(7,5)`,
    `(2,1)`.
- return value: the distance of the closest pair of points (the minimum
  pairwise distance)

```python
def distSquared(p1, p2):
    return (p2[0]-p1[0])**2 + (p2[1]-p1[1])**2

def closestPair(p):
    n = len(p)
    best = distSquared(p[0], p[1])
    # ADD ADDITIONAL CODE HERE!

    for i in range(n):
        for j in range(i+1, n):
            d = distSquared(p[i], p[j])
            if d < best:
                ...

points = [[4,-4],[7,5],[2,1],[-2,-1],[-3,5]]
print(closestPair(points))  # 4.47213595499958  (between [2,1] and [-2,-1])
```
