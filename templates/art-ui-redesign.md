# Art and UI redesign brief — [game / review scope]

Template only; complete from supplied evidence. No target game or visual verdict is implied.
Mode: `AUDIT_ONLY`. Save this report as `art-ui-redesign.md` in the agreed report directory outside the target game.
Keep original code, scenes, prefabs, assets, `.meta` files, packages, and settings unchanged.

## 1. Baseline, intent, and inputs

| Field | Value / source / uncertainty |
| --- | --- |
| Target and baseline | [repository/path; branch, commit or unknown-ref; dirty snapshot; build] |
| Genre and player experience | [existing genre, core activities, tone, session context; intent source] |
| Audience | [intended players, familiarity, needs; source or hypothesis] |
| Platforms and input | [supported hardware, viewing distance, resolution/aspect, safe areas, input] |
| Constraints | [milestone, budget, team skills, localization, accessibility, performance budgets] |
| Existing visual direction | [palette, shapes, materials, typography, lighting; sourced style goals] |
| Screens and art systems sampled | [named screens, flows, scenes, camera distances, quality/state variants] |
| Available inputs | [captures, video, requirements, source, human feedback, runtime/audio access] |
| Style references | [supplied/approved reference, provenance, relevant trait, limitation] |
| Missing evidence and next input | [specific capture/state/requirement needed; owner if known] |
| Output and privacy | [report path; permitted access to private captures and references] |

References explain a proposed trait; they do not establish that another game's style suits this game.
Preserve the intended genre and identity unless the user explicitly requests a change.

## 2. Evidence and fit assessment

