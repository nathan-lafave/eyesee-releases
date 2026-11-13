# 24. How EyeSee decides what matches

You do not need this chapter to run a clinic. You need it when a volunteer
asks *"why did it pick that pair?"*, when a result looks wrong, or when you
are training someone who wants to trust the tool rather than obey it.

Nothing here is new thinking. It is the ministry's own matching rules,
carried across from the original software unchanged, written out in plain
language.

---

## The idea in one paragraph

For every pair of glasses in your inventory, EyeSee asks a short list of
yes/no questions about each eye — *is the sphere close enough? the
cylinder? the axis?* A pair has to pass every question that applies to
count as a match at all. Everything that passes is then scored on **how
far off** it was, and the closest are listed first.

So there are really two separate things happening: a **pass/fail gate**,
and then a **ranking** of whatever got through.

---

## Part one: the gate

### The four questions

For each eye, EyeSee checks:

**1. Is the sphere close enough?**

The difference between the prescribed sphere and the lens's sphere must be
within the sphere tolerance — **±1.00 D** at the clinic standard setting.

There is an extra rule here that surprises people: **a plus lens never
matches a minus prescription**, however close the numbers. A patient
needing −0.25 is not served by a +0.25 lens even though they are half a
diopter apart; they are opposite corrections. The only exception is when
both are within 0.125 of zero, where the distinction stops meaning
anything.

**2. Is the cylinder close enough?**

Within the cylinder tolerance — again **±1.00 D** at the standard setting.

**3. Is the axis close enough?**

Within the axis tolerance — **±15°** at the standard setting.

Axis is an angle with no direction, so 179° and 1° are **2° apart**, not
178°. EyeSee measures the short way round.

When the lens has essentially no cylinder (0.25 D or less), this question
passes automatically. A spherical lens has no axis to be wrong about.

**4. Is the reading power close enough?** *(only if you asked for it)*

Sphere, add and cylinder combined into the power the patient gets when
looking through the reading portion. It must be within the sphere
tolerance, **±1.00 D** at the standard setting. The patient's figure is
taken to two decimals, as the old program did, so a pair *exactly* at the
limit can fall just outside it — the same pairs in both programs.

### Every question that applies must pass

Which questions apply depends on the prescription:

| Situation | Questions asked, per eye — all must pass |
|---|---|
| Prescription has astigmatism | **3** — sphere, cylinder, axis |
| …and you asked for a reading add too | **4** — the same, plus reading power |
| Prescription has no astigmatism | **2** — sphere, and *does the lens have little cylinder?* |
| …and you asked for a reading add too | **3** — the same, plus reading power |
| Matching reading power only | **1** — reading power |

There is no partial credit: a pair that passes two of three questions is
not a match. What makes this workable with donated stock is the width of
the tolerances — ±1.00 D is four prescription steps either way, and ±15°
of axis. Requiring near-perfect measurements would reject almost
everything in the boxes. The **Margin** (part two) then separates the
close fits from the merely acceptable.

> **"No astigmatism" means a cylinder of 0.25 D or less** in both eyes.
> Below that, cylinder is clinically negligible, so EyeSee does not
> compare cylinders or axes at all. It only asks that the lens itself has
> little cylinder: 0.50 D or less at the standard setting.

### The spherical-equivalent shortcut

One special case is worth understanding, because it is what the **Equiv**
label in the results means.

When a patient needs astigmatism correction but the lens in the box is
**plain spherical** (0.25 D of cylinder or less), EyeSee can still offer
it — if the lens's power is within the sphere tolerance of the patient's
*spherical equivalent*.

The spherical equivalent is:

```
sphere + (cylinder ÷ 2)
```

It is the single spherical power that comes closest to the overall effect
of a sphere-plus-cylinder prescription. A patient prescribed −2.00 with
−1.00 of cylinder has a spherical equivalent of −2.50, and a plain −2.50
lens will serve them tolerably.

When that shortcut is used, it stands in for the sphere, cylinder and axis
questions — there is no axis on a spherical lens — and the eye is labelled
**Equiv** rather than **Match**, so you know it happened. (If you asked
for a reading add, the reading power must still pass.)

This is also the concession that **Skip spherical equivalent** turns off,
and the one Auto-tune's step 4 turns on.

### After the gate: Dr. Rose's rules

A pair that passes the questions can still be turned away by Dr. Rose's
dispensing rules. All three are on at the clinic standard (**Settings**):

