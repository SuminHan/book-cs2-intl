# Boolean Functions

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture04.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



You want to check whether `x` is 1 or 2. In English that is one short
sentence, so you write it the way you say it:

```python
x = 5
print(x == 1 or 2)
```

`x` is 5. So this prints `False` — right?

**It prints `2`.**

Python read it as `(x == 1) or 2`:

- `x == 1` is `False`
- so `or` moves on and hands back `2`
- and `2` counts as true

So inside an `if`, this condition is true for every value of `x` — 5, 99,
anything.

### Say it twice

`or` joins two complete comparisons, not one comparison and a leftover number.

```python
# Correct
print(x == 1 or x == 2)     # False
```

**Why this one is dangerous:** it never crashes. It never warns you. It
just quietly says yes to everything — and an `if` that is always true looks
exactly like an `if` that works.
