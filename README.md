# Unity Game Audit Kit

A complete studio review workflow for an **existing Unity game**: QA, player experience, game design, UI/UX, layout, art, animation, VFX, sound, accessibility, performance, and release readiness.

**Audit the game. Explain the evidence. Produce prompts for the changes.** The audit leaves the original game's code, scenes, prefabs, assets, packages, and settings unchanged.

This repository contains instructions, checklists, and templates. It does not contain a playable game or an automatic scanner, and installing it does not run a test. A reviewer or AI assistant needs access to your actual game and any relevant evidence.

## Start here

1. Keep this repository **beside** your Unity project, outside its `Assets` folder. You can clone it with:

   ```bash
   git clone https://github.com/curib123/unity-game-audit-kit.git
   ```

2. Open your game and this kit in the same assistant workspace, or provide access to both repositories. Start with source access. Add a build, screenshots, recordings, logs, or profiler captures when available.
3. Copy the launcher below. Replace the game path and output path. The report folder must be outside the game project.
4. Review the findings and generated change prompts. Implementation is a separate task for the findings you explicitly choose.

### Copy this launcher

```text
Use the Unity Game Audit Kit at <path-to-unity-game-audit-kit>.
Read AGENTS.md and run prompts/01-full-studio-audit.md.

MODE: AUDIT_ONLY
TARGET_GAME: <absolute-path-to-my-Unity-project-or-repository-URL>
TARGET_REF: <commit-or-branch; resolve and record the commit>
TARGET_PLATFORMS: <known platforms, or determine from project evidence>
GAME_INTENT: <genre, intended players, and release stage, if known>
AVAILABLE_EVIDENCE: <source, screenshots, build, video, audio, logs, etc.>
RUNTIME_SCOPE: source and supplied evidence only unless I already authorize more
OUTPUT_ROOT: <absolute-path-to-unity-game-audit-kit>/reports/<game-name>/<date>-<commit>/

Act as a coordinated game studio: QA lead, tester, player-experience
reviewer, game and level designer, UI/UX designer, art director,
animation/VFX reviewer, sound designer, accessibility reviewer,
Unity engineer, and release producer.

Find evidenced bugs, errors, usability problems, style/layout issues,
missing requirements, and candidates to simplify or remove. Preserve
the game's intended identity. Separate defects from design suggestions.

Do not modify the original game. Do not implement fixes or delete assets.
Record evidence, severity, confidence, priority, and acceptance criteria.
Do not claim to have played, heard, profiled, built, or tested anything
unless that check actually happened. Mark unavailable checks clearly.

Finish with a prioritized report and copy-ready prompts describing
what to fix or implement later. Unverified risks need investigation
prompts. Future implementation requires my selected findings and scope.
```

## Main workflow

| Step | Prompt | Result |
| --- | --- | --- |
| 1. Audit | [Full studio audit](prompts/01-full-studio-audit.md) | Evidence, coverage, findings, priorities, and change prompts; original game unchanged. |
| 2. Prepare tasks | [Generate fix prompts](prompts/02-generate-fix-prompts.md) | Turns selected findings into scoped implementation or investigation prompts. |
| 3. Implement later | [Implement approved findings](prompts/03-implement-approved-findings.md) | Defaults to a plan. Changes only explicitly authorized findings when execution is requested. |
| 4. Verify | [Verify fixes](prompts/04-verify-fixes.md) | Checks acceptance criteria and regressions without silently fixing more things. |

The full audit already produces change prompts. Step 2 is useful when you want to refine the backlog or select a smaller batch.

## Art and UI improvement or redesign

Use the [focused art and UI review](prompts/05-art-ui-redesign-review.md) to assess whether the current visuals and interface suit the game's genre, audience, platforms, controls, and intended experience. It can expand findings from the full audit or run as a focused review.

The review recommends a strategy for each relevant screen or art system:

| Strategy | When it fits |
| --- | --- |
| Keep | The existing design works for the stated goals; preserve its strengths. |
| Enhance | Targeted changes to typography, contrast, spacing, states, or asset treatment can address the problem. |
| Restructure | Hierarchy, navigation, grouping, or composition needs changing within the existing identity. |
| Redesign | A broader direction is justified by evidence of a mismatch or an explicit new design goal. |
| Investigate | More visual, interaction, or requirement evidence is needed before recommending a change. |

The output explains observed problems, proposed layouts and art direction, expected player benefits, what to preserve, meaningful alternatives, tradeoffs, and acceptance criteria. It uses the [redesign brief template](templates/art-ui-redesign.md) and generates future implementation prompts. A recommendation remains separate from the direction you select.

Provide representative screenshots of the main menu, gameplay HUD, pause/settings, and any problem screens, plus gameplay or interaction recordings when relevant. Include the genre, target devices, and style references you want considered. Without visual evidence, the review records that limitation instead of judging the current artwork.

Optional mockups require a request and suitable image/design tools; the kit does not include those tools. Concepts remain separate report artifacts outside the game and are not proof of a working implementation. The audit keeps the original game unchanged.

### Copy this focused review request

