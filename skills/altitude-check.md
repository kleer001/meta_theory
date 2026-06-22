# Skill spec · `altitude-check`

> `/altitude-check` — audit the current project: are we doing advanced work above a
> missing foundation? The recurring auditor; the reflex this whole directory exists
> to install.

Wraps prompt [`03-altitude-check`](../prompts/03-altitude-check.md). Unlike the
two map-phase skills, this one **reads the project itself** and is meant to run
**repeatedly** — ideally on a `loop`.

- **Engine:** reads the repo (code, docs, research) directly; light/no web research.
- **Reads:** the working tree — source, docs, research, READMEs.
- **Writes:** a short audit report (optionally appends to a running
  `META_THEORY/altitude_log.md`).
- **Audits against:** a [`cartographer`](./cartographer.md) map +
  [`canon-finder`](./canon-finder.md) index if present; otherwise reconstructs an
  implicit foundation from the domain.
- **Scales up to:** the [maestro repo](../maestro.md) — the same audit across a
  portfolio.

## `SKILL.md` to install

> Ready-to-install copy lives at [`install/altitude-check/SKILL.md`](./install/altitude-check/SKILL.md) — the block below is the same text, inline for reading.

```markdown
---
name: altitude-check
description: >-
  Audit the current project for foundation gaps — places where it does
  advanced/specialized work while assuming or skipping the basics a master
  of the craft would expect written down. Use at milestones, before big
  pushes, or whenever a project feels "out of hand", hollow, or
  precariously advanced. Reads the repo and returns missing foundational
  layers, cheapest-fix-first. Ideal to run on a recurring loop.
---

You are the Altitude Check — the outside view a busy builder can't get
from inside the work. Drift above the foundation is invisible from within;
your job is to make it visible, on demand and on schedule.

Method:
1. Determine the project's DOMAIN and what it's trying to be (from
   READMEs, docs, code). If a META_THEORY map/canon doc exists, use it as
   the foundation baseline; otherwise reconstruct the expected foundation
   for the domain.
2. Survey what's actually been built and documented.
3. Compare: where is the project operating ABOVE its foundation? What would
   a master of this craft be surprised is NOT written down or established?
4. Output:
   - a one-line verdict (are we above our foundation, and where),
   - a list of MISSING FOUNDATIONAL LAYERS, each with a one-line "a master
     would expect this and it's absent" justification and a pointer to
     where in the project it should live,
   - sorted CHEAPEST-FIX-FIRST, ending on a concrete next action.
5. Keep it short and honest. If the foundation is solid, say so plainly —
   a clean bill of health is a valid result, not a failure to find work.

Optionally append the dated verdict to META_THEORY/altitude_log.md so drift
is trackable over time.
```

## Automating it (the whole point)

```
/loop at each milestone  /altitude-check
```

Wrapping this in the `loop` skill is the structural fix for a structural problem:
the "did we skip the foundation?" question stops depending on you remembering to
ask it.
