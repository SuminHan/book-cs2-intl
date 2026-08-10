# Topics Covered

## Why Lists

Without a list, summing eight numbers means eight separately-named
variables — and code that can't scale to a variable amount of data:

```python
number0, number1, number2, number3 = 2, 4, 3, 1
number4, number5, number6, number7 = 7, 2, 5, 6
total = number0 + number1 + number2 + number3 + number4 + number5 + number6 + number7
```

A **list** replaces the eight names with one, indexed by position:

```python
number = [2, 4, 3, 1, 7, 2, 5, 6]
total = 0
total += number[0]
total += number[1]
...
```

Combined with a `for` loop, this becomes genuinely concise — and now it
works for a list of *any* length, not just 8:

```python
number = [2, 4, 3, 1, 7, 2, 5, 6]
total = 0
for i in range(len(number)):
    total += number[i]
print(total)
```

(`total += numberi` is not a thing — there's no way to build a variable
name out of a loop variable. Indexing is what a list buys you.)

## Creating Lists

```python
number = [2, 5, 8, 11, 14]      # with initial values

number = [None] * 5             # uninitialized, filled in later
for i in range(len(number)):
    number[i] = 3*i + 2
```

`[None] * 5` is shorthand for `[None, None, None, None, None]` — `None`
can be replaced with any placeholder value, e.g. `[-1] * 5`. Avoid `[0] *
5` as a placeholder specifically, since it invites confusion about whether
`0` is a *real* value already written in, or just a placeholder waiting to
be overwritten.

## Indexing

`len(·)` gives the length; **always use `len(·)` instead of a literal
number**, so the code keeps working if the list's size changes.

`list[i]` is the `(i+1)`-th element (indices start at `0`). Valid indices
are `0` to `len(·)-1`; `list[-1]` through `list[-len(·)]` also work,
counting from the end (`list[-1]` is the last element). Anything else is
out of range.

```python
number = [None] * 4
number[0] = 7
number[1] = number[0] * 2
number[2] = number[0] + 1
number[3] = number[2] - 60
number[3] += number[1]
```

You can treat `number[i]` exactly like an `int` variable — read it, write
it, use it in an expression. The index itself can be any expression that
evaluates to an `int`:

```python
for i in range(4):
    print(number[(i+2) % 4])   # prints number[2], number[3], number[0], number[1]
```

## Lists as Parameters and Return Values

A list can be passed into a function just like any other value:

```python
def total(numbers):
    s = 0
    for i in range(len(numbers)):
        s += numbers[i]
    return s
```

And a function can build and return a new list:

```python
def incrementAll(b):
    a = [None] * len(b)
    for i in range(len(a)):
        a[i] = b[i] + 1
    return a

print(incrementAll([2, 4, 3, 1, 7, 2, 5, 6]))   # [3, 5, 4, 2, 8, 3, 6, 7]
```

This "make a same-length output list, fill it in with one loop" shape is
the pattern behind most of this week's Problem Set.
