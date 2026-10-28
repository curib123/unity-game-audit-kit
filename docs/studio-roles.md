# Studio roles and review responsibilities

Use these roles as review lenses for an existing Unity game. They do not imply that twelve people have played the game or endorsed a recommendation.
This kit contains no assessment of a particular game until a project and review evidence are supplied.
The coordinator activates only the roles relevant to the game's intended audience, platform, inputs, development stage, and agreed scope.
Protect the game's successful choices and intentional style; a preference for another genre, visual language, or business model is not a defect.

## Shared review contract

- Keep the original project read-only: no edits to code, assets, scenes, prefabs, packages, or project settings.
- Builds, Play Mode, and editor operations that write data require an isolated disposable copy and already authorized scope, with disposable saves and test services.
- Keep reports under `reports/<game-slug>/<YYYY-MM-DD>-<short-sha>/` outside the target game; do not publish private evidence automatically.
- Establish the intended player experience and actual target devices before applying a checklist.
- Separate observed evidence, interpretation, and proposed action in every finding.
- Source inspection can identify structural risks; it cannot establish that visuals, movement, music, or sound feel satisfying.
- Request missing evidence or mark the affected check **Blocked**. Do not manufacture observations to fill a role's report.
- Review roles do not authorize implementation, deletion, publishing, purchases, messages, or changes to live services.

## Common vocabulary

| Field | Allowed values |
| --- | --- |
| Type | Defect; Risk; Design opportunity; Missing requirement; Removal candidate |
| Confidence | Confirmed; Likely; Possible |
| Severity | Critical; High; Medium; Low; Informational |
| Priority | P0; P1; P2; P3 |
| Coverage | Checked; Partially checked; Not checked; Blocked; Not applicable |

Assign one canonical finding ID, such as `AUD-001`, to a distinct underlying problem.
**Confirmed** requires evidence that directly supports the claim; it does not mean every role agrees about its importance.
A **Missing requirement** needs an established requirement and evidence of its absence. An attractive unrequested feature is a **Design opportunity**.
Coverage describes what was examined; confidence describes the strength of a particular claim. Keep these fields separate.
Use the shared [evidence and priority rules](evidence-and-priorities.md) to justify severity and priority independently.

## 1. Review coordinator / studio producer

- **Questions:** What is the intended experience, current milestone, target audience, supported hardware, and review boundary? Which unknowns prevent a useful conclusion?
- **Evidence:** Project brief, supplied build identity, scene list, supported device/input matrix, permissions, stakeholder requirements, and every role's evidence register.
- **Output:** Review scope, role assignments, coverage map, consolidated findings, prioritized decisions, and evidence requests with owners.
- **Judgment:** Rank player harm and likely benefit before aesthetic preference or implementation convenience; expose uncertainty and dependencies.
- **Boundary:** Deduplicate overlapping observations without erasing disagreements. Record one finding with contributing roles when they share a root cause.

## 2. Gameplay and systems designer

- **Questions:** Are controls responsive and predictable? Does the core loop deliver its intended decisions, challenge, feedback, and recovery? Does progression support that loop?
- **Questions:** If an economy exists, are sources, sinks, rewards, costs, scarcity, and failure consequences understandable and consistent with the game's goals?
- **Evidence:** Authorized runtime observations, recorded input and response, representative encounters, progression paths, balancing tables, and relevant system configuration.
- **Output:** Core-loop map, friction observations, balance hypotheses, preserved strengths, and bounded experiments with measurable player outcomes.
- **Boundary:** A value in a configuration file is not proof of good or bad game feel; label unplayed balancing conclusions as hypotheses.

## 3. Player / exploratory tester

- **Questions:** What does a player try next? Where do they hesitate, get stuck, misread feedback, lose progress, or recover? Can a problem be reproduced?
- **Evidence:** Session notes, exact reproduction steps, build/device/input identity, timestamped video, and actual participant feedback when supplied or collected within scope.
- **Output:** Reproducible behavior reports, task-completion observations, edge cases, and separate persona-based hypotheses for later validation.
- **Boundary:** Simulated beginner, expert, or returning-player perspectives are hypotheses. Never present them as real interviews, quotes, usability results, or audience consensus.
- **Boundary:** Separate the reviewer's preferences from observed task failures and from feedback given by actual players.

## 4. Level, onboarding, and narrative designer

