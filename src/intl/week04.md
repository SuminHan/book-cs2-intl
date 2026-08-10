# Conditionals

## 3.1. Opener: 45 Minutes

**1 August 2012, 9:30 a.m.** Knight Capital was the largest trader of US
stocks. Its software started buying high and selling low — thousands of
times per second.

It was meant to place 212 orders. It placed more than 4 million.

Forty-five minutes later the company had lost **$440 million** — more than
it was worth.

### The cause was an `if`

Back in 2003 the code had a switch that turned on an old feature called
*Power Peg*:

```python
if flag:
    run_power_peg()      # 2003: an old testing feature
```

Years later that same `flag` was reused to mean something completely
different — and nobody deleted the old branch.

On deployment day the new code reached 7 of the 8 servers. The eighth still
had the 2003 branch. When the flag went up, that server did what it was told.

> Widely documented; see the SEC administrative proceeding against Knight
> Capital (2013).

### What an `if` really is

An `if` is a promise about the future: "whenever this condition is true, do
this."

The condition was still true. The code still ran. Only the meaning had
changed — and a condition cannot notice that.

**Every `if` you write this week is a promise that has to stay true after
you forget you wrote it.**

## 3.2. Topics Covered

- Boolean type / boolean expressions
- `if`-`else` conditionals
- Multiple return paths

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## 3.3. Problem Set

### Required

**1. `maximum(n1, n2)`** — larger of two integers.
```python
print(maximum(5,7))  # 7
print(maximum(7,5))  # 7
print(maximum(5,5))  # 5
```

**2. `countZeros(n1,n2,n3,n4,n5)`** — how many of the five arguments are 0.
```python
def countZeros(n1,n2,n3,n4,n5):
    counter = 0
    if n1 == 0: counter += 1
    if n2 == 0: counter += 1
    # ADD ADDITIONAL CODE HERE!
print(countZeros(1,0,3,0,0))  # 3
print(countZeros(0,2,2,0,4))  # 2
```

**3. `smaller(n1, n2)`** — `"left"` if `n1 < n2`, `"right"` if `n2 < n1`,
`"equal"` otherwise.

**4. `quadrant(x, y)`** — which quadrant the point `(x,y)` is in: `"First
Quadrant"`, `"Second Quadrant"`, `"Third Quadrant"`, `"Fourth Quadrant"`, or
`"On the Boundary"`.
```python
print(quadrant(10, 5))   # First Quadrant
print(quadrant(-5, 3))   # Second Quadrant
print(quadrant(-5, -7))  # Third Quadrant
print(quadrant(3, -5))   # Fourth Quadrant
print(quadrant(0, -3))   # On the Boundary
```

**5. `round(x)`** (rounding, without using the built-in `round()`) — nearest
integer to `x` (e.g. 2.4→2, 2.5→3, 2.6→3).
```python
def round(x):
    fraction = x - int(x)
    # ADD ADDITIONAL CODE HERE!
```

**6. `ceiling(x)`** — smallest integer $\geq x$ (2.0→2, 2.1→3, 2.6→3).

**7. `quadratic(a, b, c)`** — number of real roots of $ax^2+bx+c=0$
(`a` may be 0; `a=b=c=0` never given).
```python
def quadratic(a, b, c):
    if a == 0:
        # ADD ADDITIONAL CODE HERE!
    else:
        D = b**2 - 4*a*c
        # ADD ADDITIONAL CODE HERE!
print(quadratic(0, 0, 1))    # 0
print(quadratic(1, -2, 1))   # 1
print(quadratic(1, -4, 1))   # 2
```

**8. `minX(a, b, c)`** (`a>0`, `b<0`) — the integer `x` minimizing
$ax^2+bx+c$ (smallest such integer if there's a tie).
```python
x0 = int(-b / (2*a))
print(minX(1, -9, 2))  # 4 (not 4.5 or 5)
```

**9. `rock_paper_scissors(first, second)`** — `"First"`/`"Second"`/`"Tie"`.
```python
print(rock_paper_scissors("R","S"))  # First
print(rock_paper_scissors("S","P"))  # First
print(rock_paper_scissors("P","R"))  # First
```

**10. `better(gold1,silver1,bronze1, gold2,silver2,bronze2)`** — which
country wins by Olympic medal-table order (gold first, then silver, then
bronze — not by total count).
```python
print(better(10,4,24, 1,35,25))   # First  (more gold)
print(better(10,18,0, 10,4,24))   # First  (tied gold, more silver)
print(better(10,20,5, 10,20,4))   # First  (tied gold+silver, more bronze)
```

### Optional Problems

**11. `area(x1,y1,l1, x2,y2,l2)`** — area of the intersection of two
axis-aligned squares (centers `(x1,y1)`/`(x2,y2)`, side lengths `l1≥l2`).

**12. `triangular(n)`** — a positive integer `n` is *triangular* if
$n = m(m+1)/2$ for some positive integer `m`. Return that `m`, or `None`.
> Hint: $m(m+1)/2 = n \Rightarrow m^2 < 2n < (m+1)^2 \Rightarrow m < \sqrt{2n} < m+1$.

---
*Source: 2025 offering, `week04_if_else_problem.pdf`. Wording condensed;
code stubs kept close to the original.*
