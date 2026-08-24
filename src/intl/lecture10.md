# List II

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture10.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



You have just learned `.remove()`. This reads perfectly:

```python
def remove_negatives(L):
    for x in L:
        if x < 0:
            L.remove(x)
    return L

print(remove_negatives([1, -2, -3, 4, -5, -6]))
```

Expected: `[1, 4]`

**Half of them survived:**

```
[1, -3, 4, -6]
```

A `for` loop walks by position: 0, 1, 2, ... But `remove` pulls everything
after it one step left.

So when `-2` at position 1 is deleted, `-3` slides into position 1 — and
the loop has already moved on to position 2. Every second negative is skipped.

```python
# Correct -- build a new list instead
def remove_negatives(L):
    return [x for x in L if x >= 0]
```

### The rule

> Never change a list while you are walking through it.

Make a new one, or walk it backwards.

*And notice again: no crash, no warning. Just a quietly wrong answer.*
