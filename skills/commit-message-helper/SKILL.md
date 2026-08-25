---
name: commit-message-helper
description: Write clear, well-structured commit messages for staged or described changes. Use when the user asks to write, draft, improve, or review a git commit message, or asks "what should the commit message be" for a diff or set of changes.
license: MIT
---

# Commit Message Helper

Write commit messages that explain **why** a change was made, not just what changed — the diff already shows the what.

## Process

1. Look at the actual change (`git diff --staged`, or the diff/description given). Don't guess from the request text alone.
2. Identify the underlying reason for the change: a bug being fixed, a capability being added, a constraint being worked around. If the reason isn't obvious from the diff or conversation, ask rather than invent one.
3. Check the repo's own history (`git log --oneline -10`) and any local convention (e.g. Conventional Commits, a CONTRIBUTING.md rule) and match it.

## Structure

- **Subject line**: imperative mood ("Fix", "Add", "Remove" — not "Fixed"/"Adds"), under ~72 characters, no trailing period.
- **Body** (optional, blank line after subject): 1-3 short sentences on *why*, only when the subject doesn't already make it obvious. Skip the body entirely for genuinely self-explanatory changes.
- Wrap body lines at ~72 characters if the project's history does.

## What to avoid

- Restating the diff line-by-line ("changed X to Y in file Z") — that's what `git show` is for.
- Vague subjects like "update code", "fix stuff", "misc changes".
- Mentioning unrelated changes that aren't in this commit.
- Adding a body just to have one — a good subject line alone is a complete commit message.

## Example

```
Fix race condition in session cleanup

Cleanup ran before pending writes flushed, occasionally dropping
the last few events on fast disconnects.
```
