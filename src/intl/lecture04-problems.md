# Problem Set

**1.** Write a function `inSecondQuadrant` defined by:
- input parameter: two integers `x, y`
- return value: a boolean — `True` if the point `(x,y)` is in the second
  quadrant, `False` otherwise
  - *Do not return `"True"`/`"False"` — those are strings, not booleans.*

```python
def inSecondQuadrant(x, y):
    # ADD ADDITIONAL CODE HERE!

print(type(inSecondQuadrant(0, 0)))  # <class 'bool'>
print(inSecondQuadrant(-1, 2))   # True
print(inSecondQuadrant(-1, -2))  # False
print(inSecondQuadrant(1, -2))   # False
print(inSecondQuadrant(-1, 0))   # False
```

Using `inSecondQuadrant` above, write a function `exactlyTwoSecondQuadrant`
defined by:
- input parameter: six integers `x1,y1,x2,y2,x3,y3` — `(x1,y1)`, `(x2,y2)`,
  `(x3,y3)` represent three points in the plane
- return value: a boolean — `True` if exactly two of the three points are in
  the second quadrant, `False` otherwise

```python
def exactlyTwoSecondQuadrant(x1, y1, x2, y2, x3, y3):
    counter = 0
    if inSecondQuadrant(x1, y1):
        counter = counter + 1
    # ADD ADDITIONAL CODE HERE!

    return (counter == 2)

print(exactlyTwoSecondQuadrant(-1,2, 2,1, -2,1))  # True
print(exactlyTwoSecondQuadrant(1,2, -2,1, -3,3))  # True
print(exactlyTwoSecondQuadrant(1,2, -2,-1, -2,1)) # False
print(exactlyTwoSecondQuadrant(-1,2, -2,1, -2,2)) # False
```

**2.** Write a function `withinInterval` defined by:
- input parameter: three integers `lower, upper, n` (where `lower <= upper`)
- return value: a boolean — `True` if `lower <= n <= upper`, `False`
  otherwise

```python
def withinInterval(lower, upper, n):
    # ADD ADDITIONAL CODE HERE!

print(type(withinInterval(1, 5, 0)))  # <class 'bool'>
print(withinInterval(1, 5, 0))  # False
print(withinInterval(1, 5, 1))  # True
print(withinInterval(1, 5, 3))  # True
print(withinInterval(1, 5, 5))  # True
print(withinInterval(1, 5, 6))  # False
```

Using `withinInterval` above, write a function `exactlyThreeWithinInterval`
defined by:
- input parameter: seven integers `lower, upper, n1,n2,n3,n4,n5` —
  `[lower,upper]` represents an interval
- return value: a boolean — `True` if exactly three of `n1,n2,n3,n4,n5` fall
  within the interval, `False` otherwise

```python
def exactlyThreeWithinInterval(lower, upper, n1, n2, n3, n4, n5):
    counter = 0
    if withinInterval(lower, upper, n1):
        counter = counter + 1
    # ADD ADDITIONAL CODE HERE!

print(exactlyThreeWithinInterval(1,5, 1,0,6,5,3))  # True
print(exactlyThreeWithinInterval(1,5, 6,1,0,3,5))  # True
print(exactlyThreeWithinInterval(1,5, 6,1,0,7,2))  # False
print(exactlyThreeWithinInterval(1,5, 6,7,0,1,2))  # False
```

**3.** Write a function `triangle` defined by:
- input parameter: two integers `a, b`
- return value: a boolean — `True` if the x-axis, the y-axis, and the line
  `y = ax+b` together form a triangle in the plane, `False` otherwise

```python
# ADD FUNCTION HERE!

print(triangle(-3, -2))  # True
print(triangle(3, 0))    # False
print(triangle(0, 2))    # False
print(triangle(0, 0))    # False
```

**4.** Write a function `triangle` defined by:
- input parameter: three positive integers `a, b, c`
- return value: a boolean — `True` if a triangle with side lengths `a,b,c`
  can be formed, `False` otherwise
  - *If a triangle exists, `a+b>c` and `b+c>a` and `c+a>b` all hold. What
    about the converse?*

```python
# ADD FUNCTION HERE!

print(triangle(3, 4, 5))  # True
print(triangle(1, 5, 2))  # False
print(triangle(3, 1, 1))  # False
```

**5.** Write a function `rightAngled` defined by:
- input parameter: six integers `x1,y1,x2,y2,x3,y3` — `(x1,y1)`, `(x2,y2)`,
  `(x3,y3)` represent three points in the plane
- return value: a boolean — `True` if the three points form a right-angled
  triangle, `False` otherwise

