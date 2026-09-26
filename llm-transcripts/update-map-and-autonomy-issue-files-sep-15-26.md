# Conversation Summary: agent-acf475805b1201fe2

Generated on: 2026-09-26 12:45:36
Models: claude-opus-5

--------------------------------------------------------------------------------

### User Request 1

Your directive: You are a fork with the whole design conversation in context.
The developer has answered many open questions. The documentation validator now
reports issue files that still cite questions she has answered, and those issues
need their citations and their bodies brought up to date.

Project root: /mnt/cmdo/ritz/games/tq/ai-stuff/double-diaper-dungeon.

FIRST read
/tmp/claude-1000/-mnt-cmdo-ritz-games-tq-ai-stuff-double-diaper-dungeon/f76814ba-6c5e-46ea-90d1-128d98043fd5/scratchpad/her-answers-digest.md
— that is her settled design, in her own words with the reading beside each.
It is the authority. Also read docs/001-what-this-game-is.md for the fixed
vocabulary.

YOU OWN EXACTLY THESE TWELVE FILES. Edit only these:
- issues/104-the-hex-map-is-built-by-a-tool.md          (cites C1, C2, C3, C11)
- issues/107-a-room-fills-with-monsters-when-nobody-is-in-it.md  (cites C4, C9)
- issues/410-reinforcements-from-connected-rooms.md      (cites C4)
- issues/501-the-priority-table.md                       (cites E1, E12)
- issues/504-exploring-and-heading-for-the-ghost-room.md (cites E2)
- issues/505-the-wait-the-call-and-the-safety-estimate.md (cites E7, E9)
- issues/506-toilets-seeking-sensation-and-the-retry-lock.md (cites C9)
- issues/508-going-home.md                               (cites C3)
- issues/713-levels-up-and-down.md                       (cites C2, C3, C11)
- issues/714-the-intro.md                                (cites C2)
- issues/106-the-ghost-room-is-the-farthest-by-an-unlock-aware-flood.md
- issues/phase-1-progress.md

Do NOT touch any other file, any document under docs/, the balance table, or
docs/020-open-questions.md. Do not run git. Do not rename any file.

FOR EACH ISSUE, two jobs.

**One: the Open questions row.** Remove every question id she has now answered.
Keep the ones still open. If none remain, write "none". The ids she answered
that touch your files are C1, C2, C3, C4, C9, C11, E1, E2, E7, E9, E12. Anything
else stays.

**Two: the body.** Where her answer changes what the issue is meant to build,
rewrite the Intended behavior and the Suggested implementation steps so the
blueprint is correct. Do not add a worklog, do not add a "changed on this date"
note; the issue is a blueprint and it simply says the right thing now. Keep the
format: the header table, Current behavior, Intended behavior, Suggested
implementation steps, Related documents and tools, Still open.

The ones whose bodies genuinely change:

- **106** is the big one, and its title is now wrong. Its current design is "the
  farthest room from the entrance by an unlock-aware flood". Her answer replaces
  that: the generator finds the graph's LONGEST JOURNEY, the pair of rooms whose
  weighted distance apart is greatest, with a locked door costing the whole
  detour to its key and back. One end becomes the entrance and the other the
  ghost room, preferring an end on the grid's border for the entrance, and
  picking at random when neither is. Rewrite the issue completely around that.
  You may not rename the file, so add a line under the header table saying the
  file's name records the algorithm this issue replaced, and that renaming it is
  a job for whoever next renumbers the project. Say how the pair is found (an
  all-pairs search is affordable at this grid size; say what the size makes
  affordable and name the balance entry for the grid radius), how the key detour
  is priced, and what the generator must assert before it accepts a layout.
- **104** gains: every hex must be reachable, which is now a hard assertion the
  validator makes rather than a preference; levels are signed and there are
  fewer of them than there are designed ghosts; a cleared level does not
  persist; and the entrance is no longer an input to the ghost-room search but
  an output of it.
- **107** is rewritten around one room becoming infested per iteration, chosen
  from uninfested rooms with no hero in them, weighted by how long each has sat
  empty. The old per-room countdown is gone. Also: a woken haunted toilet
  infests its room the same way, and the hero who woke it becomes a crybaby who
  flees to the room they came from.
- **410** keeps reinforcements spawned from connected infested rooms, and gains
  that the whole waiting party enters at once when the door opens, and that a
  hero who wanders into a fight already happening joins it.
- **501** gains the guild's size, about twenty, and that a caregiver is not
  necessarily a healer, which shortens the in-combat order.
- **504** is rewritten around her wander: a weighted random walk over the doors
  out of the room a hero stands in, a never-visited room weighing most and then
  rooms by how long since anyone was there. Plus: the party identifies the ghost
  room and builds a basecamp beside it, and the leader is the one who deals with
  the ghost.
