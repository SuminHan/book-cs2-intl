# Topics Covered

## Boolean Functions

A **boolean function** is one that returns `True`/`False` — useful for
hiding a complicated yes/no test behind a readable name, so the calling
code can just write `if onePositive(x, y, z):` instead of repeating the
whole condition inline. Whenever you're facing a yes/no question, consider
writing it as its own boolean function.

```python
def onePositive(x, y, z):
    if x > 0 and y <= 0 and z <= 0:
        return True
    if x <= 0 and y > 0 and z <= 0:
        return True
    if x <= 0 and y <= 0 and z > 0:
        return True
    return False
```

## Common Mistake: String `"True"` / `"False"`

`"True"` and `"False"` (the strings) are *not* the same as `True` and
`False` (the boolean values) — and a non-empty string is always truthy, so
this bug won't crash, it just silently always takes the `if` branch:

```python
# WRONG — returns the strings "True"/"False"
def lessThan(x, y):
    if x < y:
        return "True"
    else:
        return "False"

if lessThan(a, b):   # always runs — "False" is a non-empty string!
    ...
```

```python
# correct
def lessThan(x, y):
    if x < y:
        return True
    else:
        return False
```

## Tip: Return the Boolean Expression Directly

If your function's job is exactly "is this condition true," skip the
`if`/`else` and return the condition itself:

```python
def lessThan(x, y):
    return x < y          # x < y already IS True or False
```

The same shortcut applies to negation:

```python
# if boolean_expr: return False   else: return True
# becomes:
return not boolean_expr
```

## Tip: Drop `== True` / Replace `== False` with `not`

`b == True` is just `b`; `b == False` is `not b`:

```python
if singleDigit(a) == True and singleDigit(b) == False:
    ...
# becomes:
if singleDigit(a) and not singleDigit(b):
    ...
```

Watch for the classic typo — `=` (assignment) where you meant `==`
(comparison). `if singleDigit(a) = True:` is not valid boolean logic at
all.

## Tip: Decompose Complicated Boolean Expressions

The same decomposition advice from Week 2 applies to conditions, maybe even
more so — a condition repeated three times with permuted variables is easy
to get wrong in one of the copies:

```python
a = (x2-x1)**2 + (y2-y1)**2
b = (x3-x2)**2 + (y3-y2)**2
c = (x1-x3)**2 + (y1-y3)**2
if a+b == c or b+c == a or a+c == b:
    ...
```

## Tip: Never `==` on `float`

```python
print(0.1 + 0.2)          # 0.30000000000000004
print(0.1 + 0.2 == 0.3)   # False
print((111**0.5)**2)        # 110.99999999999999
print((111**0.5)**2 == 111) # False
```

`==` on floats is unreliable because of how binary floating point rounds.
When possible, restructure the comparison to stay in integers rather than
comparing floats at all:

```python
# unreliable: comparing floats
d = ((x2-x1)**2 + (y2-y1)**2)**0.5
if d == dist:
    ...

# better: compare the squared (integer) distance instead
d = (x2-x1)**2 + (y2-y1)**2
if d == dist**2:
    ...
```

When you truly can't avoid a float comparison, compare with a tolerance
instead of `==` — see Week 2's Introduction essay for why.
