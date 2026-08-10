# Problem Set

**1. `printMultTable1()` / `printMultTable2()`** — print parts of a
multiplication table (odd rows only; then a growing triangular shape):
```
1 2 3 4 5 6 7 8 9
3 6 9 12 15 18 21 24 27
5 10 15 20 25 30 35 40 45
...
```
and
```
1
3 6 9
5 10 15 20 25
...
```
> What does `for i in range(1, 10, 2):` do? What about the nested
> `for j in range(1, i+1):`?

**2. `sumNumbers(a, b)`** — sum of integers from `a` to `b` inclusive.
```python
print(sumNumbers(5,10))    # 45
print(sumNumbers(15,100))  # 4945
```

**3. `factorial(n)`** — \\(n!\\).
```python
print(factorial(8))   # 40320
print(factorial(12))  # 479001600
```

**4. `exp(x)`** — approximate \\(e^x\\) via the series
\\(e^x \approx 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots + \frac{x^{100}}{100!}\\).
Reuse `factorial` from problem 3.
```python
print(exp(1.0))  # 2.7182818284590455
```

**5. `withinCircle(r)`** — number of integer-coordinate points `(x,y)` with
\\(x^2+y^2 \le r^2\\).
```python
print(withinCircle(1000) / 1000**2)  # 3.141549 -- approximates π
```

**6. `dayOfWeek(year, month, day)`** (`year ≥ 2000`) — day of week as
`"Mon"`..`"Sun"`.
> Reuse `leapYear`/`numDays` from Week 5. `2000-01-01` was a Saturday — count
> days elapsed from there and take `% 7`.
```python
print(dayOfWeek(2001,1,28))  # Sun
print(dayOfWeek(2013,3,23))  # Sat
```

**7. `findMax()`** — maximum value of
\\(f(i,j) = (i^5 + 2i^3j^2 + 5i^2 + j + 5000) \bmod 10000\\) for
\\(i,j \in \{0,\ldots,99\}\\).
```python
def f(i, j):
    return (i**5 + 2*(i**3)*(j**2) + 5*i**2 + j + 5000) % 10000
print(findMax())  # 9997
```

**8. `combination(n, k)`** (\\(1 \le k \le n \le 250\\)) — \\(\binom{n}{k}\\), as an
`int` (not `float`).
> Use \\(\prod_{i=1}^{k} \frac{n+1-i}{i} = \frac{n}{1}\cdot\frac{n-1}{2}\cdots\frac{n+1-k}{k}\\)
> and divide as you go to keep values manageable.

**9. `maxPrimeFactor(n)`** (`n ≥ 2`) — largest prime factor of `n`. E.g.
`maxPrimeFactor(12)` → `3` (since \\(12 = 2 \times 2 \times 3\\)).

**10. `withinRegion(a, c)`** — number of integer points `(x,y)` satisfying
both \\(y \le -ax^2+c\\) and \\(y \ge ax^2-c\\) (the region between two parabolas).

---
*Source: 2025 offering, `week06_for_1_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
