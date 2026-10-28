# AUD-001 — [specific observable issue or opportunity]

Template only. Assign a unique ID when evidence supports a finding. An unavailable test, inaccessible asset, or unknown requirement alone belongs in coverage.

## Classification

| Field | Value |
| --- | --- |
| Type | [Defect / Risk / Design opportunity / Missing requirement / Removal candidate] |
| Confidence | [Confirmed / Likely / Possible] |
| Confidence rationale | [what evidence establishes; what remains uncertain] |
| Severity | [Critical / High / Medium / Low / Informational] |
| Severity rationale | [player impact, affected population, likelihood/exposure; distinguish observed from estimated] |
| Priority | [P0 / P1 / P2 / P3] |
| Priority rationale | [urgency, dependencies, effort uncertainty; assessed independently of severity] |
| Discipline / affected flow | [gameplay, UX, art, audio, layout, performance, etc.] |
| State / owner | [Proposed / Needs investigation / Accepted / Deferred / Verified resolved] / [unassigned] |
| Baseline / environment | [commit plus dirty snapshot; build, platform, hardware, input] |
| Related findings / dependencies | [IDs / none known] |

## Observation and expectation

**Observed:** [Describe only what the cited evidence shows; state frequency and scope.]

**Expected:** [Required behavior or proposed improvement. Cite a requirement, established contract, or clearly label expert judgment.]

**Requirement status:** [Confirmed source / inferred intent / unknown]. A `Missing requirement` needs an established requirement and evidence of its absence; a preference can be a `Design opportunity`.

**Player or production impact:** [Specific consequence; separate measured effect from predicted impact.]

## Evidence

| Evidence ID / relative path | Timestamp (UTC) | Source and exact location | Supports / limits |
| --- | --- | --- | --- |
| [E-001 / evidence/file] | [time] | [file:line, scene/object hierarchy, GUID, screenshot/build context] | [claim; uncertainty] |

- Evidence method: [source inspection / recorded runtime observation / human report / other].
- Runtime status: [actually reproduced / reported but not reproduced / not run / not applicable].
- Provenance: [original read-only source or authorized isolated copy; exact baseline association].

## Reproduction or inspection procedure

1. Preconditions: [scene, fixture/save, account type, settings, device, input; no secrets].
2. Action or inspection: [exact steps and file locations].
3. Actual outcome: [observed result, timestamp, evidence reference].
4. Expected outcome: [observable behavior and source].
5. Frequency and counterexamples: [attempts/successes if measured; unaffected configuration if checked].

If not executed, label the steps **Proposed protocol — not run**, leave actual results unknown, and state what evidence supports the finding instead.

## Cause and uncertainty

- Root cause status: [Known / Hypothesis / Unknown].
- Cause evidence or hypothesis: [mechanism and supporting source; do not present a hypothesis as proven].
- Alternative explanations: [plausible causes, design intent, configuration, recording limitations].
- Smallest next investigation: [read-only check or authorized isolated experiment that can distinguish them].
- Coverage limits: [uninspected variants and missing evidence].

## Recommendation and acceptance criteria

- Recommended next action: [investigate / plan minimal correction / explore design / review removal].
- Proposed scope: [specific systems and paths; no change authorization implied].
- Alternatives and tradeoffs: [keep behavior, smaller change, deferred redesign; why].
- Preservation constraints: [working behavior, style, saves, accessibility, platform compatibility].
- Acceptance criteria: [observable pass/fail outcomes; thresholds need a requirement or justification].
- Verification protocol: [steps, platforms, input modes, regression cases; label not yet run].
- Effort / dependencies: [estimate with uncertainty or unknown; prerequisite IDs].
- Future prompt: [implementation-prompts.md anchor; defaults PLAN_ONLY].

## Resolution record — fill only after authorized work

- Authorization and changed baseline: [exact finding/scope approval, commit or patch reference].
- Verification actually performed: [independent evidence, environment, result, date].
- Remaining risk / follow-up: [limits; reopen condition].