```text
Use unity-game-audit-kit and follow prompts/05-art-ui-redesign-review.md.
MODE: AUDIT_ONLY
TARGET_GAME: <project-path-or-repository-URL>
OUTPUT_ROOT: <report-folder-outside-the-original-game>

Review whether my current game art and UI suit the genre, audience,
platforms, controls, and intended experience. Identify evidenced problems
with layout, readability, interaction, consistency, and visual style.

For each affected screen or art system, recommend Keep, Enhance,
Restructure, Redesign, or Investigate. Explain the problem, proposed
change, player benefit, preserved strengths, tradeoffs, and acceptance
criteria. Produce art-ui-redesign.md and future implementation prompts.
Keep the original game unchanged.
```

## What the studio checks

| Discipline | Questions it answers |
| --- | --- |
| QA and testing | What breaks? Can it be reproduced? Which platforms and states are affected? |
| Player experience | Does the player understand the goal, controls, feedback, and next action? |
| Game and level design | Does the core loop support the intended experience? Where are pacing, balance, teaching, or navigation weak? |
| UI/UX and layout | Are screens readable, responsive, consistent, and usable with the supported input methods? |
| Art direction | Are silhouettes, colors, materials, environments, and visual hierarchy coherent with the intended style? |
| Animation and VFX | Do motion, timing, hit feedback, transitions, and effects communicate the right state? |
| Sound and music | Do cues, mixing, loops, transitions, spatial sound, and volume controls serve the experience? |
| Accessibility | Can players perceive, understand, and control the game across relevant needs and devices? |
| Unity engineering | What do code, serialization, assets, dependencies, save systems, and existing tests demonstrate? |
| Performance and release | What do measured captures, build evidence, target devices, and recovery paths support? |
| Production and scope | What should be kept, fixed, improved, added, investigated, deferred, or considered for removal? |

See [studio roles](docs/studio-roles.md), [technical QA](checklists/technical-qa.md), [playtest scenarios](checklists/playtest-scenarios.md), and [design, UX, art, and audio](checklists/design-ux-art-audio.md).

## What you receive

Each audit can produce the following files under a separate report folder:

| File | Contents |
| --- | --- |
| `audit-report.md` | Executive summary, supported strengths, highest-impact findings, and recommended order. |
| `findings.md` | Stable finding IDs with evidence, impact, reproduction, confidence, and acceptance criteria. |
| `coverage.md` | What was checked, partly checked, blocked, skipped, or not applicable, and why. |
| `implementation-prompts.md` | One actionable future task per finding or shared root cause, plus dependencies. |
| `playtest-log.md` | Executed sessions and results; unexecuted protocols are clearly labeled. |
| `removal-candidates.md` | Evidence and dependency checks for possible simplifications or removals; no deletions. |
| `art-ui-redesign.md` | When relevant: screen/art-system recommendations, alternatives, selected direction, and validation criteria. |

Use [the project brief](templates/project-brief.md) to supply context. The [report template](templates/audit-report.md), [finding template](templates/finding.md), and [implementation task template](templates/implementation-task.md) keep handoffs consistent.

## What evidence makes possible

| Access available | What a reviewer can reasonably assess |
| --- | --- |
| Repository files | Configuration, implementation paths, dependencies, serialized assets, and static risks. |
| Screenshots | Visible layout, hierarchy, style, and readability at the captured resolution and state. |
| Video and audio | Recorded feedback, motion, pacing, transitions, and sound at the captured conditions. |
| An authorized isolated Editor or build | Reproducible interaction, tests, and runtime behavior for the configurations actually exercised. |
| Target-device profiler or build evidence | Measured performance or build behavior for that specific device, build, and capture. |

Source access alone cannot establish that the game feels good, sounds balanced, runs smoothly, or is ready to ship. Missing evidence is a coverage limitation, not proof of a defect.

## Working rules

- The original game remains unchanged during an audit, including non-code Unity files and player data. Runtime checks use an authorized isolated copy and disposable test data.
- Recommendations cite evidence. A personal style preference is a design opportunity, not a confirmed bug.
- A missing feature is a defect only when a supported requirement is unmet. Otherwise, explain the suggestion and its tradeoffs.
- Removal candidates stay candidates until dependencies, runtime loading, validation, and rollback have been reviewed and removal is explicitly approved.
- Findings and prompts do not authorize execution. The current user request determines what may be changed.
- Do not publish private game evidence, logs, captures, or reports automatically. This kit's repository is public.

The [workflow](docs/workflow.md) and [evidence and priority rules](docs/evidence-and-priorities.md) explain how to apply these boundaries. [Official Unity reference starting points](docs/reference-sources.md) help reviewers check version-specific behavior. Prompt instructions guide behavior; they are not a filesystem sandbox. Use a read-only source mount or an isolated copy when enforced separation is required.

GitHub also includes templates for [audit requests](.github/ISSUE_TEMPLATE/audit-request.md) and [individual findings](.github/ISSUE_TEMPLATE/audit-finding.md). They structure a report without automatically opening an issue or authorizing game changes.

## Repository status

The kit is ready to use. **No target game has been audited in this repository yet.** The `reports` folder contains guidance, not findings about a supplied game.
