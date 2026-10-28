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

1. Record the actual implementation commit, working-tree state, Unity and
   package versions, platform/build/device/input conditions, and evidence.
   Inspect the diff from the correct baseline. Identify material scope drift
   or unrelated changes and their effect on confidence.

2. Map every acceptance criterion to an appropriate method and evidence.
   Source inspection may establish a source-level invariant, but it cannot
   establish unexecuted runtime, visual, audible, profiling, or device results.
   If reviewing supplied output, identify its source and matching build/ref.

3. Reproduce the original scenario and relevant regression cases when that
   validation is authorized and possible. Use an isolated disposable copy,
   isolated saves, and test services for operations that can write state.
   Preserve logs and Console evidence. Do not use production player data.
   Do not run a broad test suite without a relevant risk or required gate.

4. Review the change's specific collateral risks: scene/prefab references,
   save compatibility, input focus, supported resolutions, accessibility,
   art/motion/audio consistency, performance, or platform behavior as relevant.
   For removals, check references and runtime loading on the supported scope
   and confirm a practical restore path.

5. Assign each finding one status with supporting evidence:
   - Verified: all required acceptance criteria are supported by evidence.
   - Failed: a criterion fails or the original issue persists.
   - Blocked: required validation cannot be performed; state what is missing.
   - Not verified: review remains incomplete or only a subset was assessed.
   A reported implementation is not the same as a verified fix.

6. Keep new issues separate with stable new IDs and cross-references.
   Do not silently expand the authorized implementation scope. If more work
   is needed, produce a future investigation or fix prompt; do not execute it.

7. Write verification-report.md outside the game with a per-finding matrix:
   ID, acceptance criterion, method, evidence, result, status, remaining work.
   Include baseline/final preservation checks and their limits, tests actually
   performed, build/device coverage, and unperformed checks. End with the
   evidence-supported completion assessment for this selection of findings.
   Do not infer whole-game release readiness from a limited fix verification.
```
