# Basic Elements

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture01.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



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

Write \\(1/3\\) in decimal: \\(0.3333\ldots\\) — it never ends. You have to stop
somewhere, so you store something slightly wrong. A computer stores numbers
in **binary**, and in binary \\(0.1\\) is a number that never ends either —
the `0011` pattern just repeats forever:

```
0.1  ->  0.0001 1001 1001 1001 1001 1001 1001 ...  (binary)
0.2  ->  0.0011 0011 0011 0011 0011 0011 0011 ...  (binary)
0.3  ->  0.0100 1100 1100 1100 1100 1100 1100 ...  (binary)
```

A computer doesn't store it in that raw form, though — like scientific
notation, it *normalizes* first (slide the point so there's a single `1`
in front) and stores the piece after the point (the **mantissa**) and how
far the point moved (the **exponent**) separately:

```
0.1  =  1.1001100110011001100110011001100110011001100110011010 x 2^(01111111011)
0.2  =  1.1001100110011001100110011001100110011001100110011010 x 2^(01111111100)
0.3  =  1.0011001100110011001100110011001100110011001100110011 x 2^(01111111101)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^      ^^^^^^^^^^^
```

The 52-bit part after `1.` is exactly the **mantissa** field in memory; the
11-bit binary number inside `2^(...)` is exactly the **exponent** field —
except it isn't the true exponent yet. It's stored with `1023` already
added to it (so `01111111011` = 1019 means a true exponent of
`1019 - 1023 = -4`). *Why 1023, specifically? See [How Numbers Live in
Memory](../general/number-representation.md) for the reference-level
version of all of this.*

Because the mantissa only has 52 bits to work with, each of these gets
cut off and rounded to the nearest value that *does* fit — which, converted
back to decimal, is:

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
