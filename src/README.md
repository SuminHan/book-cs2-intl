# CS2 International Supplement

Supplementary notes for the International track of KSA Computer Science 2 (CS2).

This is not a replacement for class — just supplementary material. The
essay below and the weekly opener content are original 2026 material. The
"Topics Covered" outline on each week page is a topic-title-only reference
to the 2025 offering — full slide content is not reproduced.
Instructor-only material (e.g. diagnostic pretests, the syllabus, and
answer keys) is intentionally excluded.

The Korean track (국내반) is maintained separately in [book-cs2](https://github.com/SuminHan/book-cs2).

---

## Why Programming Matters

*Computer Science 2*

### 1. The Question

"AI writes code now. It writes it faster than me, and honestly better than
me. So why am I sitting in a programming class?"

That's a fair question — and the answer isn't "AI is bad at coding."
**It isn't. It's very good, and it's getting better every month.** The
answer is about **what job just opened up** because of that.

### 2. What Changed

Ask an AI for a binary search and you get one — instantly, correct. Ten
years ago that was a week of the course. Now it's four seconds. So what got
expensive?

**The bottleneck moved.**

| | Before | Now |
|---|---|---|
| Hard part | **Writing** the code | **Judging** the code |
| | You wrote 100 lines a day, and understood all 100 — because you had to, to write them | You can generate 1000 lines in a minute. Do you understand any of them? |

AI improving does not shrink this job. It grows it.

This is already showing up in the job market: it's harder for new grads and
interns to get hired, and average seniority at big tech companies keeps
rising — while top tech companies are still hiring ~20% more than a year
ago, with AI engineering listings up 50–100% at places like Apple and
Google.[^job-market] Both are true at once: the old way in was "here is a
small, well-defined task — go implement it," and that's exactly what AI
does best now. **That first step is gone.** What's left starts one level
up: decide, direct, verify.

[^job-market]: The Pragmatic Engineer, [*State of the Software Engineering
    Job Market 2026*](https://newsletter.pragmaticengineer.com/p/state-of-the-job-market-2026)
    and [*The Job Market in 2026, Part 2*](http://newsletter.pragmaticengineer.com/p/the-job-market-in-2026-part-2).

You can prompt in plain language going *in*. But coming *back*, the answer
is always code — there is no human-language version of the output.
**If you cannot read what comes back, you did not give an instruction —
you made a wish.**

### 3. The Gap

Ask an AI to "write me a grade calculator" and you get something clean,
readable, that runs fine — and is wrong for this specific course, because
it can't know:

- how a medical-excuse make-up score should be weighted (80%) vs. an
  official absence (100%) — the generated code has neither rule
- what happens when a student retakes a failed test — which score counts?
- whether an attendance cutoff overrides everything else, or is checked first

**Nothing about the generated code *looks* wrong. It won't warn you. It
just quietly computes the wrong grade** — and you only know to fix the
prompt if you already noticed the rule was missing. **You had to read the
code to see the holes.**

### 4. The Trap

A function that checks for leap years passes the test you throw at it
(`is_leap_year(2024)` → `True`, correct!). Ship it?

Try `is_leap_year(1900)` — expected `False` (1900 was *not* a leap year:
divisible by 4, but a century not divisible by 400), and the naive version
returns `True`. The bug was always there; the test just never looked in the
right place. **Passing a test is not the same as being right** — choosing
the input that breaks it is the actual skill, and no one can do that for you.

The same pattern, for real: NASA's *Mars Climate Orbiter* (1999) flew for
ten months, then broke apart on arrival because one team's thruster
calculations were in pounds of force and the other team read them as
newtons — off by a factor of 4.45, for ten months, at a cost of $125
million. **Every line of that code ran perfectly. Nobody checked what the
number *meant*.**

### 5. Your Job

In 1950 Alan Turing asked "Can machines think?" — and refused to answer it
directly. He turned it into a test instead: a human judge questions both
sides and decides whether the answers hold up. At the very beginning of
computing, the design already had a person in the chair, asking the
questions. **That chair never got automated.**

This is what the course's four Subject Core Competencies actually ask of you:

- **Fundamental Programming & Problem-Solving** — read what comes back and
  understand what it really does
- **Logical Thinking & Analytical Skills** — know which input would break
  it, before it breaks
- **Communication & Collaboration** — why we work problems together, out
  loud, in class
- **Ethical Use of AI & Responsible Attitude** — use the tool, then own the
  answer. "The AI wrote it" is not a defence.

So — why are you here? Not to type code faster than a machine, but to be
the person who can say exactly what is wanted, read what comes back, and
know which input would break it. That's also why this class runs the way
it does: **in class we solve problems together, by hand, without AI** — not
because using AI is cheating, but because you cannot build a skill that the
machine performs for you.

You will use a calculator your whole life. You still learned arithmetic by
hand.

---

_Still a work in progress — chapters will be filled in as the semester goes._
