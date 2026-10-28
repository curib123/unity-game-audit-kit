# Design, UX, art, audio, and accessibility review

This is an evidence collection checklist for an existing Unity game, not a set of findings about this repository.
No game has been supplied with this kit. Do not infer that a feature is absent or broken merely because its evidence has not been provided.
Apply the relevant sections to the actual genre, audience, supported platforms, inputs, and development stage.
An intentional limitation or unusual style is not automatically a problem. Record successful choices that a future implementation should preserve.

## How to record a check

- Assign coverage: **Checked**, **Partially checked**, **Not checked**, **Blocked**, or **Not applicable**; give a reason for limitations and exclusions.
- Record the evidence location, build or revision, device, resolution/aspect ratio, input, game state, and relevant capture timestamps.
- Separate a direct observation from an interpretation, a preference, or a persona-based hypothesis.
- Actual player feedback requires an actual source. Never invent participants, play sessions, quotations, or agreement among roles.
- Use finding types **Defect**, **Risk**, **Design opportunity**, **Missing requirement**, or **Removal candidate**.
- Use confidence **Confirmed**, **Likely**, or **Possible** and severity **Critical**, **High**, **Medium**, **Low**, or **Informational**.
- A missing feature is a **Missing requirement** only when a real requirement establishes it; otherwise assess it as an opportunity or leave it outside scope.
- Reuse one `AUD-001`-style ID for observations with the same root cause. A second discipline's observation does not automatically require another finding.
- Every actionable recommendation needs expected player benefit, dependencies, testable acceptance criteria, and needed evidence; use the closing handoff template.
- Apply the shared [evidence and priority rules](../docs/evidence-and-priorities.md); justify `P0`–`P3` priority separately from severity.

## 0. Scope and evidence gate

- [ ] Identify intended player fantasy, core activities, tone, challenge, session length, audience, and current milestone from supplied evidence.
- [ ] Record supported platforms, hardware limits, displays, languages, input methods, offline/online assumptions, and accessibility commitments.
- [ ] Name representative scenes, modes, difficulty levels, progression states, and flows to sample; explain what remains outside that sample.
- [ ] Confirm that the original project stays read-only: no code, asset, scene, prefab, package, or settings edits.
- [ ] Use an isolated disposable copy and already authorized scope before builds, Play Mode, or editor operations that write data; use disposable saves and test services.
- [ ] Keep reports under `reports/<game-slug>/<YYYY-MM-DD>-<short-sha>/` outside the original target project and preserve the recorded baseline.
- [ ] Record whether screenshots, motion capture, interactive runtime, audio playback, requirements, and actual player feedback are available.
- [ ] Request missing evidence or mark the corresponding check **Blocked**; do not replace observation with invented experience.
- [ ] Treat source/configuration inspection as evidence of structure or a potential risk, never proof of aesthetic satisfaction or playability.

## 1. Moment-to-moment play and game feel

Evidence: input/response observations or recordings in representative gameplay, with device and capture limitations stated.

- [ ] Can players predict what an input will do, and recognize when it has been accepted, ignored, interrupted, or buffered?
- [ ] Examine movement start/stop, turning, aiming, interaction reach, collision contact, and action recovery as relevant to the game.
- [ ] Check consistency among visible contact, hit detection, animation, sound, VFX, haptics, and gameplay consequences.
- [ ] Identify unintentionally unresponsive windows, inconsistent interaction priorities, repeated-input problems, and unclear control lockouts.
- [ ] Assess camera framing, tracking, occlusion, target visibility, aiming relationships, and player control during transitions.
- [ ] Check camera shake, motion blur, acceleration, FOV changes, and other motion effects against available comfort controls and intended experience.
- [ ] Observe whether failure feels understandable and recovery preserves the intended pace; distinguish deliberate commitment from accidental friction.
- [ ] Preserve actions and feedback combinations that already communicate well; do not prescribe a universally faster or more exaggerated feel.

## 2. Core loop, progression, balance, and economy

Evidence: representative loop completions and progression states, design intent, configuration/data, and telemetry if supplied and within scope.