- **Questions:** Can players form a useful mental map, identify goals, learn safely, discover possibilities, and understand consequences? Does pacing support the intended world and story?
- **Evidence:** Level walkthroughs, spatial layouts, route and camera captures, teaching sequences, objective text, narrative beats, checkpoint placement, and encounter timing.
- **Output:** Navigation and teaching breakdowns, pacing observations, narrative continuity risks, and proposals that preserve intended exploration or ambiguity.
- **Boundary:** Do not treat deliberate mystery, difficulty, nonlinear routes, or sparse narrative as defects without relating them to the intended experience.
- **Handoff:** Escalate unclear feedback to UI, audio, or VFX roles under the same finding when the underlying problem is shared.

## 5. UX and interaction designer

- **Questions:** Can players find, understand, complete, cancel, undo, and recover from important tasks? Does the flow match the active input method and player context?
- **Evidence:** End-to-end flows, state transitions, menu hierarchy, focus paths, input switching, loading and error states, and interrupted-session recovery.
- **Output:** Task maps, navigation obstacles, interaction inconsistencies, missing state handling, and acceptance criteria for revised flows.
- **Boundary:** Judge information architecture through representative tasks; a screenshot alone cannot establish whether a flow works.
- **Handoff:** Coordinate with UI on presentation and with accessibility on alternatives, avoiding separate tickets for the same blocked task.

## 6. UI, layout, and typography designer

- **Questions:** Is the right information prominent at the right moment? Are labels, text, alignment, spacing, contrast, focus, and feedback legible on supported screens?
- **Evidence:** Screenshots at target sizes and aspect ratios, safe-area captures, localization samples, text scaling, selected/disabled/error states, and UI configuration.
- **Output:** Annotated screen observations, hierarchy and consistency issues, clipping or overlap evidence, and layout criteria tied to actual supported devices.
- **Boundary:** Serialized anchors or font sizes can suggest risks; rendered evidence is needed to confirm the visual result.
- **Preserve:** Record effective components and intentional visual conventions before proposing changes to a UI system.

## 7. Art director / environment and character artist

- **Questions:** Do palette, materials, lighting, silhouettes, proportions, texture density, and composition form a coherent intended style? Can players read gameplay-relevant objects?
- **Evidence:** Gameplay-distance captures, representative environments and characters, lighting variants, art references supplied by the owner, and asset provenance when relevant.
- **Output:** Art cohesion observations, silhouette and readability issues, distracting inconsistencies, retained strengths, and targeted art briefs.
- **Boundary:** An asset list or source code cannot establish aesthetic quality. Missing visual evidence blocks visual conclusions.
- **Preserve:** Do not replace stylized, low-resolution, minimalist, or unconventional work merely to match the reviewer's taste.

## 8. Animation, camera, and VFX designer

- **Questions:** Do pose, timing, transitions, anticipation, contact, recovery, and camera response make actions understandable? Do camera motion and framing support control?
- **Questions:** Do effects communicate source, direction, magnitude, timing, success, failure, and danger without obscuring gameplay? Are overlapping signals distinguishable?
- **Evidence:** Motion playback across representative actions, transition interruptions, overlapping effects in gameplay, quality variants, and camera/input context.
- **Output:** Animation, camera, and feedback observations, motion comfort risks, retained strengths, and precise review clips for future revisions.
- **Boundary:** Still images cannot validate timing, blending, motion smoothness, or camera comfort. State the limits of recorded frame rate and capture quality.
- **Boundary:** Isolated effects do not prove gameplay readability. Do not claim photosensitivity safety from casual viewing or source inspection.
- **Handoff:** Link animation, collision, and input observations when they describe one action-feedback mismatch.

## 9. Sound designer / music and audio director

- **Questions:** Can players hear necessary cues? Are dialogue, effects, ambience, and music balanced across relevant situations and supported outputs?
- **Questions:** Do musical mood, pacing, identity, repetition, intensity changes, and silence support the intended world and actual play duration?
- **Evidence:** Actual audio playback across quiet/dense scenes and narrative states, transition captures, settings states, capture details, and metering for numerical claims.
- **Output:** Timestamped cue, mix, spatial-audio, loop, and music-transition observations; retained strengths; and briefs with concrete listening criteria.
- **Boundary:** No judgments about loudness, clarity, distortion, balance, or musical fit without playback. Imports and mixer configuration establish only structural evidence.
- **Boundary:** Distinguish recording artifacts from game-audio problems. No soundtrack genre or density is mandatory; assess silence and repetition against intent.
- **Handoff:** Coordinate audio, visual, and haptic alternatives; keep artistic preference distinct from an essential cue being inaudible.

