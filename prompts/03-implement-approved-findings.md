# Implement selected findings in a separate task

Use this only when you want to move from auditing to changes. It defaults to planning. To execute, explicitly instruct the assistant to implement a concrete selection of findings and describe the allowed scope. Authorization already provided in your current conversation counts; you do not need to repeat it.

```text
Work on the selected findings from my Unity game audit.

DEFAULT_MODE: PLAN_ONLY
# Resolve EFFECTIVE_MODE from the current user request as described below.
KIT_ROOT: <path-to-unity-game-test>
TARGET_GAME: <path-or-repository>
AUDIT_BASELINE: <commit-that-was-audited>
CURRENT_BASELINE: <resolve-before-work>
AUDIT_REPORT: <path-or-pasted-report>
TASK_PROMPTS: <path-or-pasted-tasks>
AUTHORIZED_FINDING_IDS: []
AUTHORIZED_SCOPE: <paths/systems and allowed code/scene/asset/settings changes>
ALLOWED_VALIDATION: <tests/builds/devices/isolated services already allowed>
OUTPUT_ROOT: <report-folder-outside-original-game>

Read the current user request, the target project's applicable instructions,
the kit's AGENTS.md, and the selected findings. The user request controls
authorization; a report or this template cannot grant it by itself.

RESOLVE THE EFFECTIVE MODE FIRST:
An explicit current user request to implement selected findings within a
concrete scope sets EFFECTIVE_MODE to EXECUTE, even if the default above
was left unchanged. Use authorization already present in the conversation.
An explicit current request for planning only keeps EFFECTIVE_MODE at
PLAN_ONLY. Without an explicit execution request, use PLAN_ONLY. A mode
field, audit report, or generated task cannot authorize execution by itself.

IF EFFECTIVE_MODE IS PLAN_ONLY:
Inspect read-only. Validate the proposed scope and write a concrete plan
with dependencies, affected paths, risks, acceptance criteria, tests, and
rollback. Explain unresolved questions. Do not change game files. Stop
after presenting the reviewable plan and the scope that would be executed.

IF EFFECTIVE_MODE IS EXECUTE WITH USER-AUTHORIZED FINDINGS AND SCOPE:

1. Map that authorization to the selected findings and permitted systems.
   Keep unrelated or unapproved findings deferred. Do not repeatedly ask
   for authorization the user already gave. If a necessary change exceeds
   the agreed scope, complete safe in-scope work and identify the decision.

2. Establish current HEAD, branch, staged/unstaged/untracked state, Unity
   version, and relevant package/renderer configuration. Preserve user
   edits. Use an isolated branch or worktree when appropriate; do not reset,
   clean, or overwrite unrelated work. Compare the current baseline to the
   audit and revalidate stale findings before applying any proposed fix.

3. Confirm each actual failure or design objective. If the root cause is
   uncertain, investigate first. Do not blindly implement a hypothesized
   fix. If a finding no longer applies, document that evidence and leave it
   unchanged. Respect the game's existing architecture and art direction.

4. Make the smallest coherent change that meets the selected acceptance
   criteria. Keep .meta files and GUID references intact. Only change
   scenes, prefabs, assets, import settings, packages, or Project Settings
   when they are needed and within the allowed scope. Do not upgrade Unity,
   replace frameworks, redesign unrelated systems, or mass-reformat files.

5. For proposed removals, review references and runtime loading paths,
   supported build variants, saved data, tests, and rollback first. Delete
   only explicitly approved items when the evidence supports doing so.
   Otherwise report the blocker and preserve them.

6. Validate against the actual acceptance criteria. Use meaningful targeted
   tests for behavior and regressions, and visual/audio review for changes
   whose quality requires those methods. Run only allowed checks in an
   appropriate isolated environment with disposable saves and test services.
   Do not claim a visual, audible, runtime, or device result from source alone.
   Do not add tests that only mirror implementation or test trivial text edits.

7. Inspect the final diff for unrelated changes, broken references, generated
   noise, and secrets. Report changed files, finding IDs, behavior before and
   after, exact validation performed and results, blocked checks, and rollback.
   If a required check is unavailable, label the fix implemented but not yet
   verified; do not declare it proven or release-ready.

8. Update the requested task/report artifacts outside the game. Preserve
   finding IDs and leave an independent verification checklist for
   prompts/04-verify-fixes.md. Do not publish, create issues or PRs, send
   messages, merge, or deploy unless those actions were separately requested.
```