```python
def rightAngled(x1, y1, x2, y2, x3, y3):
    a = (x2-x1)**2 + (y2-y1)**2
    b = (x3-x2)**2 + (y3-y2)**2
    c = (x1-x3)**2 + (y1-y3)**2
    # ADD ADDITIONAL CODE HERE!

print(rightAngled(1, 1, 5, 2, -1, 9))  # True
print(rightAngled(1, 2, 4, 2, 5, 4))   # False
print(rightAngled(1, 2, 4, 2, 4, 3))   # True
```

**6.** Write a function `acuteAngled` defined by:
- input parameter: six integers `x1,y1,x2,y2,x3,y3` — `(x1,y1)`, `(x2,y2)`,
  `(x3,y3)` represent three points in the plane
- return value: a boolean — `True` if the three points form an acute-angled
  triangle, `False` otherwise

```python
# ADD FUNCTION HERE!

print(acuteAngled(1, 2, 4, 3, 2, 7))  # True
print(acuteAngled(1, 2, 4, 2, 5, 4))  # False
print(acuteAngled(1, 2, 4, 2, 4, 3))  # False
```

**7.** Write a function `intersect` defined by:
- input parameter: six integers `x1,y1,r1,x2,y2,r2`, where `x1,y1,r1`
  represent a circle centered at `(x1,y1)` with radius `r1`, and `x2,y2,r2`
  represent another circle centered at `(x2,y2)` with radius `r2`
- return value: a boolean — `True` if the two circles intersect at two
  points, `False` otherwise
  - *Use `abs(x)` to compute the absolute value \\(|x|\\).*

```python
# ADD FUNCTION HERE!

print(intersect(1, 1, 3, 5, 4, 2))  # False
print(intersect(1, 1, 3, 4, 3, 2))  # True
print(intersect(1, 1, 3, 2, 1, 2))  # False
```

**8.** Write a function `leapYear` defined by:
- input parameter: a positive integer `year`
- return value: a boolean — `True` if `year` is a leap year, `False`
  otherwise
  - Basically, leap years occur in years divisible by 4 (2009-2011 are not
    leap years, while 2008 and 2012 are).
  - Years ending in `00` are leap years only if divisible by 400 (1700,
    1800, 1900, 2100, 2200 are not leap years; 1600, 2000, 2400 are).

```python
def leapYear(year):
    if year % 4 != 0:
        return False
    # now, year is divisible by 4
    # ADD ADDITIONAL CODE HERE!

print(leapYear(2008), leapYear(2011), leapYear(2012))  # True False True
print(leapYear(2000), leapYear(2100), leapYear(2200))  # True False False
print(leapYear(2300), leapYear(2400), leapYear(3200))  # False True True
```

Using `leapYear` above, write a function `numDays` defined by:
- input parameter: two positive integers `year, month`
- return value: the number of days in that year and month

```python
def numDays(year, month):
    assert (1 <= month <= 12)
    if month == 1 or month == 3 or month == 5 or month == 7 or \
       month == 8 or month == 10 or month == 12:
        return 31
    # ADD ADDITIONAL CODE HERE!

print(numDays(2000,1), numDays(2001,4), numDays(2004,8))  # 31 30 31
print(numDays(2004,9), numDays(2005,3), numDays(2005,7))  # 30 31 31
print(numDays(2008,2), numDays(2011,2), numDays(2012,2))  # 29 28 29
print(numDays(2000,2), numDays(2100,2), numDays(2200,2))  # 29 28 28
print(numDays(2300,2), numDays(2400,2), numDays(3200,2))  # 28 29 29
```

**9.** Big hospitals are always ready for emergency medical treatment, which
often requires blood transfusions. Consider the problem faced by a hospital
trying to determine whether its blood supply is sufficient.

The basic rule for blood donation (ABO type only, ignoring Rh type for
simplicity):
- Patients with type O can receive only blood type O.
- Patients with type A can receive only blood types A or O.
- Patients with type B can receive only blood types B or O.
- Patients with type AB can receive any of the four types.

Write a function `blood` defined by:
- input parameter: eight integers — `supplyO,supplyA,supplyB,supplyAB` (the
  current supply of each blood type) and `demandO,demandA,demandB,demandAB`
  (the current demand)
- return value: a boolean — `True` if the current supply suffices for the
  current demand, `False` otherwise
  - *Hint: the supply does **not** suffice if any of these hold:*
    `supplyO < demandO`; `supplyO+supplyA < demandO+demandA`;
    `supplyO+supplyB < demandO+demandB`;
    `supplyO+supplyA+supplyB < demandO+demandA+demandB`;
    `supplyO+supplyA+supplyB+supplyAB < demandO+demandA+demandB+demandAB`.
    *What about the converse?*

```python
def blood(supplyO, supplyA, supplyB, supplyAB,
          demandO, demandA, demandB, demandAB):
    if supplyO < demandO:
        return False
    # ADD ADDITIONAL CODE HERE!

print(blood(50, 36, 11, 8, 45, 42, 10, 3))  # False
print(blood(50, 36, 11, 3, 45, 38, 10, 7))  # True
```
