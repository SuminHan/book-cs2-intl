# Week 4: Conditionals

## Opener: 45 Minutes

**1 August 2012, 9:30 a.m.** Knight Capital was the largest trader of US
stocks. Its software started buying high and selling low — thousands of
times per second.

It was meant to place 212 orders. It placed more than 4 million.

Forty-five minutes later the company had lost **$440 million** — more than
it was worth.

### The cause was an `if`

Back in 2003 the code had a switch that turned on an old feature called
*Power Peg*:

```python
if flag:
    run_power_peg()      # 2003: an old testing feature
```

Years later that same `flag` was reused to mean something completely
different — and nobody deleted the old branch.

On deployment day the new code reached 7 of the 8 servers. The eighth still
had the 2003 branch. When the flag went up, that server did what it was told.

> Widely documented; see the SEC administrative proceeding against Knight
> Capital (2013).

### What an `if` really is

An `if` is a promise about the future: "whenever this condition is true, do
this."

The condition was still true. The code still ran. Only the meaning had
changed — and a condition cannot notice that.

**Every `if` you write this week is a promise that has to stay true after
you forget you wrote it.**
