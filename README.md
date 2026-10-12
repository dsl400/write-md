# write-md

A skill for Claude Code that removes the filler language models add to
Markdown documents: rhetorical contrasts ("not X, but Y"), counts of the list
next to them, negated instructions, announcements and recaps, and traces of
what went away.

The skill is `skills/write-md/SKILL.md`. Its flow is written in
[lnl](https://github.com/dsl400/lnl).

## Why each check exists

- **Direct claims.** "Not X, but Y" names X to reject it. The reader holds
  both, and the sentence reads deeper than it is.
- **No counts of a visible list.** The count repeats the list and turns false
  the moment an item is added or removed.
- **Named actions.** "Do not do X" puts X in front of the reader and leaves
  the right action unnamed.
- **No frame.** Announcements, praise, and recaps cost reading time and carry
  no fact.
- **One reader.** An agent that does the work needs values and commands; a
  person who changes the system needs reasons. Mixed, each reads the other's
  part as noise.
- **Reason next to the value.** A value with no reason invites the next
  change to undo it.
- **What exists.** History in a document describes a system that is gone.

Specifications are out of scope: [spec-writer](https://github.com/dsl400/spec-writer)
writes them and checks them with ste-check.

## Install

```sh
gh release download --repo dsl400/write-md --pattern write-md.tar.gz -O - | tar -xz -C ~/.claude/skills
```

Or as part of [dsl400/skills](https://github.com/dsl400/skills).