- [ ] Describe the actual loop: player goal, meaningful choice, action, feedback, consequence, reward, and reason to continue.
- [ ] Determine whether repeated tasks retain useful decisions or become friction inconsistent with the game's intent.
- [ ] Examine difficulty, skill expression, risk/reward, dominant strategies, and recovery across representative player skill hypotheses.
- [ ] Check whether upgrades, unlocks, objectives, and rewards communicate their effects before and after a decision.
- [ ] Inspect pacing of new mechanics, challenge spikes, plateaus, resource bottlenecks, and late-game repetition where evidence exists.
- [ ] If an economy exists, map resource sources, sinks, prices, earnings, scarcity, caps, and consequences of irreversible spending.
- [ ] Check whether currencies, purchase terms, reward odds if applicable, and affordability are understandable in the provided experience.
- [ ] Consider exploits or unwinnable resource states as hypotheses until reproduced; do not claim balance from one numeric table.
- [ ] Mark economy, monetization, multiplayer balance, or long-term progression **Not applicable** when the actual game does not include them.

## 3. Teaching, level design, navigation, and world

Evidence: first-use and return sessions, level routes, screenshots/video, objective text, narrative sequences, and checkpoint context.

- [ ] Can a new player identify the first meaningful goal and perform the first action without unexplained assumptions?
- [ ] Does teaching introduce information near its use, allow safe practice, and recognize prior learning or alternative paths where intended?
- [ ] Check tutorial interruption, retry, skip, revisit, input switching, and resuming after a long absence.
- [ ] Examine spatial landmarks, entrances/exits, affordances, route choices, signposting, and the distinction between decorative and interactive objects.
- [ ] Check camera and geometry together for occluded hazards, misleading paths, accidental traps, traversal boundaries, and readable encounter spaces.
- [ ] Review checkpoints, respawn position, travel time, backtracking, shortcuts, and resource placement against the intended rhythm.
- [ ] Assess encounter variety, quiet/intense pacing, optional content, and environmental storytelling in the sampled levels.
- [ ] Check consistency among world rules, character motives, dialogue, objectives, and consequences where narrative exists.
- [ ] Distinguish intentional mystery or exploration from lost progress caused by an unreadable goal; document the player task affected.
- [ ] Record absent narrative or sparse environments as design choices unless a requirement or the intended experience establishes a gap.

## 4. UX flows and information architecture

Evidence: end-to-end flow observations across relevant states; screenshots alone give only partial coverage.

- [ ] Map entry, menu hierarchy, start/continue, mode selection, pause, settings, save/load, exit, and return flows that exist.
- [ ] Check whether labels match player expectations, related actions are grouped, and important tasks are discoverable without memorizing paths.
- [ ] Follow the full lifecycle of relevant actions: idle, hover/focus, selected, pending, success, failure, cancellation, retry, and recovery.
- [ ] Examine back/cancel behavior, nested dialogs, focus restoration, modal stacking, and consistency after switching screens or inputs.
- [ ] Check irreversible actions for understandable consequences and appropriate confirmation or recovery, based on their actual risk.
- [ ] Inspect loading, no-content, disabled-feature, unavailable-service, disconnected-controller, and interrupted-session states that apply.
- [ ] Check that errors explain what happened and offer a useful next action without losing valid player work or exposing irrelevant internals.
- [ ] Verify input prompts reflect the active device and mapping, and that simultaneous pointer/controller input does not strand focus.
- [ ] Review settings discoverability, preview, apply/revert, persistence, and safe recovery from unusable display or control choices.

## 5. UI layout, typography, and screen adaptation

Evidence: rendered screens on supported aspect ratios and sizes, safe-area cases, representative localized text, and relevant UI structure.

- [ ] Is visual hierarchy clear for the primary action, current objective, essential status, secondary details, and warnings?
- [ ] Assess spacing, alignment, grouping, density, consistent component states, and intentional use of the game's visual language.
- [ ] Inspect layout anchors, stretch behavior, scaling, and safe areas; verify their rendered effect on the actual target matrix.
- [ ] Check narrow, wide, windowed, resized, handheld, and television viewing cases only where they are supported or required.
- [ ] Examine text size at intended viewing distance, line length, wrapping, truncation, glyph support, punctuation, and localization expansion.
- [ ] Check text/background contrast, transparency over changing gameplay, outline/shadow readability, and selected/disabled/error distinctions.
- [ ] Inspect keyboard/controller focus visibility, navigation order, pointer targets, hit areas, and focus when content scrolls or changes.
- [ ] Confirm HUD elements do not obscure threats, aiming, subtitles, interaction prompts, or information prioritized by the current task.
- [ ] Check responsive reflow, scroll reachability, tooltips, popovers, on-screen keyboards, and orientation changes where applicable.
- [ ] Treat target sizes, contrast goals, and layout tolerances as explicit verification criteria; do not claim compliance without appropriate measurements.

## 6. Art direction, environments, and characters

Evidence: rendered gameplay-distance visuals across representative scenes, lighting and quality settings, plus the intended art direction if supplied.

