# Topics Covered

## Values & Variables

Every piece of data a program works with is a **value**, and every value has
a **type**:

| Examples | Kind | Type |
|---|---|---|
| `11`, `0`, `-200` | integers | `int` |
| `3.14159`, `1.234E-8` | reals | `float` |
| `"abc"`, `'abc'`, `"123"` | strings | `str` |

A **variable** is a named memory location that stores a value. Assignment
writes a value into it; using the variable's name later reads the value back
out.

```python
x = 10          # writing 10 to x
y = x*x + 1     # reading 10 from x, writing 101 to y
print(y)        # reading 101 from y
```

`10 = x` is illegal — the left side of `=` must be a variable name, not a
value (compare: "let 10 be x" isn't something you'd write in math either).
The same variable can be assigned more than once; each assignment overwrites
the previous value, which is exactly what makes accumulation work:

```python
total = 0
total = total + 7
total = total + 5
print(total)    # 12
```

Python also allows assigning to several variables at once — this is how you
swap two variables without a temporary:

```python
a, b, c = 1, 2, 4
a, b = b, a          # swap
x, y, z = y, z, x    # rotate
```

(Note `a = b` then `b = a`, done as two separate statements, does **not**
swap — by the time the second line runs, `a` and `b` already hold the same
value.)

Variable names must be made of letters, digits, and `_`, must not start with
a digit, and cannot be a **keyword** (`int`, `if`, `else`, `while`, `for`,
`range`, ... — reserved by Python itself).

## Expressions

An **operator** is a symbol for a basic computation. The arithmetic
operators are `+ - * / // % **`:

- `/` — division (always gives a `float`)
- `//` — quotient (`7 // 3` → `2`)
- `%` — remainder (`7 % 3` → `1`)
- `**` — power (`2 ** 5` → `32`)

An **expression** is a legal combination of variables/values and operators
(and, later, functions) — evaluating it substitutes each variable's value
and computes the result:

```python
z = x + y*(60 + x)
```

**Precedence**, high to low: `()` > `**` > `* / // %` > `+ -`. Same
precedence breaks left-to-right:

```python
5 + 7*9          # 5 + (7*9) = 68, not (5+7)*9
2*100 // 60      # (2*100) // 60 = 3
2*(100 // 60)    # 2*(100//60) = 2
```

When you're not sure how an expression will parse — or the reader won't be
— add parentheses. Don't rely on memorizing the table.

**Decompose** long expressions into named intermediate steps. It costs a
couple of extra lines and pays for itself the moment you need to debug or
re-read the code:

```python
# hard to read, hard to debug
p = (x+y**2)**3 + 2*(x+y**2) + (x**2+1)**y

# same computation, decomposed
a = x + y**2
b = x**2 + 1
p = a**3 + 2*a + b**y
```

## Types

`type(·)` tells you the type of a value, variable, or expression:

```python
print(type(7))        # <class 'int'>
print(type(7.0))      # <class 'float'>
print(type("7"))      # <class 'str'>
print(type(7 // 3))   # <class 'int'>
print(type(7 / 3))    # <class 'float'>
```

`int(·)`, `float(·)`, `str(·)` convert between types:

```python
x = 7
print(float(x))        # 7.0
y = 7.51
print(int(y))          # 7   (truncates, doesn't round)
print(1 + int("7"))    # 8
```

*Curious what `int`/`float` actually look like in memory, and why that's
the reason `0.1 + 0.2 != 0.3`? See [How Numbers Live in
Memory](../general/number-representation.md).*

## Input / Output

`print` writes to the screen; by default each argument is separated by a
space and it ends with a newline. Both are overridable with `sep=` and
`end=`:

```python
print(1, 2, 3)          # 1 2 3
print(1, end=" ")
print(2, end="")
print(3)                 # 1 23
```

`input(·)` reads a line typed by the user and **always returns a `str`** —
even if the user typed a number, you must convert it yourself:

```python
s = input("Enter an integer: ")
n = int(s)          # input() gives str, not int
print(n**2)
```
