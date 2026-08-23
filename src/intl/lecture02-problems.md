# Problem Set


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture02.ipynb)

*Use interactive mode (the Python shell) whenever a formula isn't clear.*

**1.** Write a function `f` defined by:
- input parameter: two positive integers `x, y`
- return value: the float value \\(\frac{x}{2y}\\)

```python
def f(x, y):
    # ADD ADDITIONAL CODE HERE!

print(f(1, 2))  # 0.25
print(f(3, 6))  # 0.25
```

**2.** Write a function `f` defined by:
- input parameter: two positive integers `x, y`
- return value: the float value \\(x^{1/y}\\)

```python
print(f(16, 4))  # 2.0
print(f(64, 6))  # 2.0
```

**3.** Write functions `f` and `g` defined by:
- \\(f(x) = e^{-x} + \sin(\pi\sqrt{1+x^2})\\)
  - use `math.exp(t)` to compute \\(e^t\\)
  - use `math.sin(t)` to compute \\(\sin(t)\\)
  - use `math.sqrt(t)` or `t**0.5` to compute \\(\sqrt{t}\\)
  - use `math.pi` to represent \\(\pi\\)
- \\(g(x,y) = \left(1+f\left(y^{1/x}\right)\right)^{f\left(y^{1/x}\right)}\\)
  - first, write code for `z = f(y**(1/x))`
  - then, write code to `return (1+z)**z`

```python
import math

def f(x):
    # ADD ADDITIONAL CODE HERE!

def g(x, y):
    # ADD ADDITIONAL CODE HERE!

print(f(2), f(3))    # 0.8108255774981366 -0.43822461448665007
print(g(2,3), g(3,5)) # 1.0292401354314726 1.0139040096665841
```

**4.** Write a function `force` defined by:
- input parameter: three positive float values `m1, m2, r` — where `m1` and
  `m2` represent the mass of two objects, and `r` the distance between them
- return value: the gravitational force between the two objects,
  \\(F = G \cdot \frac{m_1 m_2}{r^2}\\) where \\(G = 6.67 \times 10^{-11}\\)

```python
def force(m1, m2, r):
    G = 6.67 * 10**(-11)
    # ADD ADDITIONAL CODE HERE!

print(force(1.5, 1.6, 100.5))  # 1.5849112645726593e-14
```

**5.** Write a function `minValue` defined by:
- input parameter: three integers `a, b, c` where `a > 0`
- return value: the minimum value of \\(f(x) = ax^2+bx+c\\)
  - first, write code for \\(x_0 = \frac{-b}{2a}\\)
  - then, write code to `return f(x0)`

```python
def f(a, b, c, x):
    return a*x**2 + b*x + c

def minValue(a, b, c):
    # ADD ADDITIONAL CODE HERE!

print(minValue(1, 5, 10))   # 3.75
print(minValue(1, -5, 10))  # 3.75
print(minValue(3, 7, 5))    # 0.9166666666666661
```

**6.** Write a function `reverse` defined by:
- input parameter: an integer `n` where `1000 <= n <= 9999` (a 4-digit
  integer)
- return value: the integer formed by reversing the digits of `n`
  - e.g. `reverse(3712)` returns `2173`, and `reverse(3710)` returns `173`.
  - *What is the value of `n % 10`? Of `(n // 10) % 10`? Of `(n // 100) % 10`?
    Of `n // 1000`?*

```python
# ADD FUNCTION HERE!

print(reverse(3702))  # 2073
print(reverse(3710))  # 173
print(reverse(3700))  # 73
```

**7.** What is the fewest number of Korean coins needed to make 730 Korean
won? The answer is 6.

Write a function `countCoins` defined by:
- input parameter: an integer `n` where `10 <= n <= 990` and `n` is a
  multiple of 10
- return value: the fewest number of Korean coins (10, 50, 100, 500 won)
  needed to make `n` Korean won
  - e.g. `countCoins(730)` returns `6`.

```python
# ADD FUNCTION HERE!

print(countCoins(730))  # 6
print(countCoins(790))  # 8
print(countCoins(260))  # 4
print(countCoins(70))   # 3
```