- [ ] Identify the existing palette, shapes, proportions, material treatment, lighting language, texture/detail density, and stylistic strengths.
- [ ] Check cohesion across environments, characters, props, UI, icons, VFX, and promotional/menu art within their intended roles.
- [ ] Assess silhouettes, value separation, scale cues, and focal contrast for players, threats, pickups, destinations, and interactable objects.
- [ ] Check whether clutter, decorative motion, excessive detail, or lighting hides information required for a player decision.
- [ ] Examine character readability and identity across relevant poses, costumes, teams, camera distances, and lighting conditions.
- [ ] Review environment composition, depth, landmarks, material readability, repeated assets, and transitions between areas.
- [ ] Inspect visible seams, missing materials, inconsistent asset quality, and placeholder content only when rendered evidence supports the claim.
- [ ] Distinguish intentional abstraction, retro treatment, roughness, or asymmetry from accidental inconsistency.
- [ ] Preserve coherent existing style. Describe targeted fixes and references; do not demand realism, visual density, or a genre change.

## 7. Animation, VFX, and feedback

Evidence: motion playback at normal speed and, when useful, slower review; include capture frame rate and gameplay context.

- [ ] Check readable anticipation, action, contact, follow-through, recovery, and transitions for important actions.
- [ ] Examine foot sliding, contact alignment, pose discontinuities, animation interruption, blending, and state changes where observable.
- [ ] Compare animation timing with control availability, hitboxes, interaction completion, vulnerability, and outcome feedback.
- [ ] Check camera cuts, shake, zoom, recoil, and transitions for useful communication, consistent control, and optional intensity reduction.
- [ ] Examine VFX source, direction, magnitude, timing, duration, layering, and attribution during overlapping events.
- [ ] Check success, damage, danger, immunity, healing, cooldown, resource changes, and interaction rejection cues that the game needs.
- [ ] Assess clutter, persistent trails, particles, flashes, screen effects, and obstruction at actual gameplay distances and quality settings.
- [ ] Verify that essential signals remain distinguishable when color, motion, sound, or haptics are unavailable or reduced.
- [ ] Treat flash-related concerns as risks requiring qualified analysis; do not claim photosensitivity safety from casual playback.
- [ ] Mark timing and motion judgments **Blocked** without suitable motion evidence; a still image or animator graph is insufficient.

## 8. Sound design, mixing, music, and haptics

Evidence: actual audio playback from representative play, output-device context, settings states, and capture limitations. No sound judgments without listening.

- [ ] Check cue audibility and priority in quiet and dense situations, including dialogue, danger, interactions, UI, ambience, and music.
- [ ] Listen for masking, abrupt loudness changes, clipping, distortion, unwanted silence, or excessive repetition; distinguish recording artifacts.
- [ ] If reporting loudness, peaks, clipping, or channel behavior numerically, record the measurement method and source; avoid invented thresholds.
- [ ] Check positional direction, distance, occlusion, attenuation, and off-screen cue usefulness where spatial audio is part of play.
- [ ] Review loop boundaries, randomization, repeated-event overlap, scene transitions, pause/resume, fades, interruptions, and loading behavior.
- [ ] Assess whether musical mood, pacing, intensity, repetition, and silence support the intended world and play duration.
- [ ] Check music transitions between exploration, danger, success, failure, narrative, menus, and other states that actually exist.
- [ ] Review master/music/effects/dialogue controls as applicable, mute behavior, persistence, and whether reducing one channel hides essential information.
- [ ] Compare relevant headphones, speakers, mono, or other supported outputs when evidence permits; do not claim untested hardware support.
- [ ] Check subtitles/captions for availability, timing, speaker/context cues, legibility, size/background options, and coverage of necessary non-speech information.
- [ ] Review haptic timing, intensity, repetition, separate controls, and alternatives; do not make vibration the only carrier of essential information.
- [ ] Without playback, report only verified structural observations such as an assigned clip or exposed mixer control; request listening evidence for quality claims.

## 9. Accessibility and hardware experience

Evidence: task-based checks using supported settings and hardware, with participant or assistive-technology evidence where available and authorized.

