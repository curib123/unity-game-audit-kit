# Accuracy and verification policy

Use this policy for audits, planning, implementation, and verification. It defines
the evidence needed to support a claim; it does not automate enforcement. This
kit supplies no target Unity project and cannot guarantee 100% accuracy or a
defect-free result. Apply it with [evidence and priorities](evidence-and-priorities.md)
and [implementation principles](implementation-principles.md).

## Scope and preservation

Follow [AGENTS.md](../AGENTS.md), the current user request, and applicable target
instructions. During `AUDIT_ONLY` and `PLAN_ONLY`, keep the original game read-only,
including user changes, generated files, and external data. Assess commands and
Editor operations for writes: opening/importing a project, tests, Play Mode, and
builds can change state. Use only already-authorized validation in an appropriate
isolated copy with disposable saves and test services. Preserve existing evidence.

Current authorization for selected implementation remains valid; do not request
it again. Continue safe independent work when one task needs investigation or an
unavailable capability. Keep reports outside the game. Apply the public-report
redaction boundaries in AGENTS.md to secrets, personal data, and proprietary content.

## Establish evidence provenance

- **Revision:** current commit and branch, staged/unstaged/untracked state, and a
  suitable snapshot of relevant dirty content outside the game. Use `unknown-ref`
  with a reason if no commit is available; a commit alone cannot identify local edits.
- **Environment:** actual Unity and relevant package versions, renderer, target
  platform, and applicable OS/device, build, quality, input, and service conditions.
  Record unknown values instead of assuming defaults or prescribing latest versions.
- **Locators:** inspected paths and symbols, or verified asset GUIDs and scene,
  prefab, component, and object paths. Include the context needed to resolve them.
- **Artifacts:** raw logs, test output, screenshots, recordings, build reports,
  or profiler captures, with paths, date, source, and the revision they describe.
  Preserve originals in an appropriate location; publish only permitted evidence.
- **Method:** distinguish evidence supplied by someone else from checks actually
  executed in this task. Reviewing an existing log is not running its command.
  State provenance gaps, sampling, assumptions, and limits on reproducibility.

Revalidate stale/conflicting evidence against the current baseline before dependent
implementation. Resolve material differences in revision, configuration, or scenario;
record unresolved conflicts and their effect on the claim. Preserve before/after
state checks and their limits, including unexamined external data.
Retain IDs and evidence history for refuted or stale findings; record a separate
corrected/retracted/superseded disposition with rationale and replacement evidence.
Do not silently delete them or report an obsolete claim as a verified fix.

## Separate observation, cause, and proposed change

A demonstrated symptom does not establish its cause or prove a proposed fix.
Keep the observed failure, supported expectation, causal explanation, and proposed
change distinct. State whether each conclusion comes from source reasoning,
supplied output, direct execution, or a hypothesis that still needs investigation.
A coverage gap does not prove a defect, and a preference does not prove a requirement.

Never invent existing file names, symbols, APIs, GUIDs, objects, tests, commands, or
results. Verify locators against the inspected project. Explicitly label proposed
new files, symbols, and tests as proposals; validate their integration before use.
Separate suggested commands from commands actually run, and verify their syntax,
tool availability, and applicability before prescribing them as executable steps.

For version-sensitive APIs and behavior, inspect the installed source/package
metadata and use matching official Unity or package documentation as needed.
Record the version and reference supporting the choice; if source or documentation
is unavailable or ambiguous, retain that uncertainty. Do not invent compatibility
or upgrade the project merely to make a remembered API fit.

## Decide readiness for each task

- **Known cause:** establish how the proposed change addresses the demonstrated
  cause and the required behavior. A complete static proof can justify a small,
  authorized source edit when Unity is unavailable. Record the proof and its scope;
  runtime behavior and Editor integration remain unverified until checked.
- **Essential unknown:** if the cause, API contract, reference, or required behavior
  is unresolved, investigate the affected task before implementing dependent work.
  Missing Unity alone does not block unrelated work supported by adequate evidence.
