# For Loops III

This is the quantifier pattern you just learned — "for all".

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