- [ ] **Visual:** Check text scaling, contrast, color-independent distinctions, HUD readability, alternate cues, and essential information at relevant viewing distances.
- [ ] **Visual/motion:** Review reduced-motion, camera-shake, screen-flash, and other intensity options against the effects actually present.
- [ ] **Hearing:** Check subtitles, captions, visual alternatives for important cues, dialogue clarity options, and play with relevant audio channels reduced or disabled.
- [ ] **Motor:** Review remapping, conflicting bindings, hold/toggle alternatives, repeated-input demands, timing windows, simultaneous inputs, and one-handed needs where in scope.
- [ ] **Motor:** Check pointer precision demands, adjustable sensitivity, controller dead zones, menu focus, and supported device reconnection behavior.
- [ ] **Cognitive:** Review plain labels, readable objectives, tutorial recall, consistent terminology, adjustable pace, pause/retry, and recovery after interruption.
- [ ] **Cognitive:** Check whether memory, time pressure, dense menus, or ambiguous feedback creates an avoidable barrier unrelated to the intended challenge.
- [ ] **Hardware:** Verify supported resolutions, aspect ratios, safe areas, control schemes, screen distance, quality levels, and minimum-device experiences from evidence.
- [ ] **Hardware:** Review small screens, poor speakers, variable performance, offline states, and limited connectivity only where they are relevant to the target audience.
- [ ] Check that accessibility settings are discoverable before a barrier, persist correctly, and work throughout menus and gameplay.
- [ ] Record tradeoffs with creative intent and challenge; describe alternative ways to deliver essential information or operate a task.
- [ ] State coverage limits. A checklist review does not certify accessibility or substitute for feedback from affected players.

## 10. Missing content, excess content, and removal candidates

Evidence: requirements, observed player tasks, complete reference searches, runtime/loading context, and a future rollback plan. No deletion in this audit.
Record each candidate in the [removal review template](../templates/removal-review.md); a search with no matches is not proof of non-use.

- [ ] Separate a required but absent behavior from an optional idea, a planned milestone item, and evidence that has simply not been supplied.
- [ ] Identify redundant menus, misleading options, obsolete tutorial steps, duplicate feedback, distracting effects, and unused content as candidates for investigation.
- [ ] Explain the expected player benefit of simplifying or removing each candidate, including what could be lost and what should be preserved.
- [ ] Trace the candidate's Unity GUID and paths through scene, prefab, material, animation, configuration, and other serialized references, including metadata relationships.
- [ ] Check build inclusion, `Resources`, Addressables, AssetBundles, dynamic string/reflection-based loading, generated content, and platform-specific inclusion.
- [ ] Check server/remote configuration, downloadable content, external tooling, editor workflows, tests, documentation, and build pipeline references as applicable.
- [ ] Identify conditional, indirect, unbuilt, or externally controlled references that a text search cannot settle; keep confidence limited until evidence resolves them.
- [ ] Distinguish a currently unreferenced asset from an intentionally staged, fallback, test, promotional, or future content asset.
- [ ] Require an owner decision, replacement/migration plan if needed, and verified rollback readiness from a restorable revision/backup before future approval; record missing verification as a blocker.
- [ ] Define acceptance checks for all affected flows and builds in an isolated, authorized implementation task; the review itself removes no files or project content.

## 11. Synthesis and future implementation handoff

Use one record per distinct underlying issue. Attach multiple role observations to that record where they strengthen the evidence.
Prioritize player harm or expected benefit, exposure, recovery cost, affected audience, confidence, and dependencies; do not count role votes as impact.
Keep meaningful strengths, deliberate tradeoffs, and unresolved disagreements visible beside proposed changes.
Use the full [finding template](../templates/finding.md) and [implementation task template](../templates/implementation-task.md); the outline below is a compact collection aid.

```text
ID / title: AUD-001 / [specific issue]
Type / confidence / severity / coverage: [allowed labels]
Priority / rationale: [P0–P3, justified independently of severity]
Affected players, task, and target: [who is affected, doing what, under which conditions]
Observed evidence: [path/capture/timestamp, build/device/input, reproduction if applicable]
Expected behavior / basis: [requirement reference, established behavior, or proposed improvement]
Interpretation and alternatives: [why this matters; competing explanations; disagreements]
Expected player benefit: [specific improvement connected to the affected task]
Recommendation: [bounded change, investigation, experiment, or removal candidate]
Dependencies: [systems/assets, preceding decisions, missing inputs, approvals, rollback]
Acceptance criteria: [observable pass/fail outcomes under specified target conditions]
Needed evidence: [what must be collected to confirm the issue and verify the outcome]
Preserve: [existing strengths, style, constraints, supported behavior]
Future implementation prompt: [PLAN_ONLY by default; action + scope + benefit + dependencies + criteria + evidence]
```

When evidence is insufficient, the next prompt should request a bounded investigation rather than direct implementation.
Link the record to the relevant responsibilities in [studio roles](../docs/studio-roles.md).
