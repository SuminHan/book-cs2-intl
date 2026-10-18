# For Loops II

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture09.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



## Warm-up: the counter you already know

You wrote counters on the midterm (`countLeapYears`, `countPeaks`). Here is the bug that breaks most of them.

```python
L = [3, -1, 4, -5, 2]

for x in L:
    count = 0
    if x > 0:
        count = count + 1

print(count)
```

There are three positive numbers. Does this print 3?

**It prints 1.**

`count = 0` sits inside the loop. So every single time around, the count is
thrown away and started again.

The number you see at the end is not a total. It is just whatever happened
on the last item — and `2` is positive, so you get 1.

*Try `L = [3, -1, 4, -5, -2]` and it prints `0`. Same code, different last item.*

### One space is the whole bug

```python
# Correct -- set up before the loop
count = 0
for x in L:
    if x > 0:
        count = count + 1
print(count)      # 3
```

**The question to ask every counter:** "Does this line need to happen
*once*, or *every time around*?" Setting up belongs outside. Only the
counting belongs inside.

## For some / for all

This is the quantifier pattern from today's class — "for all".

```python
def all_positive(L):
    for x in L:
        if x <= 0:
            return False
    return True
```

`all_positive([1, 2, 3])` is `True`. `all_positive([1, -2])` is `False`. Good.

Now: `all_positive([])` — the empty list. Is every number in it positive?

**Python says `True`.**

Follow the code: the loop body never runs, so nothing ever returns `False`,
so it falls through to `return True`.

And that is *not a bug* — it is the correct answer. To prove "all of them
are positive" false, you must point at one that isn't. In an empty list
there is nothing to point at.

*Mathematicians call this a vacuous truth. Python's own `all([])` is `True`
for the same reason, and `any([])` is `False`.*

### Where it will bite you

```python
if all_passed(students): print("Everyone passed!")
```

Run that on a class with no students and it happily announces that
everyone passed.

**The empty case is not an edge case you forgot. It is the first case you
should test.**
