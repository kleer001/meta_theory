# The Skill Network

The [prompts](../prompts/) are the method. **Skills** bake the method into Claude
Code so the *discipline runs itself* — invokable by slash command, composable, and
(crucially) schedulable. This is the difference between "a thing I remember to do"
and "a thing that happens."

Three skills, chosen because they are the highest-leverage prompts and because they
*compose*:

| Skill | Slash | Wraps prompt | Engine | Phase |
|---|---|---|---|---|
| **cartographer** | `/cartographer` | [01](../prompts/01-cartographer.md) | `deep-research` | map (once) |
| **canon-finder** | `/canon-finder` | [02](../prompts/02-canon-finder.md) | `deep-research` | map (once) |
| **altitude-check** | `/altitude-check` | [03](../prompts/03-altitude-check.md) | reads the repo | audit (recurring) |

(The remaining prompts — `roots`, `first-principles`, `pre-mortem` — are valuable
but lower-frequency; keep them as prompts, or promote them to skills later if you
find yourself reaching for them often. `first-principles` + `roots` are natural
sub-steps a richer `cartographer` could call.)

## How they relate

```
                         ┌─────────────────┐
                         │  /cartographer  │   the spine: produces the
                         │  (map the ladder)│   layered ladder of mastery
                         └────────┬────────┘
                                  │ its foundation layers feed ↓
                         ┌────────▼────────┐
                         │  /canon-finder  │   zooms into "what to study"
                         │  (find the canon)│   for those layers, + access flags
                         └────────┬────────┘
                                  │ output of both → a real foundation doc
                                  ▼
                         ░░ you BUILD the thing ░░
                                  │
                                  │  at every milestone ↓ (put on a /loop)
                         ┌────────▼────────┐
                         │ /altitude-check │   audits what you built AGAINST
                         │ (are we above   │   the map; finds skipped rungs,
                         │  our foundation?)│   cheapest-fix-first
                         └────────┬────────┘
                                  │ aggregated across many repos ↓
                         ┌────────▼────────┐
                         │  maestro repo   │   ontological house-calls
                         │  (see ../maestro.md)│   on a whole portfolio
                         └─────────────────┘
```

- **cartographer → canon-finder** is a *zoom*: the map names the foundation layers;
  the canon-finder finds the bedrock resources for them and pins down access.
- **Both → altitude-check** is the loop's closing edge: the map and canon define
  "what the foundation should be," and the altitude-check repeatedly asks "do we
  actually have it?"
- **altitude-check → maestro** is a *scale-up*: the same audit, run across a
  portfolio on a schedule, by a dedicated repo.

## Composition with the skills you already have

- **`deep-research`** — the research engine `cartographer` and `canon-finder`
  delegate to. They are essentially *named, pre-shaped research questions*.
- **`loop`** — wrap `altitude-check` in it (`/loop <interval> /altitude-check`, or
  trigger at milestones) to make the audit automatic. This is the structural fix
  for the structural problem: the question that caught this repo's gap gets asked
  *for* you, forever.

## Where they live (text, not installed)

These are kept as **portable text inside `META_THEORY/`** — deliberately **not**
installed into this repo's `.claude/skills/`. They're subject-agnostic tools meant
to travel across *all* your ventures, not to bind to (or auto-activate in) this one
music repo.

```
META_THEORY/skills/
  cartographer.md     ← rationale (inputs/outputs/relationships) + inline SKILL.md
  canon-finder.md
  altitude-check.md
  install/            ← ready-to-install runnable copies
    cartographer/SKILL.md
    canon-finder/SKILL.md
    altitude-check/SKILL.md
```

**To actually use them**, copy the runnable copies into your **user** skills dir
on a machine where your home directory persists (so they're available in every
repo, not just this one):

```bash
cp -r META_THEORY/skills/install/{cartographer,canon-finder,altitude-check} ~/.claude/skills/
```

The `.md` spec files are the human-readable rationale and inline the same text;
[`install/`](./install/) holds the clean drop-in `SKILL.md` files.
