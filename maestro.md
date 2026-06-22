# The Maestro — ontological house-calls for a portfolio

The [altitude-check](./skills/altitude-check.md) skill audits *one* repo on
demand. The Maestro generalizes that audit **to a whole portfolio, on a schedule,
by a dedicated repo** — the conductor who periodically walks the orchestra and
asks each section whether it still knows its scales. This file specs it seriously
enough to build.

---

## The pitch

A small repo, `maestro`, whose entire job is to **pay recurring ontological
house-calls** to your other repos: clone/read each one, run an altitude-check
against its domain's foundation, and leave behind a short, honest report — *"you've
built a lot above this layer that was never written down; here's the cheapest fix."*
Not a linter (it doesn't care about style or bugs) — an **epistemic auditor**: it
checks whether a project's *foundations* keep pace with its *ambitions*.

It is the natural endpoint of this whole directory:

```
prompt  →  skill (one repo, on demand)  →  maestro (many repos, on a schedule)
03-altitude-check  →  /altitude-check     →  the Maestro
```

---

## How it would work

A run, per target repo:

1. **Visit.** Acquire the repo (a fresh clone, or a Claude Code on the web session
   scoped to it — which already clones fresh per session).
2. **Orient.** Infer the domain and intent from READMEs/docs/code. Use a committed
   foundation baseline if the repo has one (a `cartographer` map / `canon-finder`
   index, or this very `META_THEORY/` dir); otherwise reconstruct the expected
   foundation for the domain.
3. **Audit.** Run the altitude-check method: where is the repo operating *above* its
   foundation? What would a master expect written down that isn't?
4. **Report.** Emit a short, dated verdict — cheapest-fix-first, ending on one
   concrete action. Delivery options, least to most intrusive:
   - append to a `maestro/reports/<repo>/<date>.md` log in the maestro repo;
   - open a single issue titled *"Ontological checkup — <date>"* on the target;
   - (only if asked) draft the missing foundation doc as a PR.
5. **Track drift.** Diff against the previous report so the Maestro can say *"this
   gap has been open three checkups running"* or *"foundation caught up since
   last visit — clean bill of health."*

**Cadence:** weekly/monthly per repo, or event-driven (after a milestone tag, a
burst of commits, or a new top-level subsystem appears — those are exactly when
altitude drift happens).

---

## What it's built from (mostly things that already exist)

- **The audit logic** is [`/altitude-check`](./skills/altitude-check.md), unchanged
  — the Maestro is its orchestration layer, not new analysis.
- **Scheduling / recurrence** is the `loop` skill (or cron / a scheduled
  **Claude Code on the web** trigger, or a `send_later` self-check-in).
- **Per-repo isolation** maps cleanly onto **subagents** (one research/audit agent
  per target, run in parallel) and onto web sessions' fresh-clone model.
- **Cross-repo reach** needs the one genuinely new capability: a way to enumerate
  and access the portfolio (a repo list + read access). On Claude Code on the web,
  that's the `list_repos` / `add_repo` mechanism; locally, a config file of repo
  paths/URLs.

So ~80% is composition of the kit you already have; the new ~20% is the **roster**
(which repos, how reached) and the **delivery** (where reports land).

---

## Minimal shape, if you build it

```
maestro/
  roster.json          # the portfolio: repos, domains, cadence, delivery pref
  run.mjs              # for each repo: acquire → /altitude-check → report → diff
  reports/<repo>/<date>.md
  README.md            # "the conductor walks the orchestra"
```

`roster.json` entry sketch:

```json
{
  "repo": "kleer001/cyber_synth",
  "domain": "procedural music",
  "foundation": "META_THEORY/ + research/song_construction_basics.md",
  "cadence": "monthly",
  "deliver": "report-log"
}
```

---

## Design principles (so it stays charming, not naggy)

- **Honest clean bills.** "Your foundation is solid" must be a frequent, first-class
  result. An auditor that always finds work becomes noise.
- **Cheapest-fix-first, always.** Every report ends with one concrete, small action,
  not a backlog.
- **Quiet by default.** Append to a log; escalate to an issue only on real drift;
  open a PR only when asked. Respect the "be frugal about posting" instinct.
- **Foundations, not bugs.** Stay out of the linter/CI lane. The Maestro's only
  question is *does the depth of understanding match the height of the ambition?*
- **It audits itself.** The Maestro repo is also on its own roster. A conductor who
  never practices is just a guy waving a stick.

---

*Status: vision, not built. It is fully specced against tools that exist today
(`altitude-check` + `loop` + subagents + the web platform's per-session clone and
repo-roster mechanics). When you want it, start with `roster.json` + a `run.mjs`
that audits a single repo, then add recurrence, then the diff/drift tracking.*
