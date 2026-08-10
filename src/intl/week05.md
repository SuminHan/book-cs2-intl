# Boolean Functions

## 4.1. Opener: This Looks Completely Reasonable

You want to check whether `x` is 1 or 2. In English that is one short
sentence, so you write it the way you say it:

```python
x = 5
print(x == 1 or 2)
```

`x` is 5. So this prints `False` — right?

**It prints `2`.**

Python read it as `(x == 1) or 2`:

- `x == 1` is `False`
- so `or` moves on and hands back `2`
- and `2` counts as true

So inside an `if`, this condition is true for every value of `x` — 5, 99,
anything.

### Say it twice

`or` joins two complete comparisons, not one comparison and a leftover number.

```python
# Correct
print(x == 1 or x == 2)     # False
```

**Why this one is dangerous:** it never crashes. It never warns you. It
just quietly says yes to everything — and an `if` that is always true looks
exactly like an `if` that works.

## 4.2. Topics Covered

- Defining & using boolean functions
- Common mistake: returning the strings `"True"`/`"False"` instead of the
  boolean values `True`/`False`

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*

## 4.3. Problem Set

**1. `inSecondQuadrant(x, y)` / `exactlyTwoSecondQuadrant(...)`** — the
first checks if `(x,y)` is in the second quadrant (returns an actual `bool`,
not the string `"True"`/`"False"`); the second uses it to check whether
exactly two of three given points are in the second quadrant.
```python
print(type(inSecondQuadrant(0,0)))  # <class 'bool'>
print(inSecondQuadrant(-1,2))       # True
```

**2. `withinInterval(lower, upper, n)` / `exactlyThreeWithinInterval(...)`**
— first checks `lower <= n <= upper`; second uses it to check whether
exactly three of five numbers fall within `[lower,upper]`.

**3. `triangle(a, b)`** — do the x-axis, y-axis, and the line $y=ax+b$ form
a triangle?
```python
print(triangle(-3, -2))  # True
print(triangle(3, 0))    # False (passes through origin)
```

**4. `triangle(a, b, c)`** (different signature) — can side lengths `a, b, c`
form a triangle?
> If a triangle exists, $a+b>c$, $b+c>a$, $c+a>b$ all hold. Does the converse
> hold too?

**5. `rightAngled(x1,y1, x2,y2, x3,y3)`** — do three points form a
right triangle?
```python
def rightAngled(x1, y1, x2, y2, x3, y3):
    a = (x2-x1)**2 + (y2-y1)**2
    b = (x3-x2)**2 + (y3-y2)**2
    c = (x1-x3)**2 + (y1-y3)**2
    # ADD ADDITIONAL CODE HERE!
```

**6. `acuteAngled(x1,y1, x2,y2, x3,y3)`** — do three points form an
acute triangle?

**7. `intersect(x1,y1,r1, x2,y2,r2)`** — do two circles intersect at exactly
two points?
> Use `abs(x)` for $|x|$.

**8. `leapYear(year)` / `numDays(year, month)`** — the leap-year rule from
Week 1 (divisible by 4, except centuries, unless divisible by 400), then use
it to compute the number of days in a given month.
```python
def leapYear(year):
    if year % 4 != 0:
        return False
    # year is divisible by 4
    # ADD ADDITIONAL CODE HERE!
print(leapYear(2000), leapYear(2100), leapYear(2200))  # True False False

def numDays(year, month):
    assert 1 <= month <= 12
    if month in (1,3,5,7,8,10,12):
        return 31
    # ADD ADDITIONAL CODE HERE!
print(numDays(2008,2), numDays(2011,2), numDays(2012,2))  # 29 28 29
```

**9. `blood(supplyO,supplyA,supplyB,supplyAB, demandO,demandA,demandB,demandAB)`**
— given blood-type supply/demand (O can only receive O; A can receive A/O; B
can receive B/O; AB can receive any), does supply cover demand?
```python
def blood(supplyO, supplyA, supplyB, supplyAB,
          demandO, demandA, demandB, demandAB):
    if supplyO < demandO:
        return False
    # ADD ADDITIONAL CODE HERE!
print(blood(50, 36, 11, 8, 45, 42, 10, 3))  # False
print(blood(50, 36, 11, 3, 45, 38, 10, 7))  # True
```
> Hint: check the four cumulative inequalities (`O`, `O+A`, `O+B`,
> `O+A+B`, `O+A+B+AB` supply vs. matching demand). Is the converse also true?

---
*Source: 2025 offering, `week05_bool_func_problem.pdf`. Wording condensed;
code stubs kept close to the original.*
