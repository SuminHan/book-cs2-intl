# Wrap Up

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture15.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



Look back at the bugs from every page since the midterm. Almost none of
them crashed. They ran, printed something reasonable, and were wrong.

| Page | The code looked fine, but… |
|---|---|
| [For Loops II](lecture09.md) | `count = 0` inside the loop counts only the last item |
| [For Loops II](lecture09.md) | `all_positive([])` is `True` — and that is correct |
| [While Loops](lecture10.md) | a loop whose condition never changes never ends |
| [List II](lecture11.md) | removing from a list while walking it skips elements |
| [Strings](lecture12.md) | `s.replace(...)` alone changes nothing |
| [Multi-Dimensional Lists](lecture13.md) | `break` leaves one loop, not both |
| [Classes & Objects](lecture14.md) | an attribute under `class` is shared by every object |

### One habit that catches most of them

Before you trust a function, run it on the inputs that are easy to forget:

- the **empty** list / string
- **one** element
- the answer at the **first** position, at the **last** position, and **nowhere**
- every element **equal**

The bugs above all hide in exactly these cases.

### Five loop shapes to write without thinking

```python
total = 0                      # accumulate / count
for x in L:
    if cond(x):
        total += 1

for x in L:                    # for some
    if cond(x):
        return True
return False

for x in L:                    # for all
    if not cond(x):
        return False
return True

for i in range(n):             # every pair once
    for j in range(i + 1, n):
        ...

while n > 0:                   # digit by digit
    d = n % 10
    n = n // 10
```

### Changes it, or returns a new one?

| | changes the object (returns `None`) | returns a new value |
|---|---|---|
| list | `L.append(x)`, `L.sort()`, `L.remove(x)`, `L[i] = x` | `sorted(L)`, `L + M`, `L[i:j]` |
| string | nothing — strings are immutable | `s.upper()`, `s.replace(a, b)`, `s + t` |
| your class | modifier methods | pure methods |

`L = L.sort()` makes `L` equal to `None`. `s.upper()` on its own line is
thrown away. Both run without an error.
