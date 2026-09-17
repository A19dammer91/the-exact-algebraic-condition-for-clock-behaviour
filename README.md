# THE HIDDEN MATHEMATICS BEHIND THE 🕐

### The Clock [3600, 60, 1] and the (25, 12) System: Two Diophantine Structures, Two Purposes

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

## The clock uses a different Diophantine structure

A clock time can also be written as a linear Diophantine representation. In seconds it looks like this:

> T = 3600·H + 60·M + S

Same shape as the money example. Same kind of equation. But the clock arrives at exactly one answer, while the money example gives you several. The difference is not in the type of equation. It is in the structure of the bases and the bounds on the coefficients.

The clock's bases form a chain:

> 1000 → 60 → 60 → 24

Each position value is an exact multiple of the one below it. 1000 milliseconds make one second. 60 seconds make one minute. 60 minutes make one hour. 24 hours make one day. No leftover at any step. And on top of that, each coefficient is bounded: seconds and minutes stay below 60, hours stay below 24.

Together, those two properties give exactly one representation for every instant. Remove either one, and the uniqueness collapses.

The money example does the opposite. The two coefficients, 25 and 12, are not in a divisibility relation at all. They are related by a single offset:

> 25 ≡ 1 (mod 12)

Because of that one relation, you can compute the smallest €25 count directly as N mod 12. But nothing bounds the coefficients, so the same equation accepts a whole ladder of solutions, each one a valid answer.

Both systems are Diophantine. Both are deterministic in the sense that they follow exact rules. They simply achieve their determinism through opposite mechanisms:

| | (25, 12) system | Clock |
|---|---|---|
| Type | Linear Diophantine | Linear Diophantine |
| Base relation | One foundation relation: 25 ≡ 1 (mod 12) | Each base is a multiple of the one below |
| Coefficient bounds | None | Seconds < 60, minutes < 60, hours < 24 |
| Number of solutions | Multiple | Exactly one |
| Source of structure | A single residue relation | A hierarchical divisibility chain |

A clock is not a weaker Diophantine system. It is a different one, deliberately built to guarantee uniqueness instead of exploring multiplicity.

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

Those are opposite goals. You cannot unite them in one structure. That is not a flaw of the clock. It is a design decision. And both choices are Diophantine at heart. They simply pick different mechanisms to reach their purpose.

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
5. **Show the difference.** Both systems use the same kind of equation. The clock adds divisibility and bounds. Money does not. That is the real insight.

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

This system uses **one relation** for the whole number:

> 25 is one more than a multiple of 12.

In other words: 25 = 2 × 12 + 1, or 25 ≡ 1 (mod 12).

Because of this, you can work out in one step how many €25 notes you need at minimum. You divide N by 12, look at the remainder, and you are done. The smallest €25 count is exactly N mod 12.

Every other solution then follows automatically: add 12 to the number of €25 notes, subtract 25 from the number of €12 notes. Keep doing that until it no longer fits. That is what produces the ladder of valid answers.

### The clock

The clock works differently. Its bases form a chain of exact multiples:

> 24 × 60 × 60 × 1000 = 86,400,000

And each coefficient is bounded by the ratio of the adjacent bases. That is what gives you exactly one answer, not a ladder.

You peel off one layer at a time:

1. Take T mod 1000. That gives Ms directly, because 1000 is the smallest base.
2. Divide away the milliseconds, then take the result mod 60. That gives S.
3. Divide away the seconds, then take the result mod 60. That gives M.
4. Divide away the minutes, then take the result mod 24. That gives H.

At every step, the coefficient you extract is automatically bounded by the modulus you just used. Seconds land in [0, 60), minutes in [0, 60), hours in [0, 24). No ambiguity is possible.

### Why they are not the same, even though they look alike

Both systems peel off layers with a mod operation. Both are Diophantine. But they answer different questions.

The (25, 12) system asks: *how many ways can I build N out of these two coefficients?* It answers with a formula for a whole family.

The clock asks: *what is the unique decomposition of T into these five bounded layers?* It answers with exactly one tuple.

Same equation shape. Opposite purposes.

---

## The 12-hour trap

There is a classic confusion that many people fall into. The 12-hour dial (13:00 becomes 1:00) uses the same modular idea as the (25, 12) system. It is tempting to think that the clock therefore has the same structure as the money example.

It does not, for two reasons.

**First:** the dial is a **metaphor**. The clock itself does not run on a modulus of 12. The clock runs on 60, 60, 24. The 12 on the dial is a drawing that people have placed on top of the real mechanism.

**Second:** the 12-hour dial loses information. 1 in the morning and 1 in the afternoon look the same. The 24-hour structure does not. That is why the real clock uses 24 hours and not 12. Only with 24 hours does every second stay unique across a whole day.

Test it yourself: 3 in the morning is 10,800 seconds, 3 in the afternoon is 54,000 seconds. With 24 hours, those are two different values. With 12 hours, they both become "3 o'clock" and you can no longer tell them apart. That is precisely the confusion the real clock exists to prevent.

---

## Summary in three points

1. **Both are Diophantine.** The money example and the clock are both linear Diophantine representations. Same equation shape, different constraints.

2. **The source of uniqueness differs.** The (25, 12) system relies on a single foundation relation, 25 ≡ 1 (mod 12), with no bounds on the coefficients. The clock relies on a hierarchical divisibility chain, 1000, 60, 60, 24, with bounded coefficients. That is what makes the clock unique and the money example multiple.

3. **Both choices are deliberate.** Neither structure is a mistake. The (25, 12) system is built to explore multiplicity. The clock is built to guarantee certainty. Each answers the question it was designed for.

---

## What this paper adds

The mathematical literature has long covered the Frobenius problem, the counting of representations, and positional number systems. What is new here is the **direct structural comparison** between a Diophantine system driven by a single foundation relation and a Diophantine system driven by a hierarchical divisibility chain.

The central message: these two systems cannot be measured with the same ruler, even though both are Diophantine and both use mod operations. One is built around a residue relation, the other around exact divisibility. They both "jump back to 0", but they do it for opposite reasons. And that opposition is precisely what makes them useful for opposite purposes.

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
- Comparing the divisibility chain of the clock with the foundation relation of the (25, 12) system

## Interactive document

Alongside this paper there is an HTML document that brings the whole structure to life:

- Five layers that all show the same number, and update each other instantly when you change one of them
- Two sliders: one for a full month (30 days), and one that ends on 12:34:56.789
- A play button that lets time advance at four speeds, from true speed up to one day per second
- Visible carry arrows that light up when a layer reaches its maximum and pushes through to the next

The document is available in both English and Dutch.

**Live demo:** https://a19dammer91.github.io/the-exact-algebraic-condition-for-clock-behaviour/

---

## Companion work

This paper is the conceptual counterpart to a pattern paper on deterministic decomposition. Where this paper examines a system whose uniqueness comes from a hierarchical divisibility chain with bounded coefficients, the companion paper shows a system whose structure comes from a single anchor value and a closed rule for splitting any integer across five layers.

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

Or open an issue or start a discussion in this repository.
