# Verify completed changes

Use this after implementation to review whether the selected findings are resolved. Verification does not authorize more fixes.

```text
Independently verify the selected Unity game audit findings against the
implementation and its acceptance criteria.

MODE: VERIFY_ONLY
KIT_ROOT: <path-to-unity-game-audit-kit>
TARGET_GAME: <path-or-repository>
AUDIT_BASELINE: <audited-commit>
IMPLEMENTATION_REF: <commit-or-current-state-to-verify>
FINDING_IDS: <selected-IDs>
AUDIT_AND_TASKS: <report-and-task-paths>
ALLOWED_VALIDATION: <existing-evidence-only or specifically allowed checks>
OUTPUT_ROOT: <folder-outside-original-game>

Read AGENTS.md, docs/evidence-and-priorities.md, the selected finding records,
the implementation task acceptance criteria, and applicable target-project
instructions. Preserve the original game and existing user edits. Do not
apply additional fixes or rewrite the acceptance criteria to fit the result.
Use docs/implementation-principles.md to assess relevant hybrid setup and
performance claims; it does not authorize additional changes or checks.
Apply docs/accuracy-and-verification.md and templates/verification-report.md.
Identify whether this is a separate reviewer or a critical self-review;
do not imply independence or executed checks that did not occur.

1. Record the actual implementation commit, working-tree state, Unity and
   package versions, platform/build/device/input conditions, and evidence.
   Inspect the diff from the correct baseline. Identify material scope drift
   or unrelated changes and their effect on confidence.
   Include a patch/snapshot identity for changes not captured by the commit.
   Record implementation completeness separately: Planned, Partially
   implemented, or Implemented. Do not report pending Editor setup as done.

2. Map every acceptance criterion to an appropriate method and evidence.
   Source inspection may establish a source-level invariant, but it cannot
   establish unexecuted runtime, visual, audible, profiling, or device results.
   If reviewing supplied output, identify its source and matching build/ref.
   Preserve each original criterion ID, pass/fail rule, and required
   conditions. Record any authorized requirement change separately; never
   silently narrow the scope or mark a required criterion not applicable.
   Resolve stale or contradictory evidence; an unknown build/ref association
   cannot prove the current fix. Use Pass / Fail / Inconclusive / Not run for
   criterion results, separate from finding status or coverage.

3. Reproduce the original scenario and relevant regression cases when that
   validation is authorized and possible. Use an isolated disposable copy,
   isolated saves, and test services for operations that can write state.
   Preserve logs and Console evidence. Do not use production player data.
   Do not run a broad test suite without a relevant risk or required gate.
   Record actual commands/methods, test filters, discovered/executed counts,
   passed/failed/skipped counts, exit codes where available, and raw result
   artifacts. Zero relevant tests, skipped required tests, aborted runs, and
   missing result files do not prove a pass. Compare against baseline failures;
   if origin is unknown, state that instead of inventing regression history.
   Do not suppress errors, disable tests, upgrade packages, or change game
   configuration merely to make verification pass.

4. Review the change's specific collateral risks: scene/prefab references,
   save compatibility, input focus, supported resolutions, accessibility,
   art/motion/audio consistency, performance, or platform behavior as relevant.
   For removals, check references and runtime loading on the supported scope
   and confirm a practical restore path.

   For art/UI redesigns, compare the actual revised screens/assets against
   the selected brief, preserved strengths, and original acceptance criteria.
   Check relevant states, supported displays, controls, and accessibility.
   A concept image alone cannot verify implementation or improved usability;
   identify missing rendered, interaction, or player evidence explicitly.

   For hybrid implementations, check authored asset/reference setup and code
   together, including relevant overrides, tuning, state reset, and required
   variations. Identify unfinished Editor steps. For performance claims,
   compare representative baseline and changed captures under comparable
   conditions; otherwise mark the claimed improvement unverified. Do not
   expand verification merely to enforce an architectural preference.

5. Assign each finding one status with supporting evidence:
   - Verified: all required acceptance criteria and required relevant
     regression checks are supported for the declared final state and scope.
   - Failed: a required criterion fails or the original issue persists;
     this takes precedence even if other required checks are blocked.
   - Blocked: required validation cannot be performed; state what is missing.
   - Not verified: review remains incomplete or only a subset was assessed.
   A reported implementation is not the same as a verified fix.
   Source inspection, compilation, runtime interaction, rendered UI, audible
   output, builds, and device measurements support different claims. Do not
   substitute an easier check for the evidence a criterion actually requires.

6. Keep new issues separate with stable new IDs and cross-references.
   Do not silently expand the authorized implementation scope. If more work
   is needed, produce a future investigation or fix prompt; do not execute it.

7. Write verification-report.md outside the game with a per-finding matrix:
   ID, acceptance criterion, method, evidence, result, status, remaining work.
   Include baseline/final preservation checks and their limits, tests actually
   performed, build/device coverage, and unperformed checks. End with the
   evidence-supported completion assessment for this selection of findings.
   Do not infer whole-game release readiness from a limited fix verification.
   Confirm results apply to the final code, assets, configuration, and dirty
   state. Later relevant edits invalidate affected checks until rerun. Preserve
   earlier results as history and mark stale conclusions. Resolve links from
   the completed report's location and replace template placeholders with
   actual evidence or an explicit unknown; do not invent missing details.
```
