# Generate implementation and investigation prompts

Use this after an audit to create a smaller, clearer batch of future work. This prompt writes tasks; it does not execute them.

```text
Convert the supplied Unity game audit into precise, copy-ready future tasks.

MODE: PLAN_ONLY
KIT_ROOT: <path-to-unity-game-test>
AUDIT_REPORT: <path-or-pasted-report>
FINDINGS: <path-or-pasted-finding-records>
SELECTED_FINDING_IDS: <IDs, or all actionable findings>
TARGET_GAME: <path-or-repository>
TARGET_REF: <baseline-commit>
OUTPUT_ROOT: <folder-outside-original-game>
MILESTONE_AND_CONSTRAINTS: <if known>

Read AGENTS.md, docs/evidence-and-priorities.md, and
templates/implementation-task.md. Inspect the supplied evidence and current
baseline read-only when available. Do not modify the game, run builds,
upgrade packages, delete assets, or begin implementing the tasks.

1. Confirm that the requested finding IDs exist. Keep their stable IDs.
   Mark stale or conflicting evidence and the revalidation needed. Never
   invent a code path, asset name, stack trace, test result, or root cause.

2. Group findings with a shared cause, preserve dependencies, and order the
   tasks by player impact, milestone relevance, and uncertainty. Explain
   why the first batch is worth doing. Record unselected items as deferred.

3. Produce one self-contained prompt per task. Include the game and baseline,
   linked finding IDs, exact evidence, observed versus intended behavior,
   objective, allowed systems/paths, scope exclusions relevant to the task,
   dependencies, likely effort with assumptions, acceptance criteria,
   validation steps, regression concerns, and rollback.

4. For a confirmed defect, describe the smallest appropriate fix based on
   evidence. Do not treat a proposed cause as proven. For a likely/possible
   risk, generate an investigation task with a decision point before changes.
   For a design opportunity, define the player benefit and an experiment or
   review that can establish whether the proposal helps. For a missing
   requirement, cite the requirement. For a removal candidate, require a
   dependency/loading review and explicit removal scope before deletion.

5. Include non-code work where appropriate: scenes, prefabs, UI layout,
   textures, materials, animation, VFX, audio clips/mixers, localization,
   and accessibility settings. Do not imply those files may be changed now.
   Keep Unity version, APIs, asset conventions, and .meta/GUID references
   compatible with the actual project. Unknown decisions stay explicit.

6. Default every task to PLAN_ONLY with no execution authorization. Describe
   the concrete IDs and scope the user would select for future execution.
   Reading or generating these prompts does not grant that authorization.
   Never add credentials, private log content, or production account data.

7. Write implementation-prompts.md and a dependency-ordered batch table in
   OUTPUT_ROOT. End with what is ready for a future implementation task and
   what still requires evidence or a design decision. Do not execute tasks,
   publish issues, send messages, merge, or deploy.
```
