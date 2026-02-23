---
name: sync-upstream
description: Check the upstream pandoc-templates remote for new tagged releases and merge the latest one, preserving local customizations in default.latex.
---

# Sync upstream pandoc-templates

## Step 1: Check for new upstream tags

```
git fetch upstream --tags
```

Compare the current sync state (recorded in CLAUDE.md under "Current state") against the latest upstream tags:

```
git tag -l --sort=-version:refname | head -10
```

Report the current synced version and the latest available tag. If already up to date, stop here.

## Step 2: Merge the target tag

Merge the latest tag (or a user-specified tag) without committing, so conflicts can be resolved:

```
git merge <tag> --no-commit
```

## Step 3: Resolve `default.latex` conflicts

This is the file most likely to conflict, because it contains local customization blocks. To resolve:

1. Before accepting upstream, use `git diff default.latex` to inspect the current customizations and understand what needs to be preserved.
2. Accept the upstream version: `git checkout --theirs default.latex && git add default.latex`
3. Reapply the local customization blocks identified in step 1, placing them in the same relative positions within the template structure.
4. Read back `default.latex` to verify the customizations are in place.

## Step 4: Resolve other conflicts

- For any other conflicted files, prefer accepting upstream unless they contain local customizations.
- Delete stale merge artifacts if present (`default.latex.orig`, `default.latex.rej`).

## Step 5: Update CLAUDE.md

Update the "Current state" line in CLAUDE.md to record the newly synced tag.

## Step 6: Commit

Commit the merge with a message like:

```
Merge upstream pandoc-templates tag <tag>

<brief summary of what changed upstream>. Preserves local customizations:
IBM Plex font support (plex variable) and compact title block spacing.
```

## Step 7: Verify

- Confirm `letter-mason.latex`, `mason-letterhead.pdf`, `mullen-signature.pdf`, and `CLAUDE.md` still exist.
- Confirm both customization blocks are present in `default.latex`.
- Run `git log --oneline -5` to show the merge commit.
