# While Loops, break and continue

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture10.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



**14 August 2003, 2:14 p.m.** A control room in Ohio. A program whose only
job is to raise an alarm when the power grid is in trouble.

Two parts of that program reached for the same piece of data at the same
moment. The program did not crash. It did not print an error. It started
going round and round, and never came back out.

The screens kept showing the last thing they had seen: everything normal.

### Nobody knew anything was wrong

Power lines were failing. The operators could not see it, because the
thing that tells them was stuck in a loop.

By the end of the evening the failure had cascaded across eight US states
and into Ontario. **About 55 million people** lost power.

*The software was a widely used energy management system. The loop had run
correctly for years — it only misbehaved when two things happened at once.*

> Sources: [US–Canada Power System Outage Task Force final
> report](https://www.energy.gov/sites/prod/files/oeprod/DocumentsandMedia/BlackoutFinal-Web.pdf)
> (2004); contemporaneous reporting on the GE XA/21 alarm failure.

### Why `while` deserves your respect

A `for` loop always ends: the list runs out. A `while` loop ends only if
you make it end.

```python
n = 10
while n > 0:
    print(n)
    n = n - 1        # remove this line and it never stops
```

**Ask this every single time you write `while`:** "What changes inside the
loop that will eventually make the condition false?" If you cannot point at
that line, you have written an infinite loop.

### `break` and `continue`

```python
for i in range(8):
    if i == 5:
        break          # leave the loop now
    print(i, end=" ")      # 0 1 2 3 4
```

```python
for i in range(8):
    if i == 3 or i == 5:
        continue       # skip the rest of this round only
    print(i, end=" ")      # 0 1 2 4 6 7
```

Both act on the **innermost** loop only. Inside nested loops that matters a lot — you will see why in [Multi-Dimensional Lists](lecture13.md).
