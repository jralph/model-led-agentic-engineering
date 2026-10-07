# .rulesets

This directory contains local snapshots of reusable Rulesets adopted or evaluated by this Project.

A Ruleset is reusable normative material. It becomes Project authority only through a human-accepted Project Decision that adopts a specific local snapshot.

## Layout

Recommended layout:

```text
.rulesets/
  <ruleset-name>/
    <snapshot-id>/
      ...
```

`snapshot-id` should identify an exact upstream revision/version/digest.

## Rules

1. **Copy, do not link.** A snapshot must be self-contained in the Project. Do not use symlinks, floating branches, `latest`, or remote fetches as authority.
2. **Adoption requires a Decision.** Rules do not become authoritative merely because they are present.
3. **Adopted snapshots are immutable.** Once referenced by an accepted Decision, do not edit or delete the snapshot.
4. **Updates are additive.** Import a new sibling snapshot and accept a superseding/updating Decision.
5. **Keep old snapshots.** Historical Decisions must remain reconstructable.
6. **Keep local exceptions out of copied Rule files.** Express scope/exceptions through Project Decisions.
7. **No silent upstream updates.** A newer upstream Ruleset may be discovered or proposed but does not alter Project authority until deliberately adopted.

The snapshot should include enough provenance to identify its source and exact revision/version/digest, but provenance does not itself confer authority.
