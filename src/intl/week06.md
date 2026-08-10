# For Loops I

```python
for i in range(10):
    print(i)
```

This prints 0 to 9. Not 1 to 10. Why would anyone design it that way?
Nobody counts like this.

### Because of the subtraction

`range(a, b)` means start at `a`, stop before `b`. That one choice makes
three annoying things disappear:

- **How many items?** $b - a$. Nothing to add, nothing to subtract.
  `range(0,10)` has 10 items.
- **Splitting a list.** `range(0,5)` and `range(5,10)` fit together
  perfectly — no gap, no overlap, no 5 appearing twice.
- **Empty is natural.** `range(3,3)` is simply empty. No special case needed.

If it counted 1 to 10 instead, every one of those would need a `+1` or `-1`
somewhere — and that is exactly where off-by-one bugs live.

### The habit to build this week

The design is not there to annoy you. It is there so that you never have to
write `+1`.

**Whenever you catch yourself typing `range(1, n+1)`, stop and ask whether
you are fighting the language — and whether the `+1` is about to cost you.**