| Evidence ID | Existing source / exact location | Baseline and viewing context | Supports / limitations |
| --- | --- | --- | --- |
| [E-###] | [capture/path/timecode, scene/object, requirement, feedback source] | [build, state, device, viewport, input] | [direct observation; unsupported claims] |

- Evidence coverage: [Checked / Partially checked / Not checked / Blocked / Not applicable; rationale].
- Method: [rendered capture review / recorded interaction / source inspection / actual player report].
- Uninspected states and sampling limits: [list; explain relevance].
- Source review and plans cannot establish rendered aesthetics, runtime usability, motion, audio quality, or measured performance.
- Without visual evidence, mark visual fit **Uncertain** and specify the needed capture; do not issue an aesthetic verdict.

Judge fit against the intended experience and evidenced player tasks, rather than personal taste.

| Dimension | Fit: Supported / Misaligned / Uncertain | Evidence and reasoning | Strength to preserve / open question |
| --- | --- | --- | --- |
| Genre and intended experience | [judgment] | [E-###; intended activity and consequence] | [value already delivered] |
| Audience and accessibility | [judgment] | [E-###; affected player need; hypothesis if untested] | [strength / missing input] |
| Platform, display, and input | [judgment] | [E-###; specified conditions] | [strength / missing input] |
| Visual identity and cohesion | [judgment] | [E-###; established direction and observable consistency] | [distinctive features] |

### Recommended strategy

Select per screen/system; these strategies do not replace finding type, confidence, priority, or resolution state.

| Strategy | When justified |
| --- | --- |
| Keep | [Current evidence supports the design for its task; preserve documented strengths.] |
| Enhance | [Targeted legibility, feedback, consistency, or art improvements retain the structure.] |
| Restructure | [Evidence supports changing hierarchy, layout, grouping, or flow while retaining useful identity/assets.] |
| Redesign | [A broader direction addresses an evidenced mismatch or explicit new goal; explain why its benefits justify the change over viable smaller options.] |
| Investigate | [Intent, visual evidence, behavior, or causes are too uncertain to choose a change.] |

- Overall recommendation and boundaries: [strategy; affected scope; expected player benefit].
- Why this extent of change is warranted: [E-###; smaller viable change and its limitations].
- Stable findings: [link existing AUD-### records; create new IDs only for evidence-backed findings].

## 3. Screen or art-system brief — [name] (repeat for each affected area)

### Observation and intended outcome

- Screen/system and states: [named screen, scene, art family, flow entry/exit, relevant variants].
- Player task and context: [who needs to do what; platform/input; gameplay pressure or viewing distance].
- Linked findings: [AUD-### and record paths; reuse IDs for a shared root cause].
- Observed problem or opportunity: [specific visible/behavioral observation; E-### and locator].
- Expected behavior and basis: [requirement reference, established behavior, or clearly labeled proposal].
- Impact and confidence: [observed vs predicted consequence; confidence from linked finding].
- Fit and strategy: [Supported / Misaligned / Uncertain] / [Keep / Enhance / Restructure / Redesign / Investigate].
- Cause status and next check: [Known / Hypothesis / Unknown; evidence; bounded investigation if uncertain].
- Preserve: [successful layout/flow, recognizable silhouettes, style, assets, accessibility, learned controls].
- Boundaries: [specific affected screens/assets; adjacent behavior that must keep working].

### Proposed design specification

Fill applicable rows with concrete changes; use `Keep` or `Not applicable` with a reason elsewhere.
Apply the kit's `docs/implementation-principles.md`: suitable Editor/asset authoring plus simple code, with proportionate modularity, required variation, and measured performance claims.

| Area | Existing evidence | Proposed behavior or visual treatment | Constraint / dependency |
| --- | --- | --- | --- |
| Layout and hierarchy | [E-###] | [primary/secondary regions, grouping, spacing, HUD occlusion, responsive rules] | [viewport/safe area] |
| Flow and navigation | [E-###] | [entry, action sequence, back/cancel, focus order and restoration] | [input and adjacent screens] |
| Typography | [E-###] | [type roles, size/scaling, wrapping, truncation, glyph/fallback rules] | [languages/viewing distance] |
| Color and contrast | [E-###] | [palette roles, foreground/background treatment, non-color cues] | [measured targets and source] |
| Icons and imagery | [E-###] | [silhouette/meaning, label pairing, scale, consistent asset treatment] | [recognition and reuse] |
| Interaction states | [E-###] | [idle, focus/hover, selected, disabled, pending, success, error, recovery] | [applicable state/input matrix] |
| Art direction | [E-###] | [shape, proportion, materials, detail, lighting, composition, animation/VFX role] | [existing identity; gameplay readability] |
| Authoring and behavior | [existing UI framework, setup, and code] | [Editor work, focused code, configurable data, required dynamic states] | [ownership, supported tools, remaining setup, measured budgets] |

### Alternatives and selection

Use alternatives proportionately: compare a material restructure/redesign with a credible smaller change or keeping the current approach. For a small local fix, one clear proposal is enough. Remove unused rows and add another direction only when it represents a meaningful choice.

| Option | Scope and expected benefit | Cost / migration / performance tradeoffs | Evidence still needed |
| --- | --- | --- | --- |
| A — [recommended direction] | [bounded changes and benefit] | [estimate and uncertainty; affected references/assets; budget risk] | [validation prerequisite] |
| B — [meaningful alternative] | [different approach to the same task] | [benefit lost/gained; implementation and maintenance impact] | [discriminating check] |
| Keep / smallest change | [preserve or minimally adjust; include when viable] | [avoided cost; unresolved impact] | [reason viable or insufficient] |

- Recommendation: [option and evidence-based rationale; disagreements and tradeoffs].
- Selection: [Pending user decision / selected by explicit user instruction; quote or reference the instruction].
- Execution scope: [none / existing explicit authorization for specified IDs and operations]. A recommended or selected concept alone authorizes no implementation.

### Acceptance criteria and verification plan — not run

Use observable pass/fail rules. Fill thresholds, target conditions, and their source or rationale before handoff.

| Criterion | Target conditions and pass/fail rule | Verification evidence to collect |
| --- | --- | --- |
| Task and flow | [Given state/input, action reaches destination in specified steps; back/cancel restores specified state.] | [interaction recording and result] |
| Layout and text | [Named labels remain unclipped and required controls reachable at every listed viewport, scale, and language.] | [rendered matrix; measured size/spacing where required] |
| Interaction and readability | [Listed controls show each required state; specified contrast/target-size thresholds meet cited goals.] | [state captures and measurement method] |
| Art identity and gameplay | [Named preserved features remain; specified targets/cues distinguishable at defined distance, lighting, and density.] | [gameplay captures; stated recognition-review protocol] |
| Regression and budget | [Existing behavior retained; agreed frame-time, memory, asset/reference, and migration checks meet sourced limits.] | [authorized isolated checks; measurement environment] |

- Unavailable checks: [coverage label, reason, prerequisite; leave results unknown].
- Human review needed: [specific audience/design question and actual feedback protocol; no invented approval].

## 4. Optional visual concepts

Only create mockups when requested and compatible tools are available; otherwise the written brief is sufficient.

- Requested scope and available tools: [instruction/reference; tool capability or limitation].
- Concept files and provenance: [outside-game paths; input references; named screen/state].
- Label each image **Existing capture**, **Annotated capture**, or **Proposed concept — not implemented or validated**; keep links to original evidence separate.
- Caption each concept with the intended changes, preserved strengths, assumptions, and unresolved states.
- Keep private captures within the agreed access boundary; do not publish them or send messages.

## 5. Future task handoff

Use [finding.md](finding.md) for full AUD records and [implementation-task.md](implementation-task.md) for each distinct task/shared cause.
In the completed brief, replace this instruction with links to the actual finding and task records, and verify those links from the final output folder.

| Finding IDs | Task kind / dependency | Future prompt location | Scope and acceptance references |
| --- | --- | --- | --- |
| [AUD-###] | [Investigate / Implement; prior evidence or selected direction] | [implementation-prompts.md anchor] | [screen brief, exact paths/operations, criteria] |

Prompts default to `PLAN_ONLY`; resolve later execution from the user's explicit authorized scope, including any approval already present.
Carry forward evidence, selected option or pending decision, preservation constraints, asset/GUID dependencies, migration, verification, and rollback.
Unknown or hypothetical causes remain investigation tasks. Report only checks actually performed; a brief, source inspection, or concept does not establish the actual game's rendered, runtime, or audible result.
