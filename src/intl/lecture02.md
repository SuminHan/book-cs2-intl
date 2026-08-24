# Functions

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture02.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#2e3192;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>


A function takes something in and gives something back. Usually that is
exactly what you want.

Biologists study a gene called `SEPT2`. Another is called `MARCH1`. They
typed those names into Excel. Excel has a helpful little function that
looks at what you typed and decides what you *meant*. What do you think it did?

**It turned genes into dates:**

```
SEPT2   ->   2-Sep
MARCH1  ->   1-Mar
```

Nobody asked for this. Nobody was warned. The gene names were simply gone,
and once saved they are very hard to get back.

A 2016 study checked 35,175 spreadsheets from 3,597 published papers: about
one paper in five carried these corrupted names. A follow-up covering
2014–2020 found over 30%.

> Sources: Ziemann et al., [*Genome Biology*](https://doi.org/10.1186/s13059-016-1044-7)
> (2016); Abeysooriya et al., [*PLOS Computational
> Biology*](https://doi.org/10.1371/journal.pcbi.1008984) (2021).

### The lesson for this week

When you call a function, you are trusting it to do exactly one thing — the
thing its name says.

Excel's autocorrect was doing its job perfectly. It was just doing a
different job than the biologists thought it was doing.

**When you write a function this week, ask: could someone read the name and
expect something else?**
