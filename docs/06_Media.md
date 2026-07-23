# Media (Update 05)

## Media Library Model

Media objects are immutable once imported.

Runtime metadata (play count, last used, failures) is stored separately.

## States

- Imported
- Validated
- Available
- Selected
- Playing
- Completed
- Disabled

Media files themselves are never modified by playback.
