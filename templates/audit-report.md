# Unity studio audit — [game name]

Template only. Replace placeholders with observed evidence; remove unused example rows. An unperformed audit has no findings or score.

Apply the kit's `docs/accuracy-and-verification.md`. Conclusions apply to the inspected evidence and scope; this report cannot establish 100% correctness. Resolve copied links from the final output folder, and retain unknowns instead of fabricating values.

## Executive summary

- Audit outcome for the stated scope: [two or three sentences with finding/evidence references].
- Most consequential verified issue: [AUD-### + evidence / none established].
- Highest-value next decision: [action, reason, dependency, uncertainty].
- Strength worth preserving: [observed quality and evidence / not assessed].
- Overall rating: **Unrated**. [Only add a rating if a defined rubric, sufficient coverage, and evidence justify it.]

## Baseline and evidence provenance

| Field | Recorded value |
| --- | --- |
| Target repository / original path | [URL] / [absolute path] |
| Commit / branch / dirty state | [full SHA] / [branch] / [clean, dirty, unknown; snapshot reference] |
| Audit window / auditor | [start–end, UTC] / [name or agent] |
| Unity version / renderer | [exact version] / [pipeline and version; source] |
| Platform / OS / graphics API | [target and actually tested environment] |
| Build identity / type / backend | [artifact ID, source association, Development/Release, Mono/IL2CPP/unknown] |
| Hardware / display | [CPU, GPU, RAM, device, resolution, refresh rate, scaling] |
| Input / locale / accessibility settings | [actually used configuration] |
| Isolation / accounts / saves / services | [approved copy, output paths, test fixtures, permitted endpoints] |
| Evidence root / report location | [toolkit report directory outside original game] |
| Baseline integrity after audit | [verification performed and result / not verified; reason] |

Dirty work and a built artifact can differ from the named commit. Explain the exact relationship or record it as unknown. Link evidence with timestamps and source provenance; do not expose credentials or personal data.

## Scope, method, and limitations

- Requested scope and product intent: [brief reference; confirmed requirements vs assumptions].
- In scope / exclusions: [flows, disciplines, platforms, scenes].
- Limitations affecting conclusions: [access, unavailable build, short session, simulator, missing references].
- Human observations vs AI analysis: [identify who observed what; synthetic personas are analytical perspectives].
- Critical review: [actual independent review or self-review; evidence challenged, contradictions resolved or outstanding, corrected/retracted finding IDs].

| Action | Status: performed / planned / blocked | Actual environment and evidence | Limitation / next step |
| --- | --- | --- | --- |
| [read source / inspect screenshot / run flow] | [status] | [timestamp and evidence; none if not performed] | [limit] |

## Coverage

Use only `Checked`, `Partially checked`, `Not checked`, `Blocked`, or `Not applicable`. `Checked` describes completion of the stated check, not a guarantee that the area has no defects. Explain every exclusion and blocked item.

| Discipline / check boundary | Coverage | Evidence or reason | Remaining work |
| --- | --- | --- | --- |
| Gameplay, progression, balance | Not checked | [evidence / reason] | [work] |
| Bugs, stability, saves, services | Not checked | [evidence / reason] | [work] |
| UX, onboarding, navigation, feedback | Not checked | [evidence / reason] | [work] |
| Layout, responsive UI, input, accessibility | Not checked | [evidence / reason] | [work] |
| Art, animation, style consistency | Not checked | [evidence / reason] | [work] |
| Sound, music, mixing, audio feedback | Not checked | [evidence / reason] | [work] |
| Performance, builds, platform behavior | Not checked | [evidence / reason] | [work] |
| Removal candidates and reference tracing | Not checked | [evidence / reason] | [work] |

Detailed check log: [coverage.md or inline records]. Missing evidence belongs here unless separate evidence establishes a product finding.

## Prioritized backlog

Types: `Defect`, `Risk`, `Design opportunity`, `Missing requirement`, `Removal candidate`.
Confidence: `Confirmed`, `Likely`, `Possible`. Severity: `Critical`, `High`, `Medium`, `Low`, `Informational`.
Priority: `P0`, `P1`, `P2`, `P3`; justify independently from severity using urgency, exposure, dependencies, and effort uncertainty.

| ID / title | Type | Confidence | Severity | Priority and rationale | Evidence | Next action / dependency |
| --- | --- | --- | --- | --- | --- | --- |
| [AUD-001 — title] | [type] | [confidence] | [severity] | [P#; why now/later] | [reference] | [investigate / plan; dependency] |

## Detailed findings

Copy the complete `templates/finding.md` record for **every** backlog item here or into `findings.md`, then link each ID to its record. Include the observation, expected-behavior source, evidence, reproduction or inspection steps, impact, uncertainty, root-cause status, recommendation, and observable acceptance criteria. Do not publish backlog rows without supporting records.

[Insert records or linked findings.md here. If no findings were established, state that with the coverage limitation.]

## Strengths and preservation constraints

| Observed strength | Evidence / scope | What future work should preserve |
| --- | --- | --- |
| [specific behavior or presentation quality] | [reference; actually observed] | [constraint] |

## Art and UI recommendations

When relevant, use `templates/art-ui-redesign.md` to produce [art-ui-redesign.md or an inline brief]. Review suitability against the game's goals and actual visual/interaction evidence. Keep missing evidence in coverage; do not infer poor design from missing screenshots.

| Screen / art system | Finding IDs and evidence | Strategy | Expected benefit / preserved strengths | Direction selection |
| --- | --- | --- | --- | --- |
| [name and state] | [AUD-### / evidence] | [Keep / Enhance / Restructure / Redesign / Investigate] | [benefit / preserve] | [pending / selected with user instruction reference] |

Record meaningful alternatives for substantial changes and measurable acceptance criteria in the brief. A recommendation or concept does not authorize game changes. Identify requested concepts as proposals and keep them separate from actual rendered or interaction results.

## Removal candidate review

No asset, component, scene, code, package, or feature is approved for removal by this report. Use `templates/removal-review.md`; include GUID, serialized and runtime references, external/content delivery usage, alternatives, owner decision, and rollback.

| Finding / candidate | Evidence and unknown references | Proposed disposition | Approval state |
| --- | --- | --- | --- |
| [AUD-### / item] | [reference] | [Keep / Rework / Defer / Remove candidate] | [not approved / exact later authorization reference] |

Full review: [removal-candidates.md or inline record].

## Future implementation prompts and decisions

- Prompt handoff: [implementation-prompts.md; use templates/implementation-task.md].
- Default mode: `PLAN_ONLY`. Uncertain findings become investigation tasks; fixes require explicit user authorization for finding IDs and scope.
- Decisions needed: [concrete options, supporting evidence, affected findings].
- Planned verification: [acceptance criteria, platform matrix, independent reviewer; clearly not yet performed].
- Implementation readiness: [grounded tasks vs investigations; existing targets/APIs checked, proposed additions labeled, essential unknowns and next evidence].
- Open coverage work: [highest-value unperformed checks and prerequisites].

## Evidence index

| Evidence ID / relative path | Captured at (UTC) | Source / observer | What it supports | Limits |
| --- | --- | --- | --- | --- |
| [E-001 / evidence/file] | [timestamp] | [build/commit, tool or person] | [AUD-### / coverage item] | [context missing / none known] |

Label evidence as directly inspected, supplied, or actually executed; distinguish it from planned protocols. Preserve the commit/build plus dirty-state association and flag stale or contradictory evidence. Audit confidence in a symptom does not establish the proposed cause or prove a later fix. Keep original criterion IDs for the later `verification-report.md`.
