# Evidence, confidence, and priorities

Use these rules across every studio discipline. The goal is a backlog a developer or designer can act on without guessing which statements are observations and which are proposals.

## Evidence contract

For each finding, record the target commit or build, date, relevant environment, evidence locator, observed behavior, intended behavior and its basis, impact, and limits. Evidence can be a source symbol and line, asset GUID and object path, screenshot region, recording timestamp, Console stack trace, test result, build log, or profiler capture and marker.

Prefer a pinned commit link or a path plus commit, rather than a moving branch link alone. For local edits, describe the dirty state and preserve a suitable baseline snapshot outside the target. Redact secrets and personal data without erasing the context necessary to understand the issue.

Keep three statements separate:

1. **Observation:** what the evidence directly shows.
2. **Interpretation:** why it may matter and what remains uncertain.
3. **Recommendation:** what should change or be investigated next.

A demonstrated symptom can be confirmed while its cause remains unknown. A source-level invariant violation can be confirmed by inspection when the reasoning is complete, but that does not mean the game was executed. Name the method and the limits.

## Finding types

| Type | Use when | Required distinction |
| --- | --- | --- |
| Defect | Evidence demonstrates incorrect behavior or a violated supported requirement. | State the failure and the expectation it violates. |
| Risk | Evidence suggests a failure mode that has not been demonstrated. | State the hypothesis and the check that would confirm or reject it. |
| Design opportunity | A change may improve the intended experience. | Explain player benefit, tradeoff, and the decision or experiment needed. |
| Missing requirement | A documented, agreed, or otherwise supported requirement is not met. | Cite that requirement; a genre convention alone is not mandatory. |
| Removal candidate | Something may be redundant, harmful, distracting, or obsolete. | Show dependency evidence and proposed validation; do not delete it. |

If evidence is unavailable, record a coverage gap. Do not manufacture a finding to fill a section. Avoid reporting the same underlying issue separately as a UI bug, a player problem, and a design problem; use one ID with multiple affected domains.

## Confidence

| Confidence | Meaning |
| --- | --- |
| Confirmed | Direct evidence establishes the stated observation or failure within the recorded scope. |
| Likely | Several consistent signals support the claim; material validation is still missing. |
| Possible | The hypothesis is plausible but evidence is incomplete. |

Confidence is about the claim's support. It is separate from severity and from whether the proposed fix is correct. For a design opportunity, confidence can apply to an observed obstacle; it does not prove the proposed design will solve it. Use an experiment when that remains uncertain.

## Severity: consequence if the finding applies

| Severity | Consequence |
| --- | --- |
| Critical | Data loss, consistent crash, a blocked required production build, serious security exposure, or comparably severe integrity failure. |
| High | A major supported feature fails, progression is blocked, serious compatibility problems occur, or measured performance prevents intended play. |
| Medium | A meaningful localized correctness, usability, accessibility, performance, or workflow problem. |
| Low | A limited-impact problem or improvement with a workable recovery path. |
| Informational | An observation, decision, or optional idea with no demonstrated immediate harm. |

Always explain impact. Do not inflate naming preferences, aesthetic tastes, speculative performance risks, or broad rewrites to High severity. An accessibility issue may be severe when it blocks a supported core interaction; evaluate actual impact rather than treating accessibility as cosmetic.

## Priority: when to act

| Priority | Recommended timing |
| --- | --- |
| P0 | Immediate triage; a demonstrated release blocker or severe risk requiring urgent investigation. |
| P1 | Before the next relevant milestone or external test. |
| P2 | Planned work after blockers and major experience problems. |
| P3 | Optional polish, research, or backlog consideration. |

Choose priority using affected players and platforms, frequency, recoverability, milestone relevance, evidence confidence, dependencies, and effort. A Possible Critical risk can justify P0 investigation; it does not justify an unverified destructive fix. A confirmed Medium issue may be a high-value early task if it is widespread and inexpensive to resolve.

Estimate effort only when scope is understood: `XS`, `S`, `M`, `L`, or `Unknown`, with assumptions. These are relative sizes, not promises of hours. Prefer dependency-aware batches over an unexplained numeric score.

## Coverage and result are different

| Coverage status | Meaning |
| --- | --- |
| Checked | The stated check was completed for the recorded scope. It may have found a failure. |
| Partially checked | Only a subset of cases or evidence was inspected. State what remains. |
| Not checked | The check was not attempted. State why or the planned next step. |
| Blocked | A needed capability, artifact, permission, device, or environment was unavailable. |
| Not applicable | The area does not apply to this game's supported scope. Give the basis. |

Record an executed test's result separately, such as `Pass`, `Fail`, `Inconclusive`, or `Not run`. Do not interpret `Checked` as `Pass`, `Not applicable` as a perfect score, or missing evidence as a failure. Avoid a single health score unless the rubric, weighting, and evidence coverage are explicit; `Unrated` is a valid overall assessment.

## Acceptance criteria and future tasks

Describe an observable outcome in the relevant conditions. For example, require that a specific screen's controls remain visible and reachable at the supported resolutions and input modes, with screenshots and interaction evidence. Do not declare an arbitrary frame-rate, loudness, contrast, or memory target to be the game's requirement; agree on a target or cite the existing one.

Each future task includes baseline, finding IDs, objective, permitted scope, dependencies, acceptance criteria, validation, and rollback. Risk findings begin with confirmation steps. Design opportunities include the intended player benefit and a way to compare the result. Removal tasks require dependency and loading-path review before any later authorized deletion.

## Keep reports proportionate

Lead with the few findings that most affect players or the milestone. Put inventories and evidence details in supporting files. Include supported strengths so successful behavior and intentional design are preserved. State sampling, unavailable capabilities, and unperformed checks plainly; never turn a broad checklist into a claim of complete coverage.