- **505** gains the all-enter-at-once rule and the merging of two calling queues
  toward the easier room, with ties broken per hero and re-checked on arrival,
  and why that converges.
- **506** gains the woken-toilet consequence.
- **508** gains that every basecamp captured means the guild is forced off the
  level and starts it again from the beginning.
- **713** is rewritten around her level rules: fewer levels than designed
  ghosts, the player choosing up or down on clearing one, difficulty and reward
  rising with distance from the ground, lower levels toward nature and higher
  toward crystal, marble and brass, and no level persisting once cleared.
- **714** gains the level themes for what the intro must set up.
- **phase-1-progress.md**: update its Blocking line to name the questions that
  actually still block phase 1, now that these are answered.

When done, reply with: each file and its word count, the balance-table entries
you named that do not exist yet (dotted name and one line of meaning), and any
new open questions (topic plus one sentence). Nothing else.

--------------------------------------------------------------------------------

### Assistant Response 1

> I'll update the twelve issue files to match her settled answers — citations
> and bodies both.

> Now I'll rewrite them. Starting with 106, which her answer replaces outright.

All twelve pass the validator with no stale citations.

**Files and word counts**

| File | Words |
| --- | --- |
| issues/104-the-hex-map-is-built-by-a-tool.md | 1483 |
| issues/106-the-ghost-room-is-the-farthest-by-an-unlock-aware-flood.md | 1670 |
| issues/107-a-room-fills-with-monsters-when-nobody-is-in-it.md | 1586 |
| issues/410-reinforcements-from-connected-rooms.md | 923 |
| issues/501-the-priority-table.md | 1464 |
| issues/504-exploring-and-heading-for-the-ghost-room.md | 1491 |
| issues/505-the-wait-the-call-and-the-safety-estimate.md | 1347 |
| issues/506-toilets-seeking-sensation-and-the-retry-lock.md | 1117 |
| issues/508-going-home.md | 912 |
| issues/713-levels-up-and-down.md | 1781 |
| issues/714-the-intro.md | 967 |
| issues/phase-1-progress.md | 645 |

**Balance entries named that do not exist yet**

- `map.locked_door_detour_multiplier` — what a key detour costs per room of
  distance when pricing a locked door; two, being out and back.
- `map.levels_fewer_than_ghosts` — how much smaller the reachable span of
  level indices is than the ghost catalogue's length.
- `map.difficulty_per_step_from_ground` — how much harder a level gets per
  step of absolute index.
- `map.reward_per_step_from_ground` — how much better the rewards get per
  step; deliberately a separate curve from the one above.
- `room.infestation_interval` — ticks between one room becoming infested.
  Supersedes `room.infestation_ticks`, which described the per-room countdown
  that no longer exists.
- `room.infestation_choice` — the word selecting how the drip picks its
  candidate; ruled as weighting by time sat empty.
- `basecamp.build_duration` — ticks the party spends building the camp beside
  the ghost room.
- `basecamp.build_cost` — gold the build takes from the guild's purse.
- `explore.never_visited_weight` — the weight a never-entered neighbour
  carries in the wander.
- `explore.weight_per_tick_unvisited` — how fast a visited neighbour's weight
  grows with time since anyone was there.
- `monster.tier_worth` — how many monsters of the tier below one monster of a
  tier counts as, in the safety estimate; her figure is two.

**New open questions**

- **Entrance and ghost room as drip candidates.** Her rule says every room can
  be infested, so 107 takes both as candidates, reversing the old permanent
  exemption; she has not been asked directly.
- **Expulsion regenerates what.** "Start over at the beginning of the level"
  reads as the same level from the same seed; 508 and 713 both rule that way and
  both flag it.
- **The journal after expulsion.** Whether clues gathered on a level survive
  being thrown off it.
- **Very short longest journeys.** A compact loopy level can put the ghost three
  rooms from the front door; whether to reject and re-roll.
- **Drip pace within a level.** Whether the interval holds one pace or tightens
  as the level goes on.
- **A lone waiter never gives up.** The wait row sits above the wander row and
  nothing times it out, so one hero at a door with no neighbours to call stands
  still forever while the drip keeps turning rooms.
- **How far a call carries.** Her phrase is "within calling distance"; the
  document has one room through a door, and whether a locked door blocks it is
  unasked.
- **Fog and the wander.** The wander ignores fog on the reading that fog is the
  player's knowledge, not the hero's; not put to her.
- **A fled crier nobody calms.** The corner crier stops when the battle ends;
  the one who fled a woken toilet has no battle to end.
- **Who can calm a fled crier.** Anyone, by the holding rule, or only a
  caregiver.
- **More than one built basecamp.** Only the one beside the ghost room is
  described, with no trigger for others.
- **Whether the outline grows with depth**, so deeper levels are bigger as well
  as harder.

--------------------------------------------------------------------------------

