# THE HIDDEN MATHEMATICS BEHIND THE 🕐

### The Clock [3600, 60, 1] and the (25, 12) System: Why Universal Time Cannot Be Diophantine

**Author:** Bilal El Issaoui
**Independent Researcher**, Amsterdam
**Year:** 2026

🔗 **[Try the interactive web demo](https://a19dammer91.github.io/the-exact-algebraic-condition-for-clock-behaviour/)**

---

## Start here: one question

A stopwatch has been running for **45,296,789 milliseconds**. What does the display say?

Anyone who has ever used a stopwatch knows the answer without thinking:

> **12:34:56.789**

But almost nobody can explain **how** you get there. Why not 11:34, or 13:56? Where does that 12 come from? Why does a clock jump back to 0 after 59 seconds, and not after 60 or after 100?

This document is about that question. The answer is surprisingly simple, and underneath it sits a mathematical structure that people have been using for thousands of years without ever seeing it.

---

## The everyday example: money

Before we talk about clocks, first something everyone knows.

Imagine you have **notes of €25 and €12**. You want to pay exactly **€575**. How many ways are there to do that?

Two ways:

- 11 notes of €25 and 25 notes of €12
- 23 notes of €25 and 0 notes of €12

No others. That is the whole idea behind what mathematicians call a **linear Diophantine equation**. It sounds heavy, but it just means: *how many coins of each kind do I need to land exactly on an amount, and how many different combinations exist?*

That is one extreme. At the other extreme stands the clock.

---

## The clock works in the opposite way

A clock has one job that matters more than any other: **every second must have exactly one face**. Never two, never zero. When you look at the clock at 3 in the afternoon, you do not want to wonder whether it might also be 3 in the morning.

With the money example, it is fine that there are two ways to pay €575. With the clock, that is unacceptable.

That difference in purpose decides everything.

Where the money example allows **many** answers, the clock must allow **exactly one**. And to achieve that, the clock has to follow a rule that the money example does not:

**Every layer must fit exactly into the layer above it.**

- 60 seconds fit exactly into 1 minute
- 60 minutes fit exactly into 1 hour
- 24 hours fit exactly into 1 day

No leftover, no rounding. That is why seconds jump back to 0 after 59, and not after 60 or after 100. And that is why a clock cannot have a Diophantine structure. Not because it is forbidden, but because it would not work.

---

## Why this matters in practice

You might be thinking: interesting, but what is in it for me? Three things.

### 1. If you ever work with time, files, or coordinates

Everywhere you turn one big number into something readable, this happens:

| Big number | Readable form | Layers |
|---|---|---|
| 45,296,789 ms | 12:34:56.789 | days, hours, minutes, seconds, ms |
| 1,234,567 bytes | 1.23 MB | bytes, KB, MB |
| 3,661 seconds | 1:01:01 | hours, minutes, seconds |
| 20260917 | 17 September 2026 | year, month, day |

Once you see the pattern one time, you see it everywhere. And if you have ever had to hunt down a bug in a timestamp, you know it almost always comes down to understanding these layers.

### 2. If you have ever tried to explain modulo to someone

Modulo (the remainder after division) is famously hard to explain with formulas alone. But **everyone** understands a clock. *"It is 11 o'clock, three hours from now it is 2 o'clock."* That is 11 + 3 = 14, and 14 mod 12 = 2. Once someone sees that, they understand modulo for the rest of their life.

### 3. The transferable insight

Every system with layers on top of each other has to make a choice:

- **Either** you make it easy to find every possible combination (money)
- **Or** you make it impossible to be uncertain (clock)

Those are opposite goals. You cannot unite them in one structure. That is not a flaw of the clock. It is a design decision.

---

## Why this is a better teaching route than the usual one

At school, students usually learn modulo like this:

> *"The remainder after division. 17 mod 12 = 5. Now here are some exercises."*

That works, but it stays abstract. Students can do the sums without understanding why anyone would ever want this.

This route starts in exactly the opposite place:

1. **Start with the clock.** Everyone has an intuition. 12 + 1 = 1. That is not mathematics, that is just how a clock works.
2. **Then state the rule.** Why does it jump back after 12? Because it can show 12 hours and no more.
3. **Write the rule down.** That is modulo. The student already has the idea, only the name is missing.
4. **Apply it to money.** Now the student can solve a Diophantine problem without it being called that.
5. **Show the difference.** The clock chooses certainty, money chooses freedom. That is the real insight.

Someone who learns it this way understands modulo not as a trick, but as a **choice** you make when you build a system with layers. That is a much stronger understanding.

---

## The most beautiful time a clock can show

There is one time that is special, and you have probably never noticed it:

> **12:34:56.789**

The digits 1 through 9 sit neatly in order. 1, 2, 3, 4, 5, 6, 7, 8, 9. No interruption, no repetition.

It is a lucky hit of the decimal system and the 24-hour division. And it is exactly the time when people take a picture of their clock, or send a message to someone. It is the one second per day when the clock shows its own beauty.

In the interactive document that goes with this paper, there is a slider that **ends exactly on that time**. Drag it all the way to the right and you land on 45,296,789 milliseconds: 12 hours, 34 minutes, 56 seconds, and 789 thousandths of a second.

That is not a mathematical necessity. It is a tribute to the structure you would otherwise never see.

---

## The heart of the difference

Now the technical core, but without jargon.

### The (25, 12) system

This system uses **one rule** for the whole number:

> 25 is one more than a multiple of 12.

In other words: 25 = 2 × 12 + 1.

Because of this, you can work out in one step how many €25 notes you need at minimum. You divide N by 12, look at the remainder, and you are done.

Every other solution then follows automatically: add 12 to the number of €25 notes, subtract 25 from the number of €12 notes. Keep doing that until it no longer fits.

### The clock

The clock works differently. There is no single rule that gives the whole answer in one step. Each layer must be peeled off on its own:

1. First the hours: how many whole hours fit into T?
2. Then the minutes: how many whole minutes fit into what is left?
3. Then the seconds: what is still left over?
4. And so on.

Only after four steps do you know the full answer. That is not a weakness. That is exactly what is needed to make **every second unique**.

### Why they are not the same, even though they look alike

At first glance, both systems look similar. They both "jump back to 0". But the clock jumps back because every layer fits into the one above it (60 into 60, 24 into 1). The (25, 12) system does not jump back. It just keeps counting, and the rule 25 = 1 above 12 determines how many solutions exist.

That is the heart of it: **the clock has no Foundation, and that is not a mistake. That is the entire point.**

---

## The 12-hour trap

There is a classic confusion that many people fall into. The 12-hour dial (13:00 becomes 1:00) uses the same modular idea as the (25, 12) system. It is tempting to think that the clock therefore has the same structure as the money example.

It does not, for two reasons.

**First:** the dial is a **metaphor**. The clock itself does not run on a modulus of 12. The clock runs on 60, 60, 24. The 12 on the dial is a drawing that people have placed on top of the real mechanism.

**Second:** the 12-hour dial loses information. 1 in the morning and 1 in the afternoon look the same. The 24-hour structure does not. That is why the real clock uses 24 hours and not 12. Only with 24 hours does every second stay unique across a whole day.

Test it yourself: 3 in the morning is 10,800 seconds, 3 in the afternoon is 54,000 seconds. With 24 hours, those are two different values. With 12 hours, they both become "3 o'clock" and you can no longer tell them apart. That is precisely the confusion the real clock exists to prevent.

---

## Summary in three points

1. **The purpose differs.** The (25, 12) system is built to find as many combinations as possible. The clock is built to give every second exactly one face.

2. **The method differs.** The (25, 12) system uses one rule for the whole number. The clock uses a chain of rules, one per layer.

3. **The missing Foundation is not a flaw.** The clock deliberately chooses certainty. That is exactly the opposite of what the money example needs, and that is the whole point.

---

## What this paper adds

The mathematical literature has long covered the Frobenius problem, the counting of representations, and positional number systems. What is new here is the **direct comparison** between a deliberately built Diophantine system and a canonical positional system.

The central message: you cannot measure them with the same ruler, even though at first glance they look like they do the same thing. They both "jump back to 0", but they do it for opposite reasons.

---

## Repository structure

```
/paper/       Publication-ready HTML and PDF versions
/code/        Python scripts for verification and comparison
/figures/     Figures used in the paper
README.md     This file
```

## Code

The `/code/` folder contains Python scripts for:

- Computing the clock decomposition (days, hours, minutes, seconds, ms) for any T
- Computing all representations of N = 25A + 12B
- Verifying that A0 = N mod 12 for every N
- Comparing the cascade structure of the clock with the global structure of the (25, 12) system

## Interactive document

Alongside this paper there is an HTML document that brings the whole structure to life:

- Five layers that all show the same number, and update each other instantly when you change one of them
- Two sliders: one for a full month (30 days), and one that ends on 12:34:56.789
- A play button that lets time advance at four speeds, from true speed up to one day per second
- Visible carry arrows that light up when a layer reaches its maximum and pushes through to the next


**Live demo:** https://a19dammer91.github.io/the-exact-algebraic-condition-for-clock-behaviour/

---

## Companion work

This paper is the conceptual counterpart to a pattern paper on deterministic decomposition. Where this paper shows a system that deliberately refuses multiplicity in order to guarantee uniqueness, the companion paper shows a system that embraces multiplicity: one anchor value, five structural layers, and a closed O(1) rule for splitting any integer across them.

**The D³ Pattern: Deterministic Data Decomposition by A-C Coupling**

- Repository: https://github.com/A19dammer91/D3-by-A-C-Coupling-Demo
- Live demo: https://a19dammer91.github.io/D3-by-A-C-Coupling-Demo/
- DOI: https://doi.org/10.5281/zenodo.20819940

Read together, the two papers frame a single question: what does it mean for a representation system to be complete, and what does it cost to give up multiplicity in exchange for uniqueness?

---

## Related work

This paper is part of a series on linear Diophantine representation systems with p ≡ 1 (mod q):

- 19 9 system: https://doi.org/10.5281/zenodo.19474707
- 25 12 system and clock structure comparison: this repository

## License

Released under Creative Commons Attribution NonCommercial ShareAlike 4.0 (CC BY NC SA 4.0).

Commercial use is not covered by this license.

## Contact

Bilal El Issaoui
elissa.oui.amster@gmail.com
elissa.oui@outlook.com

Or open an Issue or start a Discussion in this repository.
