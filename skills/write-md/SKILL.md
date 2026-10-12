---
name: write-md
description: Use when you write or edit a Markdown document — a README, a report, a plan, a handover, a doc under docs/. Removes the filler that language models add and keeps the statements a reader acts on.
metadata:
  source: https://github.com/dsl400/write-md
  version: 0.1.0
---

# write-md

A document holds statements a reader acts on. Each check below names one kind
of filler, a sample that has it, and the same text without it.

## Checks

### State the claim directly

The contrast "not X, but Y" adds a false depth: it names X only to reject it.
Write Y.

| Filler | Direct |
|---|---|
| This is not a bug, but a design choice. | This is a design choice: the cache keeps stale entries for 5 s. |
| The goal is not speed, it is correctness. | The goal is correctness. |
| It's not just a linter — it's a workflow. | It lints and fixes the file in one run. |

### Count only when the number is the information

A count of the items next to it repeats the list and goes wrong when the list
changes.

| Filler | Direct |
|---|---|
| The install has three steps: | The install has these steps: |
| `## 1. Source` · `## 2. Build` | `## Source` · `## Build` |
| I changed 4 files: a, b, c, d. | I changed a, b, c, d. |
| Here are 5 key takeaways: | (the list alone) |

Keep a count that the reader needs and cannot see: "12 of 40 tests fail",
"the queue holds 3 000 jobs".

### Name the action to take

A negated instruction names the wrong action and leaves the right one open.

| Filler | Direct |
|---|---|
| Do not edit the generated file. | Edit `src/cli.js`; `lnl.mjs` is built from it. |
| Don't forget to restart the service. | Restart the service. |

### Drop the frame around the content

Remove each sentence that announces, praises, or repeats the content.

| Filler | Direct |
|---|---|
| It's worth noting that the token expires. | The token expires after 1 h. |
| Great question! The answer is X. | X. |
| In summary, … (repeats the sections above) | (remove) |
| This robust, seamless, powerful tool … | The tool … (plus the fact the adjective claimed) |

### Write for one reader

A document for the agent that does the work holds the commands, paths,
values, and shapes it needs. A document for the person who changes the system
holds the reasons and the measurements. Move each sentence to the document of
its reader.

### Put the reason next to the value

Each threshold, limit, and choice carries one sentence with its reason: what
it does, and what moves when it changes.

| Filler | Direct |
|---|---|
| `NOTIFY_ENTRIES = 20` | `NOTIFY_ENTRIES = 20` — the panel shows 20 lines without a scroll bar. |

### Describe what exists

Each heading and each line names something the system holds today. Remove
each trace of what went away: "previously", "no longer", "we removed", "now
uses".

### Show the shape

Write a sample of a format in place of a sentence about it.

### Name the subject in a heading

A heading is a noun phrase: `## Install`, `## Release workflow`.

## Flow

```lnl
START:
  DO    read the document from the first line to the last
CHECK_ALL:
  ADD   1 to <c>
  STOP  show the remaining findings and ask the human how to continue IF <c> >= 4
  DO    apply each check of this file to each sentence and heading, and list each finding with its line
  ASK   does a finding remain?
  JUMP  REVIEW IF no
  DO    rewrite each line of a finding to its direct form
  JUMP  CHECK_ALL
REVIEW:
  CHECK each sentence states a claim, an action, or a value
  CHECK each count left in the document is information the reader cannot see
REPLY:
  SAY   the document is written, and the findings a STOP left open
  END
```
