# For Loops II

## Opener: Count the Positive Numbers

```python
L = [3, -1, 4, -5, 2]

for x in L:
    count = 0
    if x > 0:
        count = count + 1

print(count)
```

There are three positive numbers. Does this print 3?

**It prints 1.**

`count = 0` sits inside the loop. So every single time around, the count is
thrown away and started again.

The number you see at the end is not a total. It is just whatever happened
on the last item — and `2` is positive, so you get 1.

*Try `L = [3, -1, 4, -5, -2]` and it prints `0`. Same code, different last item.*

### One space is the whole bug

```python
# Correct -- set up before the loop
count = 0
for x in L:
    if x > 0:
        count = count + 1
print(count)      # 3
```

**The question to ask every counter:** "Does this line need to happen
*once*, or *every time around*?" Setting up belongs outside. Only the
counting belongs inside.

## Topics Covered

- `for` loop pattern: counter (count elements satisfying a condition)
- Toy Robot: basic moves (`move()`, `turn_left()`, `turn_right()`)

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## Problem Set

### Required

**1. `countZero(numbers)`** — number of `0`s in a list. Counter pattern.

**2. `countRange(numbers, lower, upper)`** — count of elements `x` with
`lower <= x <= upper`.

**3. `countSecondQuadrant(p)`** — count of points (each `[x,y]`) in the
second quadrant.
> `p[i][0] < 0 and p[i][1] > 0`.

**4. `countWithinCircle(p, r)`** — count of points with $x^2+y^2 \le r^2$.

**5. `withinRect(top,bottom,left,right, x,y)` / `countWithinRect(...)`** —
first checks if `(x,y)` is inside an axis-aligned rectangle (boundary
included); second counts how many points from a list fall inside it.
```python
print(withinRect(2,-4,-5,6, -5,2))  # True
print(countWithinRect(2,-4,-5,6, points))  # 7
```

**6. `countLeapYear(numbers)`** — count of leap years in a list of years
(reuse `leapYear` from Week 5).

**7. `countComposite(numbers)`** — count of composite numbers (`not isPrime(p)`).

**8. `zigzagEntireWorld()`** — Toy Robot: use `move9steps()` and `zigzag()`
to make the robot zigzag across the whole grid and return.
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
```

**9. `whirlEntireWorld()`** — Toy Robot: spiral pattern, "1 L 1 L 2 L 2 L 3 L
3 L ... 9 L 9 L 9" (`L` = turn left, numbers = steps forward).

**10. `zigzagEntireWorld()`** (a different pattern) — Toy Robot: sequence
"L 1 L 1 L 1 R 1 R 2 R 2 L 1 L 3 L 3 R 1 R 4 R 4 ...".

### Optional Problems

*Not for submission/grading, but good practice (mostly past exam problems).*

**11. `countOutOfCircle(L, r)`** — count of points *outside* the circle
$x^2+y^2=r^2$.

**12. `countLower(L)`** — count of integers in `L` smaller than the average
of all of `L`.

**13. `countWithinRange(L)`** — `L` gives cube side lengths; count cubes
whose *volume* falls within $[A-B, A+B]$ where $A$ is the average volume and
$B$ is the standard deviation of the volumes:
$\sigma = \sqrt{\frac{\sum_{i=1}^n (x_i-\bar{x})^2}{n}}$.

**14. `countDoublePrime(L)`** — a "double prime" is $q=2p$ for some prime
`p`; count how many elements of `L` are double primes.

**15. `countTriangular(L)`** — count of triangular numbers in `L`
($n = m(m+1)/2$).
> Hint: $m(m+1)/2 = n \Rightarrow m < \sqrt{2n} < m+1$.

**16. `findMax(L)`** — maximum value in `L` among elements whose *index* is
not prime. E.g. `L = [110,49,441,91,341,20]` — indices 0,1,4 are non-prime,
giving values `110, 49, 341`, so the answer is `341`.

**17. `colinear(L)`** — count of collinear triples `L[i], L[j], L[k]`
(`i<j<k`) among a list of points.

---
*Source: 2025 offering, `week08_for_2_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
