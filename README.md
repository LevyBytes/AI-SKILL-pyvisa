# PyVISA Instrument-Control Reference

Original-prose PyVISA documentation reference for Agent Kaizen.

This is the `pyvisa` skill for **[Agent Kaizen](https://github.com/DirectorGunner/agent-kaizen)**: a PyVISA documentation corpus recontextualized into original prose while preserving identifiers exactly.

## What this skill covers

PyVISA is the Python library for controlling measurement instruments over VISA across GPIB, USB, serial/RS-232, and TCPIP/Ethernet. This skill is a faithful reference for the `ResourceManager`, listing and opening resources, read/write/query operations, VISA attributes and constants, termination characters, timeouts, and event handling. It also covers the `visa` shell, choosing a backend (pyvisa-py vs NI-VISA), and both the high-level and low-level API. It does not cover the Python standard library or other instrument-control libraries.

## What's inside

- `SKILL.md` — the trigger description and workflow for using the reference.
- `references/` — right-sized topic files (one subject per file, across 54 reference files), plus `INDEX.md` to pick the matching file and `topics.json` metadata.
- `GOTCHA.md` — recurring failure modes and what to do instead.

## Use it

After promotion, this skill lives at `<devroot>\SKILLS\skills\pyvisa`. Link it for local testing with a Windows directory junction (no admin), or a symlink elsewhere:

```cmd
mklink /J .agents\skills\pyvisa  <devroot>\SKILLS\skills\pyvisa
mklink /J .claude\skills\pyvisa  <devroot>\SKILLS\skills\pyvisa
```

It publishes as `AI-SKILL-pyvisa`. See **[skill-drafting](https://github.com/DirectorGunner/AI-SKILL-skill-drafting)** for the full linked-skills workflow.

## Status

Recontextualized into AGPL-licensable original prose with identifiers preserved; pending promotion and publication by the user.

## Reducing idle context cost (skill invocation policy)

Every installed skill costs a little context on every session: the agent sees each skill's name and description before you ever use it. If you rarely use this skill in a given project, you can keep it installed and still explicitly invocable while hiding it from the model's automatic listing.

Doing so does **not** modify this skill's source repo — the policy lives in your local agent settings. The Agent Kaizen **[skill-drafting](https://github.com/DirectorGunner/AI-skill-drafting)** repo ships a manager, `scripts/skill_policy.py`, that sets this for all your skills at once:

```bash
python skill_policy.py audit     # list every skill + its current policy + idle cost
python skill_policy.py plan      # write a decision file with recommendations (nothing applied)
# edit that decision file: set selected_policy + approved:true for the skills you choose
python skill_policy.py preview   # show the exact change
python skill_policy.py apply     # apply ONLY what you approved (backup + rollback recorded)
python skill_policy.py restore   # roll back
```

- **Claude Code (works today):** writes `skillOverrides: { "<skill>": "user-invocable-only" }` to `.claude/settings.local.json` — zero idle listing cost, still available from the `/skills` menu. Start a new session for it to take effect; invoke it any time via `/skills`.
- **Codex (currently unreliable):** explicit-only Codex skills are affected by an open bug ([openai/codex#23454](https://github.com/openai/codex/issues/23454)) where `$skill` invocation of an explicit-only local skill can fail. Until it's fixed, leave Codex skills implicit, or fully disable rarely-used ones with `[[skills.config]] enabled = false` in `config.toml`. The manager audits Codex but does not change Codex policy.
