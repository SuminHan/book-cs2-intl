# List II

## 11.1. Opener: Remove Every Negative Number

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

## 11.2. Topics Covered

- `.append()`, slicing `[:]`
- List operations: `==`, `+`, `in`
- Built-in functions: `sum()`, `max()`, `min()`, `sort()`
- List comprehension

*Reference: 2025 offering topic outline. This year's full lecture slides
are still in development — only the topic list is reflected here, not the
slide content.*
