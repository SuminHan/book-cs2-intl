# Problem Set

**1. `sumSquares(a)`** — sum of squares of a list's elements.
```python
print(sumSquares([3,5,4]))  # 50
```

**2. `computePolynomial(a, x)`** — evaluate $a_0 + a_1x + a_2x^2 + \cdots +
a_{n-1}x^{n-1}$.
```python
print(computePolynomial([3,5,4], 5))  # 128
```

**3. `harmonicMean(a)`** — \\(\dfrac{n}{\frac{1}{a_0}+\frac{1}{a_1}+\cdots+\frac{1}{a_{n-1}}}\\).

**4. `geometricMean(a)`** — \\(\sqrt[n]{a_0 \cdot a_1 \cdots a_{n-1}}\\).
> Compute the product first, then raise to the `1/n` power.

**5. `reverse(a)`** — new list with elements in reverse order.
```python
print(reverse([3,1,5,2,4]))  # [4,2,5,1,3]
```

**6. `square(a)`** — new list where each element is squared (original list
unchanged).
```python
L = [7,6,3,1,5,8,2,4]
print(square(L))  # [49,36,9,1,25,64,4,16]
print(L)          # [7,6,3,1,5,8,2,4] -- L itself unchanged
```

**7. `accumulate(a)`** — running-sum list: `b[i] = a[0]+a[1]+...+a[i]`.
```python
print(accumulate([1,2,1,3,1]))  # [1,3,4,7,8]
```
> `b[i] = b[i-1] + a[i]`.

**8. `fibonacci(n)`** — first `n` Fibonacci numbers `1, 1, 2, 3, 5, 8, ...`.
```python
print(fibonacci(10))  # [1,1,2,3,5,8,13,21,34,55]
```

**9. `area(p)`** — area of a polygon (list of `[x,y]` points, given
counter-clockwise) via the Shoelace formula:
\\(\text{area} = \frac{1}{2}\left|\sum_{i=0}^{n-1} x_i \cdot (y_{(i+1)\bmod n} - y_{(i-1)\bmod n})\right|\\)
```python
points = [[3,1],[6,3],[4,4],[7,6],[2,7],[0,5],[2,3],[1,2]]
print(area(points))  # 22.0
```
> Use `abs(x)` for \\(|x|\\).

**10. `perimeter(p)`** — perimeter of the same kind of polygon (sum of
consecutive-point distances, wrapping around).
```python
print(perimeter(points))  # 23.85332583138582
```

**11. `findMin(a)`** — minimum value in a list (max/min pattern, from Week 6).
```python
print(findMin([7,8,3,4,3,6]))  # 3
```

**12. `closestPair(p)`** — smallest distance between any two points in a
list of `[x,y]` points.
```python
def distSquared(p1, p2):
    return (p2[0]-p1[0])**2 + (p2[1]-p1[1])**2

def closestPair(p):
    n = len(p)
    min_d = distSquared(p[0], p[1])
    # ADD ADDITIONAL CODE HERE!

points = [[4,-4],[7,5],[2,1],[-2,-1],[-3,5]]
print(closestPair(points))  # 4.47213595499958 (between [2,1] and [-2,-1])
```

---
*Source: 2025 offering, `week07_list_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
