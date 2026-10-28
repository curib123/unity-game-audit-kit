# Unity change verification — [game / selected findings]

Template only. Replace placeholders with actual evidence; no verification results are implied by this file.
Use [accuracy and verification](../docs/accuracy-and-verification.md) and [implementation principles](../docs/implementation-principles.md). These links are relative to this source template; when copying into `reports/`, update them to the actual kit destinations.

## Scope and authority

- Mode / selected findings: `VERIFY_ONLY` / [AUD-###; linked original findings and implementation tasks].
- Request and existing authorization: [exact instruction or reference; authorized checks and scope]. Honor authorization already given; this report grants no additional operations.
- Included behavior / required regressions / exclusions: [bounded selection and requirement sources].
- Original game / isolated validation copy / report directory: [actual paths; report outside original game].
- Permitted validation: [existing evidence, static review, specific Editor/test/build/device operations].
- Isolation: [permitted test services, accounts, fixtures, isolated saves and outputs; unavailable prerequisites].
- Reviewer / time window: [actual person or agent; UTC].

Verification cannot auto-fix, clear Console/log evidence, weaken tests, change packages, or complete missing Editor setup. Preserve the original game's read-only boundary and existing edits. Run writing operations only within authorized isolated runtime scope; never use production services or player data. Continue with available evidence when checks are unavailable.

## Baseline, final state, and environment

| Field | Actual value and evidence locator |
| --- | --- |
| Audit baseline | [repository, branch, full commit or unknown-ref; original finding evidence] |
| Implementation starting state | [commit; staged, unstaged, untracked state; dirty snapshot/patch identity] |
| Final implementation state verified | [commit plus final dirty/snapshot identity, including relevant uncommitted assets; captured at UTC] |
| Baseline-to-final diff | [actual range or snapshot comparison; changed paths; unrelated changes/scope drift] |
| Unity / relevant packages / renderer | [exact Editor, package/lock, pipeline versions and sources; unknown where unavailable] |
| Target / actual platform | [OS, graphics API, build configuration/backend, Editor vs player] |
| Build identity and source association | [artifact ID/hash; build source commit and dirty snapshot, or association unknown] |
| Required device / display / input | [actual hardware, resolution, scaling, input, locale/accessibility settings relevant to change] |
| Required scenes / states / data | [scene, content/version, save fixture, seed, configuration and service conditions] |
| Conditions not assessed | [required but unavailable environments and impact; unaffected fields with reason] |

A commit alone does not identify dirty work or prove a built artifact matches it. Bind each conclusion to the final state above. Earlier evidence affected by later edits must be repeated or marked stale; unknown source/build association cannot substantiate a current implementation claim.

## Acceptance contract — recorded before testing

Keep stable finding and criterion IDs, including required regression criteria. Preserve original wording and pass/fail rules; an implementation report is not a requirement source. Document criteria agreed before testing and identify any later revisions explicitly.

| Finding / criterion ID | Original requirement and source | Observable pass/fail rule and required conditions | Required / optional | Agreement source / date |
| --- | --- | --- | --- | --- |
| [AUD-### / AC-# or REG-#] | [exact criterion; finding/task/brief locator] | [behavior or threshold, method, relevant cases/platforms] | [value] | [existing agreement/reference] |

| Criterion ID | Original → revised criterion | Reason and effect on scope | Explicit authorization/source / date |
| --- | --- | --- | --- |
| [ID; or no revisions] | [retain original and revised wording] | [explanation] | [verifiable source; pending changes do not replace agreed criteria] |

Never quietly weaken criteria, thresholds, or tests to fit the result; preserve any outcome already observed against original criteria. Record `Not applicable` separately before omitting a check; include its reason and requirement/scope source. Missing access or a skipped run does not make a required check inapplicable.

| Criterion / check marked Not applicable | Reason | Requirement/scope source |
| --- | --- | --- |
| [ID/check; or none] | [why unaffected/outside agreed scope] | [locator] |

## Evidence index and execution records

Assign evidence IDs to actual observations and supplied artifacts. Label provenance `Executed here`, `Supplied`, `Static inspection`, or `Planned`. A plan is not an execution record; supplied evidence needs its source and source/build association. Preserve raw outputs and record limitations or contradictory evidence.

| Evidence ID / path | Provenance / observer / UTC | Commit/snapshot/build and environment | Supports | Current / stale / unmapped; limits |
| --- | --- | --- | --- | --- |
| [E-### / log, capture, file:line, artifact] | [value; actual source] | [identity or unknown; environment above] | [criterion IDs / baseline reproduction] | [validity and missing context] |

Repeat this execution/inspection record for each distinct method; use `not run` or `unknown`, never invented commands, counts, timings, or outputs.

- Check ID / evidence IDs / criterion IDs: [traceable IDs].
- Provenance and actual method: [executed command or precise manual/static procedure; tool/version; supplied record origin].
- Invocation and conditions: [working directory, test filter, scene/state, device/build/fixture; redact secrets].
- Execution state / time / exit code: [completed, failed, interrupted, not run; actual UTC and code if available].
- Results, where relevant: [discovered / run / passed / failed / skipped / inconclusive counts, or unknown/not applicable].
- Observed outcome: [actual behavior, compiler/test/build diagnostics, measurements; separate inference].
- Raw evidence / artifacts: [logs, result XML, build report, screenshots/video/audio/profile capture paths and identities].
- Limitations / remaining check: [what this method cannot establish; planned checks explicitly labeled].

A successful exit alone, zero relevant discovered/executed tests, skipped required tests, and planned runs do not establish a test criterion's pass. Record discovery, failures, skips, and incomplete output honestly. A failed tool invocation is not automatically a product defect.

## Criterion results

Use `Pass`, `Fail`, `Inconclusive`, or `Not run` for each applicable criterion. `Pass` requires sufficient evidence of its agreed result on the current final state; `Fail` requires evidence of a violated rule. Use `Inconclusive` for insufficient, stale, contradictory, or unmapped evidence, and `Not run` when no applicable check was performed. Record required cases separately where outcomes differ.

| Finding / criterion ID | Actual method / conditions | Evidence IDs and final-state match | Observed result vs pass rule | Result | Remaining gap / action |
| --- | --- | --- | --- | --- | --- |
| [AUD-### / AC-# or REG-#] | [performed method or not run] | [IDs / association] | [observation, or none] | [status] | [next prerequisite/check] |

Source inspection can pass a genuinely source-only criterion. Source review and compilation cannot prove visual, audible, interaction, runtime, build, device, or performance outcomes. Actual rendered captures, interaction observations, listening, builds, and profiling support only their demonstrated scope. Concept images and implementation descriptions are not runtime evidence.

Tests using mocks or synthetic fixtures establish only the layer and conditions exercised. Do not use them as evidence of real scene, asset, service, or device integration without the required integration checks.

## Before/after and relevant regression assessment

| Finding / scenario | Original reproduction and baseline evidence | Final-state steps and evidence | Outcome / failure origin | Remaining uncertainty |
| --- | --- | --- | --- | --- |
| [AUD-### / scenario] | [actual reproduction, supplied evidence, or not run] | [actual method/results or not run] | [resolved/persists/unresolved; pre-existing/introduced/unknown origin, with evidence] | [gap] |

Attribute a failure as pre-existing or introduced only when comparison evidence supports it. Unknown origin stays unknown. Keep newly discovered issues under stable new IDs linked to the affected finding; do not silently add them to implementation scope.

Record only checks relevant to the change, with criterion/evidence IDs; explain omitted required checks. If coverage needs a separate label, use `Checked`, `Partially checked`, `Not checked`, `Blocked`, or `Not applicable`. Coverage describes the extent reviewed, not whether a criterion passed.

- Final diff and authored setup: [current code plus actual serialized scene/prefab/asset changes, overrides, bindings, build inclusion, real `.meta`/GUID references; remaining Editor steps].
- Configuration/state and regressions: [ownership/reset, required variation, scene transitions, save compatibility, references/runtime loading and removal restore path as relevant].
- Art/UI/audio: [selected brief, preserved strengths, actual screens/states/displays, controls/accessibility, observed motion/listening; concept-only or absent evidence].
- Performance: [representative baseline and final captures with comparable device/build/settings/workload, metrics and method; otherwise improvement unverified].
- Platform/build/device: [required matrix, actual coverage, absent environments and consequences].

## Implementation completeness

Record `Planned`, `Partially implemented`, or `Implemented` from actual changed files and completed setup, separately from verification status. Required Inspector/scene wiring still pending means `Partially implemented`, even when code compiles; `Implemented` alone does not establish correctness.

| Finding ID | Actual changed files / completed setup and evidence | Completion state | Required work still pending |
| --- | --- | --- | --- |
| [AUD-###] | [paths, authored setup, evidence IDs] | [one state above] | [specific remaining setup or none established] |

Incomplete setup is `Failed` when evidence establishes an unmet required criterion. Otherwise use the appropriate `Blocked` or `Not verified` decision below; do not invent a failure or claim completion from absent evidence.

## Finding decisions

- `Verified`: every required acceptance criterion and required relevant regression is supported on the current final state; no unresolved required failure or evidence gap.
- `Failed`: a required criterion fails or the original issue persists. A known required failure takes precedence even when other checks are blocked.
- `Blocked`: no known required failure, but unavailable prerequisites prevent required validation; name the missing evidence/access/condition.
- `Not verified`: no known required failure, but review is incomplete or only a subset was assessed without a demonstrated blocker.

| Finding ID | Required criteria and regressions | Status | Supporting evidence / reasons | Remaining work |
| --- | --- | --- | --- | --- |
| [AUD-###] | [all applicable criterion IDs] | [one status above] | [evidence and unresolved gaps] | [specific next action] |

## Review method and preservation

- Actual review method: [independent reviewer, independent evidence method, or self-review; identity, work against original criteria and limitations]. Do not claim separate reviewers, agents, or sessions that did not occur.
- Final-state reconciliation: [reviewed final diff/snapshot and evidence association after checks; later modifications and stale evidence].
- Original preservation: [before/after HEAD plus staged, unstaged and untracked checks; actual results and evidence].
- Preservation limits: [ignored files, external saves/services, generated files or other state checked/not checked; a clean tracked diff is insufficient].
- Unexpected changes: [paths and circumstances, or none observed within checked scope; stop affected operation, disclose, do not hide through reset/clean/restore].

## Completion assessment and next actions

- Supported conclusion for this selection: [finding decisions and exact scope; distinguish reported implementation from verified behavior].
- Remaining failures, blockers and unperformed checks: [IDs, practical consequence, prerequisite and owner/next action].
- Follow-up investigation/fix prompts: [linked proposed tasks only; respect existing scope and authorization].
- Evidence-supported limits: [untested environments/states and residual uncertainty]. Do not claim 100% correctness or whole-game release readiness from this scoped verification.
