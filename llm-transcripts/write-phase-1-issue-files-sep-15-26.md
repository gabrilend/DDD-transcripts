# Conversation Summary: agent-a54d67c6e92e11268

Generated on: 2026-09-26 12:45:33
Models: claude-fable-5-1

--------------------------------------------------------------------------------

### User Request 1

Your directive: You are a fork with the whole design conversation in context.
Write the ISSUE FILES for PHASE 1 of Double Diaper Dungeon, plus the phase's
progress page. Project root:
/mnt/cmdo/ritz/games/tq/ai-stuff/double-diaper-dungeon. Read docs/019-roadmap.md
for the exact list of your phase's issues (101 through 111a),
docs/001-what-this-game-is.md for vocabulary, docs/002, 003, 004, 022 for the
mechanisms, docs/018 for house style, docs/020 for open question ids, and
assets/023-balance-table.lua for entry names. Do not touch any file outside
issues/. Do not run git. Do not run new-source-file.

File naming: issues/{PHASE}{ID}-{dashed-lowercase-title}.md, e.g.
issues/101-the-tick-is-a-dispatch-table.md, and
issues/111a-every-mechanic-has-a-scenario.md. One file per roadmap row, exact
titles.

Format of every issue (copy the hero-less-moba shape you read):

# NNN — Title

| | |
| --- | --- |
| Phase | 1 — The Clock and the Ground |
| Blocked by | issue numbers, or — |
| Blocks | issue numbers |
| Reads | links to the documents it builds from, ../docs/NNN-name.md |
| Open questions | ids from docs/020-open-questions.md (e.g. C4, C16), or none |

## Current behavior
What exists now. For every issue in this phase: nothing runs; the documents, the
balance table, the file tools, the fridge and the demo runner exist.

## Intended behavior
The blueprint. What the thing is, how it works mechanically, what data it owns
(fields with datatypes), what each branch leads to, what it refuses and how
(errors, never fallbacks, nothing nil), what log lines it emits if any, and how
it is tested. Enough that a reader could rebuild the piece from this file plus
the documents. Plain English and the fixed vocabulary; list files, functions and
data structures by descriptive name rather than writing code snippets. Numbers
by balance-table entry name, never values.

## Suggested implementation steps
Numbered. Which files to create (propose dashed names for ./new-source-file; do
NOT claim indices), which functions and structures each holds, the scenario or
test that validates it, and the order.

## Related documents and tools

## Still open
What this issue leaves for the open-questions page.

Rules: issues are blueprints, not work logs. Every issue that builds a mechanic
also writes that mechanic's log lines and a scenario in tests/. Issue 111 is the
phase capstone: it creates issues/completed/demos/phase-1-demo, a bash script
following the house script convention (header comment, hard-coded DIR at the top
overridable by the first argument, all paths relative), that runs the headless
runner on a level scenario for ten thousand ticks, prints which rooms became
infested when, and runs the determinism check at normal and half speed; the demo
shows numbers and outputs, not descriptions. Issue 111a is the census: every
mechanic has a scenario. Also write issues/phase-1-progress.md in the shape of
hero-less-moba's phase-1-progress.md: the goal, what it ends with, a table of
issues with status "not started", a Blocking line naming the open questions that
block anything in the phase, and "Demo: not yet built".

Length: 500 to 1200 words per issue. When done, reply with the list of files
written and their word counts, and any NEW open questions you noticed (topic
plus one sentence). Nothing else.

--------------------------------------------------------------------------------

### Assistant Response 1

Task: write the phase-1 issue files and the phase-1 progress page. Done.

Files written under
`/mnt/cmdo/ritz/games/tq/ai-stuff/double-diaper-dungeon/issues/`:

| File | Words |
| --- | --- |
| 101-the-tick-is-a-dispatch-table.md | 1044 |
| 102-randomness-comes-from-named-streams.md | 751 |
| 103-the-world-is-flat-records-allocated-once.md | 908 |
| 104-the-hex-map-is-built-by-a-tool.md | 1082 |
| 105-doors-keys-and-the-acyclic-lock-chain.md | 861 |
| 106-the-ghost-room-is-the-farthest-by-an-unlock-aware-flood.md | 871 |
| 107-a-room-fills-with-monsters-when-nobody-is-in-it.md | 1012 |
| 108-the-headless-runner.md | 897 |
| 109-a-scenario-you-can-hold-at-the-gate.md | 834 |
| 110-the-report-you-read-in-the-morning.md | 791 |
| 111-the-proving-ground.md | 773 |
| 111a-every-mechanic-has-a-scenario.md | 689 |
| phase-1-progress.md | 459 |

No files outside `issues/` touched; no git; no counter claims.

New open questions noticed while writing:

- **Event-kind catalogue ownership.** The events list carries integer kinds and
  the text lives in a catalogue under assets; which issue owns adding a kind,
  and whether a kind with no catalogue text is refused at assembly or at report
  time.
- **Fridge in scenarios.** Whether a scenario may name fridge contents, so the
  demo's sticker printout is testable without the real file.
- **Provisional entries in the report.** Whether every report should print the
  balance table's provisional entries at the top so a nobody-confirmed number is
  never read as settled.
- **Demo stop choice.** Whether the phase-1 demo's fourth step ends on the first
  infestation or on a stop the developer picks at run time.
- **Monster slot sizing.** Whether the monster array is sized per battle or per
  level once several battles spawn reinforcements at once.
- **Terminal colour bands.** The report has no colour, so slider shares are
  printed in brackets after a name; whether that is the wanted terminal form.
- **Hand-described maps and the outline.** A room address outside the outline is
  refused, but a hand-described map may want no outline at all; whether the
  validator takes an outline parameter or infers it.

--------------------------------------------------------------------------------

