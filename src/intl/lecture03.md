# Conditionals

<a href="https://colab.research.google.com/github/SuminHan/book-cs2-intl/blob/main/notebooks/intl/lecture03.ipynb" target="_blank" rel="noopener" style="display:inline-block;padding:7px 16px;margin:2px 0 14px;background:#F37626;color:#ffffff;border-radius:6px;text-decoration:none;font-weight:600;font-size:0.92em;">📓 Open Jupyter Notebook</a>



**1 August 2012, 9:30 a.m.** Knight Capital was the largest trader of US
stocks. Its software started buying high and selling low — thousands of
times per second.

It was meant to place 212 orders. It placed more than 4 million.

Forty-five minutes later the company had lost **$440 million** — more than
it was worth.

### The cause was an `if`

Back in 2003, Knight built an internal test tool called *Power Peg*: fire
off small, repeated buy-high/sell-low orders just to probe how the market
reacted — it was never supposed to touch real trading. By 2005 it was
retired. Nobody deleted the code. It just sat there, dormant, behind an
`if`:

```python
if flag:
    run_power_peg()      # 2003: an old testing feature
```

In 2012, Knight needed that exact same `flag` for something new: routing
orders for the NYSE's incoming Retail Liquidity Program. Same variable,
completely different meaning now. Nobody deleted the old branch — they
just wrote the new one and assumed the flag would only ever mean the new
thing.

On deployment day the new code reached 7 of the company's 8 order-routing
servers. The eighth didn't get the update — so on that one server, `flag`
still meant *Power Peg*. And the safety counter that used to stop
`run_power_peg()` after one small round of test trades? Years earlier,
that counter had been quietly repurposed for something else entirely.
Nothing was left to stop it.

Every incoming customer order that morning re-triggered the dormant code
on that one server — over and over, buying high and selling low, exactly
as designed back in 2003, except now with real money and no limit. In 45
minutes: more than 4 million trades across 154 stocks, most of them
losing money by design.

> Widely documented; see the [SEC administrative proceeding against
> Knight Capital](https://www.sec.gov/files/litigation/admin/2013/34-70694.pdf)
> (2013).

### What an `if` really is

An `if` is a promise about the future: "whenever this condition is true, do
this."

The condition was still true. The code still ran. Only the meaning had
changed — and a condition cannot notice that.

**Every `if` you write this week is a promise that has to stay true after
you forget you wrote it.**
