# Topics Covered

## Boolean Type & Expressions

A fourth type joins `int`/`float`/`str`: `bool`, whose only two values are
`True` and `False`.

**Relational operators** build primitive boolean expressions: `== != > < >=
<=`. Watch the difference between assignment and equality — "let x = y" in
math becomes `x = y` (assignment) in Python, while "if x equals y" becomes
`x == y` (a boolean expression, no side effect).

**Logical operators** combine boolean expressions: `and`, `or`, `not`.

| p | q | `p and q` | `p or q` | `not p` |
|---|---|---|---|---|
| True | True | True | True | False |
| True | False | False | True | False |
| False | True | False | True | True |
| False | False | False | False | True |

Precedence, high to low: `()` > `**` > `* / // %` > `+ -` > relational
(`== != > < >= <=`) > `not` > `and` > `or`. As always, parenthesize
anything you're not 100% sure of:

```python
p = x%2 == 1 or x%3 != 0 and (not(y <= 1) or x%2 == 1)
```

## `if`-`else` Conditionals

```python
if boolean_expression:
    statements
else:               # the else block may be omitted
    statements
```

This is how a **multi-case math definition** (a curly-brace piecewise
formula) becomes code — each case becomes a branch:

```python
# f(x) = 0 if x <= 0, else x**2 + 1
def f(x):
    if x <= 0:
        y = 0
    else:
        y = x**2 + 1
    return y
```

Chain more than two cases with `elif`:

```python
if b1:
    statements          # runs if b1 is True
elif b2:
    statements           # runs if b1 is False and b2 is True
elif b3:
    statements           # runs if b1, b2 are False and b3 is True
else:
    statements           # runs if none of the above are True
```

`if`s can also **nest** — but watch out, `if x != 0: if x > 0: ... else:
...` is not the same branching as `if x > 0: ... else: if x < 0: ... else:
...`, even though both can compute the sign of `x`. Trace through `x == 0`
by hand in each version if the difference isn't obvious.

## Multiple `return` Statements

A function can have more than one `return` — commonly one per branch of a
conditional. **As soon as one `return` executes, the function ends
immediately** — no code after it runs, even if it's inside more branches:

```python
def absoluteValue(x):
    if x < 0:
        return -x
    else:
        return x
```

This lets you **prune** dead structure. Once a branch has returned, there's
no need for the surrounding `else` — the code after the `if` block only
ever runs when that `if` didn't return, so it's implicitly the "else" case
already:

```python
# before pruning                    # after pruning — equivalent
if b1:                              if b1:
    return v1                           return v1
else:
    if b2:                          if b2:
        return v2                       return v2
    else:
        if b3:                      if b3:
            return v3                    return v3
        else:
            return v4                return v4
```

Fewer nesting levels, same behavior — easier to read, easier to extend with
one more case later.