- **No over-plus.** For a farsighted (plus) eye, the lens may not be more
  plus than prescribed. When you asked for a reading add, the lens's add
  may not be higher than prescribed either.
- **No over-cylinder.** The lens's cylinder may exceed the patient's by at
  most 0.25 D — or 0.50 D with **Over-cylinder up to 0.50 D** on, which is
  the clinic standard.
- **No over-minus.** For a nearsighted (minus) eye, from age 35 the lens
  may not be more minus than prescribed; under 35, up to 0.50 D more minus
  is allowed. This applies only when an age has been entered.

---

## Part two: the ranking

Everything that passed the gate is scored, and the smaller the score, the
closer the fit. That score is the **Margin** column.

### The unit

Margin is counted in **quarter-diopters**. Every 0.25 D of error is one
margin unit. So a margin of 2.0 means roughly half a diopter out.

Quarter-diopters because that is the step real prescriptions come in.

### What goes into it

For each eye, three numbers:

- how far the **sphere** is off, in quarter-diopters
- how far the **cylinder** is off, in quarter-diopters
- how far the **axis** is off, weighted (see below)

Those are **averaged** — divided by three. Add a fourth, the reading add,
and it is divided by four instead.

Averaging rather than adding is what stops a single imperfect measurement
from dominating. A pair that is slightly off on everything ranks near a
pair that is exact on two things and poor on the third.

### Why axis is weighted

Axis error is not equally important at every prescription, so it counts
for more when there is more cylinder to misalign:

| Patient's cylinder | Each degree of axis error counts |
|---|---|
| Up to 2.00 D | 0.05 margin units |
| 2.00 – 3.00 D | 0.5 units |
| Over 3.00 D | 1.0 unit |

At a small cylinder, being 10° off the axis barely matters — there is
little astigmatism correction to misalign. At 3.50 D of cylinder, the same
10° is a serious error, and the scoring says so, twenty times over.

And if the *lens* has no meaningful cylinder, axis error scores zero —
there is nothing to align.

### How the margin is shown

To one decimal, **cut off rather than rounded** — 0.67 shows as 0.6 —
exactly as the old program did. Pairs showing the same margin are listed
in inventory-number order. Because both programs work this way, the same
search prints the same list in the same order in either one.

### The Equiv case

When an eye matched by spherical equivalent, the margin is the distance
between the patient's spherical equivalent and the lens's, in
quarter-diopters. The cylinder and axis are not scored, because the whole
premise of that match is that the cylinder was set aside.

One quirk, kept from the old program so both list the same pairs in the
same order: for the lens, it uses the sphere *minus* half the cylinder
rather than plus. That only matters for a lens with a quarter-diopter of
cylinder, and it moves that eye's margin by one quarter-diopter unit.

---

## Putting it together

For a patient prescribed **−2.25 −0.75 × 175**, against a lens of
**−2.00 −0.50 × 5**, at the clinic standard (±1.00 D, ±15°):

| | |
|---|---|
| Sphere | 0.25 D out → within ±1.00 ✓ · margin 1.0 |
| Cylinder | 0.25 D out → within ±1.00 ✓ · margin 1.0 |
| Axis | 175° vs 5° → **10° apart** the short way, not 170° · within ±15° ✓ · 10 × 0.05 = 0.5, counted in whole units → 1 |

All three questions pass, so the eye matches, with a margin of
(1.0 + 1.0 + 1) ÷ 3 = 1.0. If the other eye were an exact fit (0), the
pair's margin is the average of the two eyes: **0.5**.

(The axis figure is always a whole number. At cylinders up to 2.00 D an
exact half, like this 0.5, is rounded up — the old program's arithmetic
did that, and EyeSee matches it so both give the same scores.)

At a tighter setting with a ±5° axis limit, that 10° would fail the
third question, and two out of three is not enough. Raising that eye's
Tolerance to ×2 doubles the limit to 10° and the pair appears again.

That is exactly what the Tolerance multiplier does: it multiplies the
limits in the gate. It does not change the scoring, so margins stay
comparable however you got there.

---

## What this means in practice

- **A match is not a perfect fit.** It is a pair that passed every
  question within the tolerances. Margin tells you how good it actually is.
- **Margin compares pairs against each other**, and is only meaningful
  within one search.
- **Loosening tolerance lets more pairs through the gate**; it never makes
  a pair fit better. A pair found at MAX tolerance has the same margin it
  would have had at Exact — you have simply agreed to see it.
- **Equiv means the cylinder was set aside.** Worth a look before
  dispensing, especially at higher cylinders.
