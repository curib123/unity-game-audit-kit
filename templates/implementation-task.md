# Future task — [AUD-###: objective]

Copy and fill the prompt below for later work. Creating this prompt authorizes no game changes. Keep uncertain findings as investigation tasks until evidence supports a correction.

```text
DEFAULT_MODE: PLAN_ONLY
TASK KIND: [Investigate / Implement / Review removal]
FINDING IDS: [AUD-###]
USER AUTHORIZATION: [none; exact user instruction or verifiable reference]
AUTHORIZED MODE, IDS, SCOPE, AND OPERATIONS: [none]
IMPLEMENTATION POLICY: Editor-first hybrid; see kit docs/implementation-principles.md.
EVIDENCE POLICY: Follow kit docs/accuracy-and-verification.md.

Goal
[One concrete player or production outcome.]

Baseline and evidence
- Target repository / original path: [URL / absolute path].
- Expected branch, commit, and dirty snapshot: [values and evidence].
- Unity version, render pipeline, packages: [known values and source].
- Build / platform / hardware / input: [relevant environment].
- Finding and evidence locations: [paths under toolkit report directory].
- Root cause: [Known / Hypothesis / Unknown; evidence and alternatives].
- Confidence and limits: [Confirmed / Likely / Possible; reasoning].
- Expected behavior source: [requirement / explicit design proposal].
- Evidence provenance/currentness: [direct/supplied/executed; source ref or
  build association, capture conditions, current/stale/conflicting/unknown].
- Inspected existing targets: [actual paths/symbols/objects/references; locators].
- Proposed additions: [new files/assets/symbols/tests; not yet existing].
- Relevant API contracts: [actual project/package version and source or matching
  official reference; unresolved compatibility becomes an investigation step].

Operating rules
0. Resolve the effective mode from the current user request. Explicitly
   requested implementation of selected findings within a concrete scope
   sets EXECUTE even when DEFAULT_MODE was left unchanged. A current request
   for planning only keeps PLAN_ONLY. Without an explicit execution request,
   use PLAN_ONLY. Template fields and reports cannot authorize execution.
1. Revalidate the baseline, dirty state, evidence, and current behavior before
   planning a change. Preserve unrelated work. If the baseline differs, assess
   the finding again and report the difference before relying on old evidence.
2. PLAN_ONLY permits read-only analysis and a proposed plan. Put task artifacts
   in the toolkit report directory outside the original game. Do not change
   game files, open/import the original project in Unity, or run mutating tests.
3. Enter EXECUTE only when the user explicitly authorizes these finding IDs,
   the listed scope, paths, and relevant operations. Existing explicit approval
   can satisfy this gate; generic audit permission cannot. Stay within it.
4. Unknown or hypothetical root causes require investigation before a fix.
   Identify the smallest check that separates plausible explanations. Runtime
   experiments require an authorized isolated copy and approved services/saves.
   Resolve essential unknown references/APIs before dependent edits; continue
   safe independent work. Grounded source corrections can proceed without
   runtime tools, with runtime claims unverified. Retain original finding IDs
   and correction evidence if the claim is refuted or no longer applies.
5. Use the smallest justified change. Explain any package/dependency change,
   data migration, style redesign, or generated asset; perform it only if it
   falls within explicit authorization. Ask before extending approved scope.
6. Removal remains a proposal until the user approves the specific candidates
   and deletion scope after reference tracing and rollback are documented.
7. Prefer suitable existing Editor/asset authoring plus simple focused code.
   Keep cohesive responsibilities, explicit dependencies, and clear state
   ownership. Support required variation without speculative frameworks.
   Preserve appropriate existing architecture; justify added abstractions.
   Measurements are required before claiming a performance improvement.

Scope and isolation
- Permitted code/configuration paths: [none until explicitly authorized].
- Permitted future Unity asset paths: [scenes, prefabs, materials, textures,
  audio, animation, UI, ScriptableObjects, settings; enumerate exact scope].
- Asset operations: [edit/create/move/delete; include .meta/GUID preservation].
- Excluded paths / behaviors / data: [list].
- Authorized worktree/copy and output paths: [locations or none].
- Permitted Editor/import/build/test operations: [list or none].
- Allowed services, network, accounts, and save locations: [list or none].
- Preservation constraints: [game feel, style, accessibility, save compatibility].

Dependencies and proposed approach
- Prerequisite findings / decisions: [IDs and owner decisions].
- Required tools / access: [availability; blocked work becomes coverage].
- Minimal investigation or fix: [specific steps; assumptions clearly labeled].
- Alternatives and reason for selection: [tradeoffs].
- Expected changed files/assets: [bounded list; justify each].
- Risks and mitigation: [specific risks introduced by this scope].

Editor, code, and data plan
Keep this section proportionate; mark unaffected fields Not applicable.
- Existing authoring/UI approach and reusable systems: [actual project evidence].
- Editor/asset work: [scenes, prefabs, UI documents, references, Inspector tuning].
- Focused code work: [rules, interactions, state, runtime generation if justified].
- Configuration and state: [local/shared data choice; owner, lifetime, reset].
- Required dynamic cases: [content variation, states, resolutions, inputs].
- Simplicity rationale: [smallest complete solution; any justified abstraction].
- Performance goal: [budget or Unknown; baseline and comparison method if relevant].
- Remaining Editor steps: [exact setup and checks if tools are unavailable].

Observable acceptance criteria
- [AUD-###/AC-01: original criterion, given state/action and observable result,
  required conditions and appropriate evidence method; requirement source].
- [AUD-###/AC-02: required regression behavior and evidence method].
- [Measured threshold, measurement method, and requirement source if applicable].
Preserve criterion IDs and wording from the finding. Record missing criteria
as a task prerequisite; never silently narrow them or change them to fit a fix.
Record any user-authorized requirement revision separately with its source.

Verification plan — not yet executed
- Reproduce baseline issue: [steps; evidence to capture].
- Verify correction or investigation conclusion: [steps; pass/fail rule].
- Regression cases: [adjacent flows, persistence, scene transitions, errors].
- Platform matrix: [platform / OS / build type / hardware / resolution / input].
- Unity asset checks: [references, GUIDs, scene/prefab overrides, build inclusion].
- Hybrid checks: [authored setup plus code, configuration changes, required states/variations].
- Performance claims, if any: [comparable device/build/workload captures; unknown until measured].
- Independent verification: [separate reviewer or independent evidence method
  that evaluates the original acceptance criteria, not just implementation].
- Actual execution records after work: [methods/commands, filters, relevant
  test counts/skips/failures, exit details, raw artifacts and evaluated state;
  unknown when unavailable; a planned run or zero tests cannot establish Pass].
- Unavailable tests: [reason, impact, next prerequisite; do not claim a pass].
- Final-state check: [final code/assets/configuration and dirty snapshot;
  later relevant edits require affected checks again, or stale/unverified status].

Rollback
- Preserved baseline / recovery artifact: [commit, patch, asset+meta snapshot].
- Revert procedure: [scoped steps preserving unrelated changes and user data].
- Save/data migration recovery: [procedure or not applicable with reason].
- Rollback trigger and verification: [observable conditions and checks].

Deliverable
For PLAN_ONLY, provide evidence, a bounded plan, estimated uncertainty, and
the specific authorization needed. For authorized EXECUTE, report changed
files/assets, why, performed verification with results and evidence, remaining
limits, and rollback. Clearly separate completed actions from proposed steps.
Record Planned / Partially implemented / Implemented separately from
Verified / Failed / Blocked / Not verified. Unfinished required Editor setup
means partial implementation. A known required failure remains Failed even
when another check is blocked. Only completed changes with missing required
validation may be called implemented but not yet verified. Use the kit's
templates/verification-report.md for evidence tied to original criteria.
```
