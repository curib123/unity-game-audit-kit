# Removal review — [AUD-### / candidate]

This is a review record, not deletion authorization. A search with no matches does not establish that an item is unused, safe to remove, or valueless.

## Candidate and decision

| Field | Value |
| --- | --- |
| Candidate / exact paths | [feature, code, component, scene, prefab, asset, package, etc.] |
| Baseline | [repository/path, commit, dirty snapshot] |
| Associated finding / evidence | [AUD-### and evidence references] |
| Proposed disposition | [Keep / Rework / Defer / Remove candidate] |
| Current decision | [Pending; exact later user decision if available] |
| Explicit removal authorization | [none; approved candidate IDs, paths, operations, user reference] |
| Reason for consideration | [observed harm, duplication, cost, obsolete requirement; evidence] |
| Confidence and limits | [Confirmed / Likely / Possible; what remains unknown] |
| Owner / product intent | [known requirement and decision source / unknown] |

## Reference and usage investigation

Record the search boundary and results. Treat unavailable checks as coverage gaps. Include the candidate's `.meta` file and all relevant GUIDs; package or feature removal may have additional reference systems.

| Reference class | Search/check performed and boundary | Actual evidence / result | Coverage |
| --- | --- | --- | --- |
| Asset GUIDs and .meta relationships | [GUIDs, paths, sub-assets] | [reference] | [status] |
| Serialized scenes, prefabs, variants, ScriptableObjects | [including disabled objects and overrides] | [reference] | [status] |
| Code, reflection, string names, generated registrations | [assemblies and search scope] | [reference] | [status] |
| Resources.Load and dynamic asset/path loading | [names, conventions, configurations] | [reference] | [status] |
| Addressables, AssetBundles, remote catalogs/content | [groups, labels, external consumers] | [reference] | [status] |
| Build scenes/profiles, platform defines, conditional code | [platform-specific inclusion] | [reference] | [status] |
| Animation, Timeline, events, shaders/materials, audio | [indirect bindings and runtime selection] | [reference] | [status] |
| Saves, migrations, analytics, services, external tools | [compatibility and external references] | [reference] | [status] |
| Runtime flow and production/content usage | [actually executed or available historical evidence] | [reference] | [status] |

Coverage values: `Checked`, `Partially checked`, `Not checked`, `Blocked`, `Not applicable`. Document exact queries and tools where useful; do not treat text search as complete runtime reference tracing.

## Value, alternatives, and uncertainty

- Current player or production value: [observed value / unknown].
- Cost or harm if kept: [evidence; measured vs estimated].
- Consequence if removed: [flows, supported platforms, saves, content, users].
- Keep option: [reason and cost].
- Rework option: [smaller change that preserves value].
- Defer option: [missing evidence or prerequisite decision].
- Remove candidate option: [bounded scope and evidence needed for approval].
- Unresolved references and confidence limits: [list; never silently assume no use].
- Recommendation and rationale: [one disposition; cite evidence and uncertainties].

## Proposed removal and verification — not yet executed

- Exact files/assets/components and paired `.meta` files: [bounded manifest].
- Dependent edits / migration / cleanup: [paths, serialized references, configuration].
- Permitted isolated experiment: [only if explicitly authorized; copy and operations].
- Baseline comparison: [behavior, build contents/size, performance, errors as relevant].
- Acceptance criteria: [observable preserved behavior and eliminated cost/harm].
- Regression matrix: [scenes, saves, platforms, inputs, remote/offline behavior].
- Independent verification: [reviewer or separate check of reference and runtime evidence].

## Rollback and approval record

- Recovery snapshot: [commit/patch or complete asset + .meta backup preserving GUIDs].
- Restore procedure: [scoped steps, reference restoration, save/data compatibility].
- Rollback triggers and proof of restoration: [observable checks].
- Explicit user decision: [Pending / approved Keep / approved Rework / approved Defer / approved removal; reference].
- Authorized IDs, paths, and operations: [none until approved].
- Actual changes and verification: [leave unfilled during audit; evidence after approved work].