## 10. Unity engineer / technical QA reviewer

- **Questions:** Do code, serialization, references, initialization, state transitions, saves, and dependencies support the intended behavior? What existing tests or logs establish failures?
- **Evidence:** Pinned source, scenes/prefabs and GUID relationships, package/configuration records, existing logs/tests, and authorized isolated reproduction when available.
- **Output:** Specific invariant violations, reproduction protocols, cause hypotheses, technical dependencies for creative findings, and reference traces for removal candidates.
- **Boundary:** Static reasoning can confirm a source-level defect when complete, but it does not prove the game was run, looked correct, or felt satisfying.
- **Handoff:** Connect technical causes to the player task affected. Review vendor integration separately from vendor internals, and disclose sampling.

## 11. Performance, compatibility, and release reviewer

- **Questions:** Does measured behavior meet the project's supported device and release targets? Do loading, long sessions, recovery, and build variants preserve intended play?
- **Evidence:** Target-device profiler captures, frame/memory/loading measurements, build reports, compatibility results, and reproduction conditions with baseline identity.
- **Output:** Measured bottlenecks, compatibility gaps, release risks, required evidence, and narrowly scoped verification protocols.
- **Boundary:** Do not infer performance from object counts or code style alone, or declare release readiness from a successful build or source review.
- **Handoff:** Coordinate with art/audio/design before suggesting reductions that alter the experience; tie budgets to project requirements and measured limits.

## 12. Accessibility and platform-experience reviewer

- **Questions:** Can intended players perceive information, operate controls, understand tasks, and recover using their supported devices and available settings?
- **Evidence:** Visual/hearing/motor/cognitive task reviews, supported display and controller combinations, subtitle samples, input remapping, focus behavior, and assistive-technology evidence when in scope.
- **Output:** Barrier reports tied to player tasks, settings discoverability gaps, hardware limitations, and concrete alternatives with verification needs.
- **Boundary:** A checklist pass is not certification. Do not claim support for a platform or assistive technology that has not been tested.
- **Handoff:** Integrate accessibility into each discipline's findings; retain a separate finding only when the barrier has a distinct cause or remedy.

## Collaboration and synthesis

1. The coordinator records the game brief, evidence received, authorized operations, and target matrix before distributing reviews.
2. Each active role states what it examined, its coverage status, the strongest retained strengths, and evidence limitations.
3. Roles submit observations with evidence locations, conditions, affected player tasks, and alternative explanations.
4. The coordinator merges observations that share a root cause and assigns one `AUD-001`-style ID; preserve linked symptoms and role contributions.
5. Roles may disagree about aesthetics, expected benefit, or tradeoffs. Document the disagreement and the evidence that could resolve it; do not manufacture a unanimous studio verdict.
6. Prioritize by severity of player impact, exposure, reproducibility, affected audience, recovery cost, and confidence. Consider effort and dependencies when sequencing work.
7. Produce future implementation prompts only after the recommendation is sufficiently specific; the audit itself makes no project changes.

## Required shape of an actionable recommendation

Every proposed change, experiment, or removal candidate must include:

- **Finding:** Canonical ID, title, type, confidence, severity, priority with rationale, coverage, affected experience, and contributing roles.
- **Evidence:** Exact source or capture, relevant timestamp or path, build/device/input conditions, reproduction steps where applicable, and missing evidence.
- **Reasoning:** Observed behavior, player impact, intended behavior or requirement, alternative explanations, and any unresolved disagreement.
- **Expected player benefit:** A concrete task or experience that should improve; do not substitute a stylistic preference for a benefit.
- **Dependencies and boundaries:** Prerequisites, affected systems/assets, supported targets, choices to preserve, approval needs, and safe rollback requirements.
- **Testable acceptance criteria:** Observable pass/fail outcomes under named conditions, including regressions to check; define measurements before claiming a percentage improvement.
- **Needed evidence:** Captures, playback, user research, reference traces, or runtime checks required to confirm the problem and later verify the result.
- **Future implementation prompt:** A bounded instruction carrying the evidence, benefit, dependencies, acceptance criteria, and verification plan into a separately authorized implementation task.

Use the [finding template](../templates/finding.md) and [implementation task template](../templates/implementation-task.md) for the full handoff.
For removal candidates, complete the [removal review](../templates/removal-review.md), including reference tracing and verified rollback readiness, before any later approval; never delete files as part of this audit.
Use [the design, UX, art, and audio checklist](../checklists/design-ux-art-audio.md) to collect observations without treating unchecked questions as findings.
