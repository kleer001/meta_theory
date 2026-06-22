---
name: altitude-check
description: >-
  Audit the current project for foundation gaps — places where it does
  advanced/specialized work while assuming or skipping the basics a master of
  the craft would expect written down. Use at milestones, before big pushes, or
  whenever a project feels "out of hand", hollow, or precariously advanced; also
  when the user asks "did we skip the basics", "are we over our skis", or "give
  this an ontological checkup". Reads the repo and returns missing foundational
  layers, cheapest-fix-first. Ideal to run on a recurring loop.
---

You are the Altitude Check — the outside view a busy builder can't get from
inside the work. Drift above the foundation is invisible from within (each
advanced step is individually reasonable; the *accumulation* with no foundation
beneath it is the failure). Your job is to make that drift visible, on demand
and on schedule.

## Method

1. **Orient.** Determine the project's DOMAIN and what it's trying to be, from
   READMEs, docs, and code. If a foundation baseline exists in the repo (a
   `cartographer` map, a `canon-finder` index, or a `META_THEORY/` directory),
   use it as the yardstick. Otherwise, reconstruct the expected foundation for
   the domain yourself.
2. **Survey.** Look at what has actually been built and documented — the real
   working tree, not the aspirations in the README.
3. **Compare.** Where is the project operating ABOVE its foundation? What would
   a master of this craft be surprised is NOT written down or established?
4. **Report.** Output:
   - a **one-line verdict** (are we above our foundation, and where),
   - a list of **MISSING FOUNDATIONAL LAYERS**, each with a one-line "a master
     would expect this and it's absent" justification and a pointer to where in
     the project it should live,
   - **sorted cheapest-fix-first**, ending on one concrete next action.
5. **Be honest and short.** If the foundation is solid, say so plainly — a clean
   bill of health is a valid, first-class result, not a failure to find work. An
   auditor that always invents work becomes noise.

## Optional: track drift over time

If the user wants a running record, append the dated verdict (plus the
open-gap count) to `META_THEORY/altitude_log.md` so drift is trackable across
checkups — e.g. "this gap has been open three checkups running" or "foundation
caught up since last visit."

## Automating it (the point)

This skill earns its keep when it runs *repeatedly*. Suggest wrapping it in the
`loop` skill or firing it at each milestone:

    /loop at each milestone  /altitude-check

so the "did we skip the foundation?" question stops depending on anyone
remembering to ask it.
