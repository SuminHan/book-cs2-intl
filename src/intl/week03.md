# Functions

## 2.1. Opener: A Function You Did Not Write

A function takes something in and gives something back. Usually that is
exactly what you want.

Biologists study a gene called `SEPT2`. Another is called `MARCH1`. They
typed those names into Excel. Excel has a helpful little function that
looks at what you typed and decides what you *meant*. What do you think it did?

**It turned genes into dates:**

```
SEPT2   ->   2-Sep
MARCH1  ->   1-Mar
```

Nobody asked for this. Nobody was warned. The gene names were simply gone,
and once saved they are very hard to get back.

A 2016 study checked 35,175 spreadsheets from 3,597 published papers: about
one paper in five carried these corrupted names. A follow-up covering
2014–2020 found over 30%.

> Sources: Ziemann et al., *Genome Biology* (2016); Abeysooriya et al.,
> *PLOS Computational Biology* (2021).

### The lesson for this week

When you call a function, you are trusting it to do exactly one thing — the
thing its name says.

Excel's autocorrect was doing its job perfectly. It was just doing a
different job than the biologists thought it was doing.

**When you write a function this week, ask: could someone read the name and
expect something else?**

## 2.2. Topics Covered

- Indentation
- Built-in functions
- User-defined functions
- Parameters & arguments

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## 2.3. Problem Set

*Use interactive mode (the Python shell) whenever a formula isn't clear.*

**1. `f(x, y) = x / (2y)`**
```python
def f(x, y):
    # ADD ADDITIONAL CODE HERE!
print(f(1, 2))  # 0.25
print(f(3, 6))  # 0.25
```

**2. `f(x, y) = x^(1/y)`**
```python
print(f(16, 4))  # 2.0
print(f(64, 6))  # 2.0
```

**3. `f(x)` and `g(x, y)`** — $f(x) = e^{-x} + \sin(\pi\sqrt{1+x^2})$, using
`math.exp`, `math.sin`, `math.sqrt` (or `**0.5`), `math.pi`.

```python
import math
def f(x):
    # ADD ADDITIONAL CODE HERE!
def g(x, y):
    # ADD ADDITIONAL CODE HERE!
print(f(2), f(3))    # 0.8108255774981366 -0.43822461448665007
print(g(2,3), g(3,5)) # 1.0292401354314726 1.0139040096665841
```
> The definition of `g` involves a nested fraction that didn't survive PDF
> text extraction cleanly — check the original PDF for the exact formula;
> the hint structure is "compute `z = f(1/x)` (or similar), then return
> `(1+z)**z`".

**4. `force(m1, m2, r)`** — gravitational force between two masses:
$F = G \cdot \frac{m_1 m_2}{r^2}$ where $G = 6.67 \times 10^{-11}$.
```python
def force(m1, m2, r):
    G = 6.67 * 10**(-11)
    # ADD ADDITIONAL CODE HERE!
print(force(1.5, 1.6, 100.5))  # 1.5849112645726593e-14
```

**5. `minValue(a, b, c)`** — minimum value of $f(x) = ax^2+bx+c$ (for $a>0$),
found via the vertex $x_0 = \frac{-b}{2a}$.
```python
def f(a, b, c, x):
    return a*x**2 + b*x + c
def minValue(a, b, c):
    # ADD ADDITIONAL CODE HERE!
print(minValue(1, 5, 10))   # 3.75
print(minValue(1, -5, 10))  # 3.75
print(minValue(3, 7, 5))    # 0.9166666666666661
```

**6. `reverse(n)`** — reverse the digits of a 4-digit integer `n`.
```python
print(reverse(3702))  # 2073
print(reverse(3710))  # 173
print(reverse(3700))  # 73
```
> `n % 10`, `(n // 10) % 10`, `(n // 100) % 10`, `n // 1000` give you each
> digit.

**7. `countCoins(n)`** — fewest Korean coins (10, 50, 100, 500 won) that add
up to `n` won (`10 ≤ n ≤ 990`, multiple of 10). E.g. `countCoins(730)` → `6`.
```python
print(countCoins(790))  # 8
print(countCoins(260))  # 4
print(countCoins(70))   # 3
```

---
*Source: 2025 offering, `week03_func_problem.pdf`. Wording condensed; code
stubs kept close to the original.*
