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

`snapshot-id` should identify an exact upstream revision/version/digest. For Git-backed sources, use or record the exact commit SHA rather than a branch name.

## Rules

1. **Copy, do not link.** A snapshot must be self-contained in the Project. Do not use symlinks, floating branches, `latest`, or remote fetches as authority.
2. **Adoption requires a Decision.** Rules do not become authoritative merely because they are present.
3. **Snapshots are immutable by identity.** Once materialised under a snapshot ID, do not edit it in place, even before adoption.
4. **Adopted snapshots are retained.** Once referenced by an accepted Decision, do not delete the snapshot while historical Decisions depend on it.
5. **Updates are additive.** Import a new sibling snapshot and accept a superseding/updating Decision.
6. **Keep old snapshots.** Historical Decisions must remain reconstructable.
7. **Keep local exceptions out of copied Rule files.** Express scope/exceptions through Project Decisions.
8. **No silent upstream updates.** A newer upstream Ruleset may be discovered or proposed but does not alter Project authority until deliberately adopted.

The snapshot should include enough provenance to identify its source and exact revision/version/digest, but provenance does not itself confer authority.
