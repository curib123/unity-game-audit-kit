# Audit workflow

## 1. Establish the two locations

Identify the kit directory and the original target game separately. Resolve the requested branch to a commit where possible. Record the exact source of evidence and whether local changes differ from that commit. If no game has been supplied, prepare a project brief and list the minimum evidence needed; do not issue a game verdict.

The default output directory is `reports/<game-slug>/<YYYY-MM-DD>-<short-sha>/` in the kit. Resolve paths before writing. If that would be inside the target checkout, use another agreed location. Append a run suffix when a folder already exists, or update it only when the user requested an update. Use `unknown-ref` where there is no commit and explain the baseline.

## 2. Understand the intended game

Read the [project brief](../templates/project-brief.md), game documentation, applicable repository instructions, Unity version, packages, render pipeline, supported platforms and controls, scenes or build profiles, first-party directories, and existing issue or test summaries when available. Read only what is relevant; disclose sampling on large projects.

Distinguish confirmed project intent from reasonable assumptions. Inspect existing evidence before asking a question. If a missing answer would change a major recommendation, record the uncertainty and the smallest question needed. Do not block useful static analysis because a nonessential preference is unknown.

## 3. Establish preservation and capability baselines

Record Git HEAD and existing staged, unstaged, and untracked state when Git is available. Preserve existing work. Also record what is known about ignored files, external save data, and services; Git status alone cannot cover them. A read-only mount gives a stronger boundary for original files than instructions alone.

List available capabilities: source, images, video, audio playback, read-only Editor inspection, isolated runtime, test execution, builds, target devices, and profiler data. A tool being installed does not prove that it is connected to this project or authorized for this task.

Static and supplied-evidence review is the default. Opening Unity or running builds/tests/Play Mode can write project state, generated files, and persistent data. Use an isolated disposable copy and disposable test saves/services only when the action is within the user's existing authorization. Otherwise document a protocol and mark the runtime check unperformed. Never clear the Console or replace the original evidence.

## 4. Review through the studio roles

Use [studio roles](studio-roles.md) to assign independent areas. Give all reviewers the same project baseline, intended experience, access limits, evidence conventions, and read-only boundary.

Cover [technical QA](../checklists/technical-qa.md), [playtest scenarios](../checklists/playtest-scenarios.md), and [design, UI/UX, art, and audio](../checklists/design-ux-art-audio.md) according to applicability. A small 2D single-player game does not need a fictional multiplayer audit. An early prototype should be evaluated against its stage and purpose.

Run specialists concurrently if available, or review their perspectives sequentially. Do not describe simulated perspectives as independent human playtests. Each specialist returns findings, evidence, supported strengths, and coverage gaps. The coordinator validates the evidence and merges duplicate root causes.

## 5. Build the evidence-backed backlog

Use stable `AUD-001` IDs and the [finding template](../templates/finding.md). Apply the [evidence and priority rules](evidence-and-priorities.md). Record specific expected versus observed behavior. If the expected behavior is a proposal, say so.

Separate confirmed defects, risks, design opportunities, missing requirements, and removal candidates. Prefer a small set of well-supported findings to a long generic wishlist. Keep uncertainty attached to each finding instead of hiding it in a global disclaimer.

For evidenced art/UI problems, use the [focused redesign review](../prompts/05-art-ui-redesign-review.md) within the requested scope. Recommend Keep, Enhance, Restructure, Redesign, or Investigate for each affected screen or art system. Use the [redesign brief](../templates/art-ui-redesign.md) to record fit with the game's goals, preserved strengths, proposed changes, meaningful alternatives, and acceptance criteria. Missing visuals remain a coverage gap. Requested concepts require suitable tools, stay outside the original game, and do not count as implementation or runtime validation.

For possible removals, complete the [removal review](../templates/removal-review.md). Reference searches alone do not establish that an asset is unused. Consider GUID references, scenes, prefabs, Resources, Addressables, bundles, string keys, reflection, configuration, server content, editor tools, tests, and supported build variants as applicable. Recommend keep, rework, defer, or further investigation when evidence is incomplete.

## 6. Prepare prompts for future work

The full audit produces copy-ready prompts using the [implementation task template](../templates/implementation-task.md). Use [prompt 2](../prompts/02-generate-fix-prompts.md) to refine a selected batch later.

Group symptoms with a shared cause. Put dependencies before dependent fixes. Include precise acceptance criteria, affected systems, needed evidence, test scope, rollback, and an effort estimate with assumptions. Unknown causes produce investigation tasks. Design decisions that the user must make remain explicit; they are not silently chosen by the implementation prompt.

When a redesign brief exists, carry its screen/system scope, direction, preserved elements, responsive/input behavior, and validation criteria into the future tasks. Distinguish a recommendation from a selected direction. Honor a current user instruction adopting the recommendation; otherwise keep tasks conditional on the design decision and do not combine alternative directions into one implementation.

Generating the prompt does not execute it. The separate [implementation prompt](../prompts/03-implement-approved-findings.md) defaults to planning. Execution requires explicit user authorization for the selected findings and scope; authorization already provided in the current task remains valid.

## 7. Close the audit

Recheck the original project's preserved state and compare it with the baseline. Report the paths and evidence checked, including limits. Do not reset or clean unexpected changes. Stop and disclose any accidental modification before further potentially mutating work.

Save the [audit report](../templates/audit-report.md) and supporting files outside the game. Summarize the most important findings, supported strengths, recommended order, and blocked checks. Do not say the game is tested or release-ready based only on source review.

Reports may contain proprietary or personal information. Keep evidence local or in an authorized destination, redact secrets, and publish to a public repository or GitHub Issues only when specifically requested. Merely auditing a repository does not authorize communication or publication.

## 8. Verify separately after authorized fixes

Use [prompt 4](../prompts/04-verify-fixes.md) against the actual implementation commit. Compare each approved task's acceptance criteria with fresh evidence. State `Verified`, `Failed`, `Blocked`, or `Not verified` for each finding and explain why. Preserve original IDs and record new issues separately.

Verification can conclude that a fix is incomplete. It does not authorize additional game changes. Stop when the requested validation is sufficient; broaden testing only for a concrete remaining risk or required release gate.
