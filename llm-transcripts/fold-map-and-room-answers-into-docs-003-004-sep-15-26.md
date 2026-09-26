# Conversation Summary: agent-a66f8d672a5c2afe9

Generated on: 2026-09-26 12:45:33
Models: claude-opus-5

--------------------------------------------------------------------------------

### User Request 1

Your directive: You are a fork with the whole design conversation in context.
The developer has answered open questions by writing arrow lines into
docs/020-open-questions.md. Fold her answers into the two documents you own, so
the documents say what the game does. Project root:
/mnt/cmdo/ritz/games/tq/ai-stuff/double-diaper-dungeon.

YOU OWN EXACTLY TWO FILES. Edit only these:
- docs/003-the-hex-map-and-its-doors.md
- docs/004-rooms-that-fill-with-monsters.md

Do NOT touch docs/020-open-questions.md, the balance table, any issue file, or
any other document. Do not run git. Another writer owns each of the others.

Read first: docs/001-what-this-game-is.md (the fixed vocabulary — use it and
no synonyms), your two documents as they stand, and assets/023-balance-table.lua
for entry names. House style: plain English, mechanism-level, no balance numbers
in prose (name the entry instead and link ../assets/023-balance-table.info.md),
every branch says what each path leads to, errors not fallbacks, nothing nil.

HER ANSWERS, VERBATIM. Treat each as settled design. Where one contradicts what
your document currently says, the document is wrong and you rewrite it.

C1, must every hex be reachable: "yes every hex must be reachable."

C2, levels: "fewer levels than there are ghosts that we've built and designed.
The player chooses up or down whenever they clear a level. The further you are
from ground level, the harder it is, the better the rewards etc, but sometimes a
player might choose to do an easier level to get their heroes levelled up
perhaps. Lower levels are closer to nature themes, higher levels are more
crystal, marble, and brass."

C3, arrival and the ghost room: "if every basecamp is captured they get forced
out of the level and you have to start over at the beginning of the level. The
guild arrives at one of the border rooms, randomly placed when we identify which
room(s) have the longest distance. Each end of the longest journey (taking into
account locked doors, so if you have to go out of the way 5 rooms to find a key
then that adds 10 steps (5 there and 5 back)) one of them at one end becomes the
ghost room, and the other becomes the entrance room. If it's not at the border,
try the other side. If neither are at the border, then that's okay make one of
them the entrance anyway, randomly chosen."

This REPLACES the current ghost-room algorithm. It is no longer "farthest from a
given entrance". It is the graph's longest journey: find the pair of rooms whose
weighted distance apart is greatest, where a locked door costs the whole detour
to its key and back (her example: a key five rooms out of the way adds ten
steps). One end becomes the entrance, the other the ghost room. Prefer an end
that sits on the grid's border; if only one end is on the border that end is the
entrance; if neither is, pick one at random. Say clearly how a generator
computes this and why the round-trip weighting is the honest measure of effort.

C4, infestation: "every room can be infested, but only one room will become
infested per iteration."

This REPLACES per-room independent timers. Infestation is now a global drip:
every uninfested room with no hero in it is a candidate, and one of them becomes
infested per iteration. Define "iteration" as a tick count in the balance
table's room group (name it room.infestation_interval and say it is
provisional), and say how a candidate is chosen — propose weighting by how
long the room has sat empty, so the longest-empty room is likeliest, and mark
that as a working ruling. Note what this buys: the number of infested rooms
grows at a rate the player can outrun, instead of every room counting down at
once.

C9, a woken haunted toilet: "idk what this question is asking. It infests the
room and the hero who triggered it automatically goes crybaby and runs to the
room they entered from. They'll sit and cry until someone comes and helps them
calm down, and then they'll both queue to fight the monster."

So: waking a haunted toilet infests that room like any infestation, and the hero
who woke it becomes a crybaby who RUNS to the room they came from and cries
there. That is a second kind of crybaby — the ordinary one sits in the corner
of the room it is in. When someone calms them, both of them join the wait at
that door.

C11, level persistence: "nah it doesn't persist. Once a floor is cleared, the
ghost room is purified and there's no more monsters there."

E7, reinforcements at the door: "Before the fight starts? Yeah they all enter at
once. If reinforcements wander into the room of their own accord (because they
heard fighting in the next room over and wanted to help) then they can help
fight."

