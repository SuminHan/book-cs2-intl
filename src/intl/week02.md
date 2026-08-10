# Basic Elements

## Opener: A Very Easy Question

You have just learned variables, expressions, and `print`. So this should be easy:

```python
print(0.1 + 0.2)
```

What does Python print? Everyone knows this one — say it out loud.

**Python disagrees:**

```
0.30000000000000004
```

```python
print(0.1 + 0.2 == 0.3)      # False
```

This is not a bug. Every computer on Earth agrees with Python here.

### Why: some numbers have no exact form

Write $1/3$ in decimal: $0.3333\ldots$ — it never ends. You have to stop
somewhere, so you store something slightly wrong. A computer stores numbers
in **binary**, and in binary $0.1$ is a number that never ends either. Here
is what is really in memory:

```
0.1  ->  0.10000000000000000555
0.2  ->  0.20000000000000001110
0.3  ->  0.29999999999999998890
```

The first two add up to a hair *more* than the third. That hair is the
`...004` you saw.

### Where this bites you

Tiny errors pile up. Add 0.1 ten times:

```python
total = 0.0
for i in range(10):
    total = total + 0.1
print(total)          # 0.9999999999999999
print(total == 1.0)   # False
```

**The rule to remember all semester:** never test two decimals with `==`.
Ask whether the gap is small enough instead: `abs(a - b) < 0.000001`.

The computer did the arithmetic perfectly. It still gave you an answer you
did not expect. Knowing what the machine will actually do is a different
skill from telling it what to do.

## Topics Covered

- Computation in math vs. Python
- Variables & values
- Operators & expressions (`+ - * / // % **`)
- Input from keyboard, output to screen

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*
