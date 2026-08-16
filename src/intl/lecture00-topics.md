# Topics Covered

## Functions

Most of the time you'll write functions that `return` a value:

```python
def distance(x1,y1,x2,y2):
    u, v = (x2-x1)**2, (y2-y1)**2
    return math.sqrt(u+v)

print(distance(0,0,3,4))    # prints 5
```

Sometimes a function has no return value — it just `print`s from inside
the function instead. If a function never hits a `return`, it returns
`None` automatically:

```python
def distance(x1,y1,x2,y2):
    u, v = (x2-x1)**2, (y2-y1)**2
    print(math.sqrt(u+v))    # prints 5 here

distance(0,0,3,4)             # no return value
print(distance(0,0,3,4))      # prints None
```

## Conditionals

**`if`-`else` syntax** — the `else` block is optional:

```python
def f(x,y):
    if x > 0:
        print("positive")
    else:
        print("zero/negative")

    if x > 0 and y > 0:
        print("both positive")
```

**Chained `if`-`elif`-`else`**: `elif b2` runs when `b1` is `False` and `b2`
is `True`; the next `elif b3` runs when neither `b1` nor `b2` held but `b3`
does — only the first matching branch, top to bottom, runs.

```python
def f(x):
    if x > 0:
        print("positive")
    elif x < 0:
        print("negative")
    else:
        print("zero")
```

**Nested vs. flat (pruning)**: a nested `if` can often be flattened by
"pruning" — the two forms below are equivalent:

```python
def absoluteValue(x):
    if x < 0:
        return -x
    else:
        return x

# equivalent: if the else-block is the only thing left, the else itself
# can be dropped
def absoluteValue(x):
    if x < 0:
        return -x
    return x
```

**Boolean functions** — useful for hiding a complicated test inside an
`if`:

```python
def onePositive(x,y,z):
    if x > 0 and y <= 0 and z <= 0:
        return True
    if x <= 0 and y > 0 and z <= 0:
        return True
    if x <= 0 and y <= 0 and z > 0:
        return True
    return False

if onePositive(x,y,z):
    print("Exactly one number is positive.")
```

A boolean expression is already a value, so `if ...: return True / else:
return False` collapses to `return boolean_expr`:

```python
def lessThan(x,y):
    if x < y:
        return True
    else:
        return False

# equivalent
def lessThan(x,y):
    return x < y
```

For the same reason, `b == True` is just `b`, and `b == False` is `not b`
— drop `== True`/`== False` (it also protects you from typing `=` when you
meant `==`):

```python
def singleDigit(x):
    return 0 <= x < 10

# instead of singleDigit(a) == True and singleDigit(b) == False
if singleDigit(a) and not singleDigit(b):
    ...
```

## Loops

**`for` with `range(·)`**: `range(m,n)` is short for `range(m,n,1)`, and
`range(n)` is short for `range(0,n,1)`.

```python
for k in range(n):
    print(k)              # 0 1 ... n-1

for k in range(1, n+1):
    print(k)              # 1 2 ... n

for k in range(10, 21, 2):
    print(k)              # 10 12 14 16 18 20

for k in range(n, 0, -1):
    print(k)              # n n-1 ... 2 1
```

**Accumulating a sum or product**:

```python
def sum(n):
    x = 0          # identity element for addition is 0
    for i in range(1,n+1):
        x += i
    return x

def factorial(n):
    x = 1          # identity element for multiplication is 1
    for i in range(1,n+1):
        x *= i
    return x
```

**Nested `for` loops** build 2-D output, like a multiplication table:

```python
for i in range(1, 10):
    for j in range(1, 10):
        print(i*j, end=" ")
    print()
```

**`while` loops** repeat as long as a boolean expression holds:

```python
def countDigits(n):
    counter = 0
    while n > 0:
        counter += 1
        n = n // 10
    return counter

print(countDigits(713))   # 3
```

## Lists

**Creating a list**: either with initial values, or with `[None]*n` to
reserve empty slots to fill in later.

```python
number = [2, 5, 8, 11, 14]

number = [None] * 5   # [None, None, None, None, None]
number[0] = 2
```

**Reading/writing with `len(·)` and `[i]`**: indices run from `0` to
`len(·)-1` (not starting at `1`).

```python
for i in range(len(number)):
    number[i] = 3*i + 2
```

**Lists as function input/output**:

```python
def func(b):
    a = [None] * len(b)
    for i in range(len(a)):
        a[i] = b[i] + 1
    return a

num = [2, 4, 3, 1, 7, 2, 5, 6]
c = func(num)
print(c)    # [3, 5, 4, 2, 8, 3, 6, 7]
```

## Loop Patterns

Most `for` loops you'll write are some combination of the patterns below.

**1. Minimum/maximum pattern** — you may need the **index** of the extreme
value, not just the value itself:

```python
def findMin(numbers):
    min = numbers[0]
    for i in range(len(numbers)):
        if numbers[i] < min:
            min = numbers[i]
    return min

def findMinIndex(numbers):
    minIndex = 0
    for i in range(len(numbers)):
        if numbers[i] < numbers[minIndex]:
            minIndex = i
    return minIndex
```

**2. Counter pattern** — count how many elements satisfy some condition:

```python
def countPrime(numbers):
    counter = 0
    for i in range(len(numbers)):
        if isPrime(numbers[i]):    # boolean function
            counter += 1
    return counter
```

**3. Quantifier pattern ("for some" / "for all")** — by De Morgan's laws,
\\(\forall x, p(x) \equiv \neg(\exists x, \neg p(x))\\), so "for all" can
be built as the negation of "for some":

```python
def somePositive(numbers):
    for i in range(len(numbers)):
        if numbers[i] > 0:
            return True
    return False

def allPositive(numbers):
    for i in range(len(numbers)):
        if not (numbers[i] > 0):   # numbers[i] <= 0
            return False
    return True
```

A "for all" pattern you'll see a lot this semester is primality testing
("`p` is prime" ≡ "`p%i != 0` for all `i`"):

```python
def isPrime(p):
    if p < 2:
        return False
    for i in range(2, p//2+1):
        if not (p%i != 0):    # p%i == 0
            return False
    return True
```
