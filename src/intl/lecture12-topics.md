# Topics Covered

## `break` and `continue`

- **`break`** — exits the loop immediately. Nothing else in the loop body
  runs, and the loop doesn't run again.
- **`continue`** — skips the rest of *this* iteration only, and moves on
  to the next one. The loop keeps going.

```python
for i in range(8):
    if i == 5:
        break              # stop the loop entirely once i reaches 5
    print(i, end=" ")
print()   # 0 1 2 3 4

for i in range(8):
    if i in [3, 5]:
        continue            # skip printing 3 and 5, keep looping
    print(i, end=" ")
print()   # 0 1 2 4 6 7
```

## In Nested Loops: Only the Innermost Loop

Both `break` and `continue` act on the **innermost** loop that contains
them — they never reach out to an outer loop. This is the detail that
trips people up, so trace it carefully:

```python
i = 0
while i < 5:
    j = 0
    while j < 5:
        if i > 0:
            break          # exits the INNER while j loop only
        print(j, end=" ")
        j += 1
    print(i, end=" ")       # this line still runs every time
    i += 1
```

Here, `break` fires as soon as `i > 0` — but it only ever escapes the inner
`j`-loop. The outer `i`-loop is completely unaffected: it keeps
incrementing `i` and printing it every iteration, it just stops seeing any
`j` values printed from the second iteration onward.

Now compare with `continue` in the same position:

```python
i = 0
while i < 5:
    j = 0
    while j < 5:
        if i > 0:
            continue        # skips straight back to "while j < 5" —
                              # j never gets incremented!
        print(j, end=" ")
        j += 1
    print(i, end=" ")
    i += 1
```

This second version is a trap: once `i > 0`, `continue` sends control back
to the `while j < 5` check *without* ever reaching `j += 1` — so `j` stays
at whatever it was, the condition `j < 5` is still true, and the loop spins
forever. **`continue` re-checks the loop condition; it does not advance
whatever variable your loop condition depends on for you.** This is a good
reason to prefer `for` loops (where the loop variable advances
automatically) whenever the number of iterations is known in advance, and
to be extra careful with `continue` inside a `while`.
