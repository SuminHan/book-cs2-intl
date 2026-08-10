# Topics Covered

## Why `for` Loops

Computing `1 + 2 + ... + n` without a loop means writing one line per
term — it doesn't even work unless you already know `n` in advance:

```python
def sumTo(n):
    total = 0
    total = total + 1
    total = total + 2
    ...                  # can't write this for a variable n!
```

A `for` loop repeats a block once per value in a range:

```python
def sumTo(n):
    total = 0
    for i in range(1, n+1):   # i = 1, 2, ..., n
        total = total + i
    return total
```

## `for` Loops with `range(·)`

`range` has three forms:

```python
for k in range(n):          # 0, 1, ..., n-1
for k in range(m, n):       # m, m+1, ..., n-1
for k in range(m, n, k):    # m, m+k, m+2k, ... (stops before n)
```

`range(n)` is shorthand for `range(0, n, 1)`; `range(m, n)` is shorthand for
`range(m, n, 1)`. A negative step counts down:

```python
for k in range(n, 0, -1):
    print(k)      # n, n-1, ..., 1
```

Whichever form, the loop is equivalent to writing out the body once per
value the range produces, in order — that mental model (unrolling the
loop) is the way to check you picked the right range.

## Increment/Decrement Shortcuts

```python
x += y   # x = x + y
x -= y   # x = x - y
x *= y   # x = x * y
x /= y   # x = x / y
x //= y  # x = x // y
```

```python
total, product = 0, 1
for k in range(1, n+1):
    total += k     # running sum
    product *= k   # running product
```

## Loop + Conditional

A loop body can contain an `if`, applying different logic per iteration:

```python
for k in range(1, 11):
    if k % 2 == 0:
        print(k, "is even")
    else:
        print(k, "is odd")
```

## Nested Loops

A loop body can itself contain another loop — the inner loop runs to
completion for *every* iteration of the outer one. Printing a
multiplication table is the canonical example:

```python
for i in range(1, 10):
    for j in range(1, 10):
        print(i*j, end=" ")
    print()      # newline after each row
```

## Pattern: Find Max/Min Over a Range

Track a running best value, and update it whenever you see something
better. Initialize it with the *first* value the loop will consider (here
`f(0)`), not an arbitrary constant like `0` — that only works by luck if
every `f(i)` happens to be non-negative.

```python
def f(i):
    return (i**5 + 2*i**3 + 7*i**2 + i + 500) % 1000

def findMax():
    best = f(0)
    for i in range(100):
        if f(i) > best:
            best = f(i)
    return best
```

(`findMin` is the same pattern with `<` instead of `>`.) This "running
best" pattern will come back constantly for the rest of the course — get
comfortable with it now.