D15, monster scaling: "more of them and more powerful monsters. See the monster
idea notes. Typically a monster tier should count as 2 of a lower tier."

Use that last one in the safety estimate: the party's reckoning of a room counts
a monster of each tier as two of the tier below, so the estimate has a unit.

ALSO: she has described a fog of war, in her answer to a question about
something else, and it belongs in your map document:

"Once you enter a room the fog of war is permanently cleared. You can see one
room over but you don't know what's in it, just that it exists, and whether or
not it's infested with monsters. If a room gets infested with monsters then the
fog of war comes back for that particular room, and any rooms that are gated by
that room. You can tell if they're 'gated' by tracing a path to any basecamp."

Write this as a real mechanic in docs/003: three states per room (unknown,
glimpsed, seen), how entering changes them, that a room adjacent to a seen room
is glimpsed and shows only that it exists and whether it is infested, and that
infestation re-fogs the room and everything gated behind it, where gated means
every path from it to any basecamp passes through it. Say how a generator or the
tick recomputes gating (a flood from the basecamps through unfogged, uninfested
rooms; anything unreached is gated). Note that this is the player's knowledge,
not the heroes' — say plainly whether a hero's own wandering uses it, and mark
that as a question for her if you cannot settle it from her words.

Also read notes/monster-ideas, which she wrote: three tiers of monsters, low,
medium and high, and a closing paragraph explaining that they are all buffed by
stolen ghost power. Reference it where D15 lands. Do not edit that file.

Each document keeps its "## Still open" section, updated: remove what she has
now answered, keep what she has not, and add anything new her answers raise. End
with the Related line as before.

When done, reply with: the word count of each file, a list of the balance-table
entries you named that do not exist yet (dotted names, one line each with what
it means), and any new open questions (topic plus one sentence). Nothing else.

--------------------------------------------------------------------------------

### Assistant Response 1

> I'll fold her answers into the two map and room documents I own.

> Now I'll rewrite the map document with her longest-journey rule, the fog of
> war, and the level answers.

> Now the rooms document, with the global drip, the tier unit, and the haunted
> toilet.

Both documents rewritten.

**Word counts**
- `docs/003-the-hex-map-and-its-doors.md` — 2662
- `docs/004-rooms-that-fill-with-monsters.md` — 2199

**Balance entries named that do not exist yet**
- `map.locked_door_detour_multiplier` — how many steps a key detour adds per
  room of distance; her example is two, five out and five back.
- `map.levels_fewer_than_ghosts` — how much smaller a run's reachable span of
  levels is than the ghost catalogue.
- `room.infestation_interval` — ticks between one room becoming infested.
  Supersedes `room.infestation_ticks`, which described the per-room timer the
  single clock replaces.
- `room.infestation_choice` — the word selecting how the candidate is picked;
  working ruling is weighting by how long the room has sat empty.
- `monster.tier_worth` — how many monsters of the tier below one monster of a
  tier counts as, in the safety estimate. Her figure is two.

**New open questions**
- Ghost room algorithm in the vocabulary page. `docs/001-what-this-game-is.md`
  still defines the ghost room as "the farthest room from the entrance", which
  her longest-journey answer replaces; that sentence needs changing by whoever
  owns that file, and `issues/106` is named for the old algorithm.
- Superseded balance entry. `room.infestation_ticks` now describes a mechanism
  that no longer exists and should be retired rather than left to be read as
  live.
- Entrance infestation. Whether the entrance is spared from the candidate pool
  the way the ghost room is, or can turn like anything else.
- Journal after expulsion. Whether being thrown off a level costs the clues
  already gathered, or only the map progress.
- Clock pace. Whether the infestation interval holds one pace for a whole level
  or tightens as the level goes on.
- Never-seen versus long-cleared. Whether a room the party has never entered
  should be a likelier candidate than one they cleared long ago, or whether time
  empty is the whole weighting.
- Doorway sight. Whether standing in a glimpsed room's doorway shows the player
  what is inside, or only walking in does.
- Low-health heroes inside. Everyone at the door enters together, so whether the
  low-health ones fight or hang back once through is now a live question rather
  than a question about entering.
- Difficulty and reward curves. Distance from the ground drives both; whether
  they are one curve or two, and how steep, is unset.

--------------------------------------------------------------------------------

