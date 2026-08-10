# Topics Covered

## Indentation

The body of a function (and later, of `if`/`for`/`while`) is marked purely
by **indentation** — there are no `{ }` or `end` keywords. Use Tab (not the
space bar) to indent consistently.

```python
def distance(x1, y1, x2, y2):
    u = (x2-x1)**2
    v = (y2-y1)**2
    return math.sqrt(u+v)
```

Nested structure is represented by *nested* indentation, and different
indentation gives a genuinely different program — these two are not the
same function:

```python
def walk_9_by_9():
    for j in range(4):
        for i in range(9):
            hubo.move()
        hubo.turn_left()

def walk_1_by_1_9_times():
    for j in range(4):
        for i in range(9):
            hubo.move()
            hubo.turn_left()
```

## Built-in Functions

Python ships built-in functions for the common math functions: `math.sqrt`,
the trig family (`math.sin`, `math.cos`, `math.tan`, `math.asin`, ...),
`math.exp`, `math.log`, and more (`import math` first).

```python
a = math.sqrt(17)
b = math.sin(60 * math.pi / 180)
c = math.log(20 * b)
d = math.cos(b * math.cos(a + math.sqrt(c+1)) - 2)
```

A long composed expression like `d` above is exactly the case for
**decomposition** (see Week 2): split it into named steps.

```python
x1 = a + math.sqrt(c+1)
x2 = b * math.cos(x1) - 2
d = math.cos(x2)
```

## User-Defined Functions

`math.sqrt` is built in; you can define your own functions the same
way — either returning a value, or just doing something (printing,
say) without returning one:

```python
def distance(x1, y1, x2, y2):     # returns a value
    u = (x2-x1)**2
    v = (y2-y1)**2
    return math.sqrt(u+v)

def printCircleArea(radius):      # no return — just prints
    print(math.pi * radius**2)
```

**Define functions first, then write the code that calls them** — the
order the `def`s appear in the file doesn't affect what they compute, but a
function has to already be defined by the time you call it:

```python
def circleArea(radius):
    return math.pi * radius**2

def distance(x1, y1, x2, y2):
    u = (x2-x1)**2
    v = (y2-y1)**2
    return math.sqrt(u+v)

a = circleArea(10)
b = distance(0, 0, 3, 4)
```

A common pattern is to wrap all the "main" calls in one `startFromHere()`
function and call that last, so the file reads top-to-bottom as
*definitions, then the program*:

```python
def startFromHere():
    a = circleArea(10)
    b = distance(0, 0, 3, 4)
    printCircleArea(10)

startFromHere()
```

## Parameters & Arguments

A **parameter** is the variable name a function receives its input through;
an **argument** is the actual value passed in at the call site.

```python
def circleArea(radius):     # radius: parameter
    return math.pi * radius**2

a = circleArea(10)          # 10: argument — copied into radius
```

The argument variable's name (if it even has one) has nothing to do with
the parameter's name — only the *value* is passed:

```python
def circleArea(x):
    return math.pi * x**2

x = 10
circleArea(x)     # this call passes the value 10, not "the variable x"
```

A function can call another function, and can call itself... indirectly —
you'll see recursion later. For now: each function has its own local
variables (its parameters, plus anything it assigns inside its body) —
a variable named `y` inside one function is unrelated to a variable
named `y` inside another, or at the top level.
