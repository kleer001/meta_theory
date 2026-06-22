# 03 · The Altitude Check

> Audit what you've already built against the map: are you operating *above* your
> foundation?

The most valuable prompt in the kit, because it is *recurring* — the "did we skip
the basics?" check turned into a repeatable reflex. Run it at every milestone.

- **Fire when:** at each milestone, before a big push, or whenever a project starts
  to feel "out of hand," hollow, or precariously advanced.
- **Engine:** reads the project itself (code, docs, research) — run via
  [`/altitude-check`](../skills/altitude-check.md); automate with `loop`.
- **Pairs with:** [`01-cartographer`](./01-cartographer.md) (the map it audits
  against — explicit if you have one, reconstructed if you don't);
  [`06-pre-mortem`](./06-pre-mortem.md) is its future-tense twin.

## The prompt

```
Look at everything we've built and researched in <PROJECT> so far. Are we
operating ABOVE our foundation — doing advanced/specialized work while
assuming or skipping basics? What would a master of this craft be
surprised we don't have written down? List the missing foundational
layers, cheapest-to-fix first.
```

## Variables

- `<PROJECT>` — the repo/effort under audit (point it at the working tree, or name
  the project).

## What good output looks like

- A short verdict: **are we above our foundation, and where?**
- A list of **missing foundational layers**, each with a one-line "a master would
  expect this and it's absent" justification.
- **Sorted cheapest-fix-first**, so the audit ends with an actionable next step,
  not just anxiety.
- Ideally, a pointer to *where* in the project each gap should live.

## The failure it prevents

Silent drift. Each individual advanced step is reasonable; the *accumulation* of
them with no foundation underneath is the failure, and it's invisible from inside
the work. The altitude check is the outside view, on a schedule.
