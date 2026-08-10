# Problem Set

**1.** Write functions `printMultTable1` and `printMultTable2` defined by:
- input parameter: none
- return value: none
- action: print out parts of the multiplication table, as shown below
  - *Copy and slightly modify `printMultTable0` from this week's lecture.*
  - *What does `for i in range(1,10,2):` do? What about the nested
    `for i in range(1,10,2): for j in range(1,i+1):`?*

```python
def printMultTable1():
    # ADD ADDITIONAL CODE HERE!
printMultTable1()
```
Output:
```
1 2 3 4 5 6 7 8 9
3 6 9 12 15 18 21 24 27
5 10 15 20 25 30 35 40 45
7 14 21 28 35 42 49 56 63
9 18 27 36 45 54 63 72 81
```

```python
def printMultTable2():
    # ADD ADDITIONAL CODE HERE!
printMultTable2()
```
Output:
```
1
3 6 9
5 10 15 20 25
7 14 21 28 35 42 49
9 18 27 36 45 54 63 72 81
```

**2.** Write a function `sumNumbers` defined by:
- input parameter: two integers `a` and `b` where `a <= b`
- return value: the sum of integers from `a` to `b`
  - *What does `for i in range(a,b):` do? What about `for i in
    range(a,b+1):`?*

```python
def sumNumbers(a, b):
    total = 0
    # ADD ADDITIONAL CODE HERE!
print(sumNumbers(5, 10))   # 45
print(sumNumbers(15, 100)) # 4945
```

**3.** Write a function `factorial` defined by:
- input parameter: an integer `n`
- return value: \\(n! = 1 \times 2 \times 3 \times \cdots \times (n-1)
  \times n\\)

```python
def factorial(n):
    prod = 1
    # ADD ADDITIONAL CODE HERE!
print(factorial(8))   # 40320
print(factorial(12))  # 479001600
```

**4.** One way to compute \\(e^x\\) is the infinite series
\\(e^x \approx 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} +
\cdots + \frac{x^{100}}{100!}\\) (100 can be replaced by any larger integer
for greater precision).

Write a function `exp` defined by:
- input parameter: a float `x`
- return value: the approximation of \\(e^x\\) computed by the above formula
  - *Copy the `factorial` function from problem 3 here, and make use of it.*

```python
# copy factorial() from problem 3 here, and make use of it
def exp(x):
    total = 1
    # ADD ADDITIONAL CODE HERE!
print(exp(1.0))  # 2.7182818284590455
print(exp(2.0))  # 7.389056098930649
print(exp(4.0))  # 54.598150033144265
```

**5.** Write a function `withinCircle` defined by:
- input parameter: a positive integer `r`
- return value: the number of integer-coordinate points `(x,y)` with
  \\(x^2+y^2 \le r^2\\) (i.e. points within the circle of radius `r`)

```python
def withinCircle(r):
    counter = 0
    for x in range(-r, r+1):
        for y in range(-r, r+1):
            # ADD ADDITIONAL CODE HERE!
    return counter
print(withinCircle(100) / 100**2)    # 3.1417
print(withinCircle(1000) / 1000**2)  # 3.141549
```

**6.** Write a function `dayOfWeek` defined by:
- input parameter: three integers `year, month, day` where `year >= 2000`
- return value: the day of the week for that date, as one of the strings
  `"Mon"`, `"Tue"`, `"Wed"`, `"Thu"`, `"Fri"`, `"Sat"`, `"Sun"`
  - *Make use of `leapYear`/`numDays` from last week. `2000/1/1` was a
    Saturday. Count the number of days elapsed from `2000/1/1` to
    `year/month/day` in three steps — e.g. for `2015/4/13`: (1) days from
    2000 through 2014, (2) days from `2015/Jan` through `2015/Mar`, (3) days
    from `2015/Apr/1` to `2015/Apr/12`.*

```python
def dayOfWeek(year, month, day):
    counter = 0
    # step 1: count the number of days from 2000 to year-1
    # step 2: count the number of days from year/Jan to year/(month-1)
    # step 3: count the days from year/month/1 to year/month/(day-1)
    n = counter % 7
    if n == 0:
        return "Sat"
    # step 4: complete the code for the other cases
print(dayOfWeek(2001, 1, 28))  # Sun
print(dayOfWeek(2002, 11, 21)) # Thu
print(dayOfWeek(2004, 3, 4))   # Thu
print(dayOfWeek(2008, 7, 1))   # Tue
print(dayOfWeek(2011, 5, 8))   # Sun
print(dayOfWeek(2013, 3, 23))  # Sat
```

**7.** Let \\(f: \{0,1,\ldots,99\}^2 \to \mathbb{Z}\\) be defined by
\\(f(i,j) = (i^5 + 2i^3j^2 + 5i^2 + j + 5000) \bmod 10000\\).

Write a function `findMax` defined by:
- input parameter: none
- return value: the maximum value of `f` defined above

```python
def f(i, j):
    return (i**5 + 2*(i**3)*(j**2) + 5*i**2 + j + 5000) % 10000
def findMax():
    best = f(0, 0)
    for i in range(100):
        for j in range(100):
            # ADD ADDITIONAL CODE HERE!
    return best
print("max value:", findMax())  # 9997
```

**8.** Write a function `combination` defined by:
- input parameter: two integers `n` and `k` with `1 <= k <= n <= 250`
- return value: the number of ways to choose `k` from a set of `n`
  (\\(\binom{n}{k}\\)), as an `int` (not `float`)
  - *Use the formula \\(\prod_{i=1}^{k} \frac{n+1-i}{i} = \frac{n}{1} \cdot
    \frac{n-1}{2} \cdot \frac{n-2}{3} \cdots \frac{n+2-k}{k-1} \cdot
    \frac{n+1-k}{k}\\).*

**9.** Write a function `maxPrimeFactor` defined by:
- input parameter: an integer `n >= 2`
- return value: the largest prime factor of `n` — e.g. `maxPrimeFactor(12)`
  returns `3`, since `12 = 2×2×3`
  - *Use an `isPrime` function to check primality.*

**10.** Write a function `withinRegion` defined by:
- input parameter: two positive integers `a, c`
- return value: the number of integer-coordinate points `(x,y)` that satisfy
  both \\(y \le -ax^2+c\\) and \\(y \ge ax^2-c\\) (points within the region
  bounded by the two parabolas)