- **Design work:** identify the selected direction, intended player benefit,
  preserved strengths, and acceptance criteria. Treat aesthetic preferences as
  design opportunities. Validate the actual rendered result and interactions in
  relevant states; a concept or source change cannot establish usability.
- **Removal:** inspect references, dynamic loading, supported build variants,
  saved data/migrations, and restore procedures before an authorized deletion.
  An empty text search alone cannot establish that an asset or system is unused.

Challenge the diagnosis with plausible alternative explanations and relevant
counterexamples. Check lifecycle, configuration, and integration assumptions where
they could change the conclusion. Use independent review when tools and access
permit; share the same baseline, criteria, and raw evidence with the reviewer.
Otherwise label the review `Self-review`. Resolve disagreements through evidence;
reviewer agreement, repeated assertions, and model confidence are not proof.

## Verify the final changed state

Map each original acceptance criterion to a suitable check and evidence. Choose
checks proportional to the change and its concrete regression risks. Preserve
required gates; do not weaken criteria, hide failures, silently narrow the scope,
or change tests to make an unsuccessful result appear successful. Record any
user-approved requirement change explicitly and preserve the original outcome.
Keep criterion IDs such as `AUD-001/AC-01`, requirement sources, conditions, and
pass/fail rules traceable from finding to task to verification report.

Inspect the final diff and relevant authored references/configuration. Run allowed
checks against the actual final revision and dirty state, including required
scenarios and regressions. Later relevant edits invalidate earlier affected checks;
rerun them or mark the affected criteria unverified. Retain unaffected evidence only
when its continued applicability is justified.

Record actual commands or manual methods, tool versions, test filters, discovered
and executed counts, skipped cases, exit/result details, and artifact paths as
applicable. A command exit code alone cannot prove that the intended tests ran.
Zero executed tests, skipped required checks, and missing output are not passes.
Name expected checks that were unavailable or not attempted and explain why.

Use the method the claim requires. Compilation does not establish runtime, build,
visual, audio, device, or performance behavior. A successful build does not prove
playability. Compare actual rendered states and interactions for UI/art claims;
use representative comparable baseline/changed captures for performance claims.
Do not claim executed checks or measurements from source inspection alone.
Mocks and synthetic fixtures support the layer they exercise; they do not prove
real scene, asset, service, or device integration. Check the observable requirement
rather than merely copying the implementation's logic into a test.

## Report results and completion precisely

Record each criterion/check result separately from coverage and finding status:

| Criterion/check result | Meaning |
| --- | --- |
| `Pass` | Appropriate evidence supports this criterion within the declared scope. |
| `Fail` | Evidence demonstrates the criterion is not met. |
| `Inconclusive` | Attempted review or execution cannot establish pass or fail. |
| `Not run` | The check was not performed; give the reason and remaining step. |

| Per-finding status | Meaning |
| --- | --- |
| `Verified` | All required criteria and required relevant regressions have supporting evidence for the final state at the declared scope. |
| `Failed` | A required criterion fails or the original issue persists. |
| `Blocked` | Required validation is unavailable, with no established failure. |
| `Not verified` | Review is incomplete or supports only part of the required scope. |

A known required failure takes precedence over unavailable checks: use `Failed` and retain
the blocked checks in the detail. No hidden skips, scope narrowing, or unexamined
criteria may be counted as `Verified`. Keep audit confidence, coverage, and these
verification results separate; `Checked` does not mean `Pass`.

Report implementation as `Planned`, `Partially implemented`, or `Implemented`,
separately from verification. Required unfinished Inspector/scene wiring means
`Partially implemented`. Use `Implemented, not yet verified` only when all intended
changes and setup are complete but required verification evidence remains missing.

Use the [verification report](../templates/verification-report.md) to connect IDs,
criteria, methods, artifacts, results, and remaining work. State limits and next
checks without inferring whole-game correctness or release readiness from samples.
Follow the [implementation](../prompts/03-implement-approved-findings.md) and
[verification](../prompts/04-verify-fixes.md) prompts for the authorized task mode.
