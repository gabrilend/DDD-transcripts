# Copying

**Double Diaper Dungeon is licensed under the GNU Affero General Public
License, version 3 or (at your option) any later version.**

    SPDX-License-Identifier: AGPL-3.0-or-later

The full text is in [LICENSE](LICENSE), verbatim from
<https://www.gnu.org/licenses/agpl-3.0.txt>. It has not been edited, and it
should not be.

## What the AGPL asks of you, in short

This is a summary for orientation and it is not the licence. Where this page
and `LICENSE` disagree, `LICENSE` is correct.

- You may run, read, modify, and share this, commercially or not.
- If you distribute it, or a modified version, you pass on the same freedoms
  and the source.
- **And if you run a modified version where people interact with it over a
  network, the people using it over that network must be offered the source
  too.** That is section 13, and it is the difference between the AGPL and
  the plain GPL.

This game is played alone on one machine, so section 13 is not the clause
that bites today. It is the clause that matters the day somebody puts a
version of this behind a web page and invites people in, which is exactly
the case where a plain GPL would let them keep their changes. The stricter
licence was chosen while there was nothing to lose by choosing it.

## Applying the notice to source files

Every source file carries the notice near the top, in that file's comment
syntax. For Lua:

    -- Double Diaper Dungeon — a roguelike auto-battler in a haunted daycare
    -- Copyright (C) 2026 gabrilend
    --
    -- This program is free software: you can redistribute it and/or modify it
    -- under the terms of the GNU Affero General Public License as published by
    -- the Free Software Foundation, either version 3 of the License, or (at
    -- your option) any later version.
    --
    -- This program is distributed in the hope that it will be useful, but
    -- WITHOUT ANY WARRANTY; without even the implied warranty of
    -- MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero
    -- General Public License for more details.
    --
    -- You should have received a copy of the GNU Affero General Public License
    -- along with this program. If not, see <https://www.gnu.org/licenses/>.
    --
    -- SPDX-License-Identifier: AGPL-3.0-or-later

**No person types that.** `./new-source-file` stamps it, and
`./fill-source-file` rewrites a body underneath it without ever disturbing
it. The standing rule of this project is to build the tool that makes the
thing rather than making the thing by hand, and a licence header is the
purest form of the boilerplate that rots when it is hand-copied: one file
missing it, another carrying a version from two years ago.

## What this covers

Everything in the repository: the simulation, the viewer, the tools, the
documents, the issue files, the catalogue tables, and the transcripts of the
conversations that produced them. The documents are not incidental here.
They are how the software is built, and rebuilding it means reading them, so
they are licensed with it.

## Her own writing

`notes/vision`, `notes/monster-ideas`, and the arrow lines she has written
into the pages throughout are hers, and are covered by the same licence as
the rest of the repository. The rule that an assistant does not edit them is
a rule about respect and authorship, not about copyright.
