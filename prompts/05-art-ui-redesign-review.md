# Art and UI improvement or redesign review

Use this focused prompt when you want to know whether an existing game's art and interface suit its intended experience, and what should change. It can also expand art/UI findings from the full studio audit. It produces a design recommendation and future tasks while keeping the original game unchanged.

Copy the prompt below and supply the available evidence. Visual mockups and replacement assets require suitable tools; this repository does not include an image generator or Unity editor integration.

```text
Review my existing Unity game's art and UI, then recommend the appropriate
extent of improvement or redesign. Act as an art director, UI/UX designer,
accessibility reviewer, player-experience reviewer, and Unity technical
reviewer. Base your conclusions on the game's goals and actual evidence.

MODE: AUDIT_ONLY
KIT_ROOT: <path-to-unity-game-audit-kit>
TARGET_GAME: <absolute-project-path-or-repository-URL>
TARGET_REF: <commit/build; resolve and record the actual baseline>
OUTPUT_ROOT: <report-folder-outside-the-original-game>
GAME_INTENT: <genre, player fantasy, tone, audience, stage, and goals>
TARGET_MATRIX: <platforms, screens/aspect ratios, controls, locales>
CURRENT_EVIDENCE: <screenshots, gameplay video, UI flow recordings, source>
EXISTING_FINDINGS: <AUD IDs/report, or none>
STYLE_REFERENCES: <owner-supplied references and preferences, or unknown>
PRESERVE: <identity, mechanics, recognizable elements, working interactions>
CONSTRAINTS: <time, asset budget, performance targets, technical limits>
MOCKUPS: text recommendations only unless visual concepts are requested
RUNTIME_SCOPE: supplied evidence and source only unless my current request
               already authorizes specific isolated runtime checks

1. ESTABLISH THE BASELINE AND READ-ONLY BOUNDARY

Read AGENTS.md, docs/evidence-and-priorities.md,
checklists/design-ux-art-audio.md, and templates/art-ui-redesign.md.
Follow the applicable target-project instructions. Distinguish the kit,
original game, and report output. Keep the original code, scenes, prefabs,
assets, .meta files, import settings, packages, settings, and player data
unchanged. Do not implement, delete, upgrade, save, or replace game content.

Record the target revision/build, existing local changes, evidence sources,
and limits. Keep output outside the original game. Editor, import, build,
play, or test operations require already-authorized isolated copies and
disposable saves/services. Otherwise continue with supplied evidence and
mark the affected runtime checks unperformed. Preserve Console evidence.

2. DETERMINE WHAT SUITABLE MEANS FOR THIS GAME

Establish genre, intended audience, core activities, tone, target devices,
input methods, supported languages, milestone, and existing art direction.
Distinguish documented intent, owner preferences, and reviewer assumptions.
Identify successful choices before recommending changes. Do not impose a
different genre, realism, minimalism, or visual trend as a universal goal.

Use screenshots to assess only visible states and their recorded conditions.
Use motion or interaction evidence for navigation, transitions, feedback,
and readability during gameplay. Source can expose structural risks but
does not establish aesthetic quality. Without suitable visuals, record the
missing evidence and provide a conditional review plan, not a verdict that
the current art or UI is bad. Do not invent player reactions or measurements.

3. REVIEW REPRESENTATIVE SCREENS AND ART SYSTEMS

Sample the main menu, gameplay HUD, pause/settings, and relevant selection,
inventory, dialogue, results, loading, and error screens that actually exist.
Sample important characters, environments, props, icons, materials, lighting,
camera views, animation, and effects where relevant to the requested scope.
Do not treat absent optional screens or systems as missing requirements.

Assess these relationships using actual evidence:
- Player tasks and information hierarchy: what needs attention first?
- Layout: grouping, spacing, density, alignment, safe areas, and resizing.
- Typography: reading distance, contrast, wrapping, scaling, and locales.
- Interaction: navigation, focus, targets, labels, feedback, and recovery.
- Component states: idle, focus/hover, selected, disabled, loading, and error.
- Art cohesion: palette, shape language, icons, materials, lighting, and detail.
- Gameplay readability: silhouettes, focal contrast, threats, interactables,
  HUD obstruction, and overlapping effects at gameplay distance.
- Accessibility: color-independent cues, text, focus, motion, and input needs.
- Feasibility: actual UI framework, asset reuse, production effort, supported
  devices, and measured budgets; do not prescribe a framework migration.

Record specific problems and player impact rather than labels such as ugly,
outdated, or unprofessional without an explanation. Separate defects from
design opportunities. Reuse existing AUD IDs and merge shared root causes.

4. CHOOSE THE APPROPRIATE EXTENT OF CHANGE

Assign a strategy to each reviewed screen or art system:
- Keep: evidence supports the existing approach; preserve its strengths.
- Enhance: focused changes to readability, spacing, states, or asset treatment
  can address the observed problem within the current structure and identity.
- Restructure: hierarchy, navigation, grouping, or composition needs changing
  while the overall identity remains appropriate.
- Redesign: a broader visual or interaction direction is justified by an
  evidenced mismatch with the intended experience or an explicit new goal.
- Investigate: evidence is insufficient to choose a justified intervention.

These are design strategies, not new finding types, severity levels, or
approval states. Justify the choice and scope. A substantial redesign is a
proposal, not permission to implement. Missing visuals alone do not justify
a redesign. Keep unsupported hypotheses and remaining questions explicit.

5. PRODUCE A SPECIFIC RECOMMENDATION AND MEANINGFUL ALTERNATIVES

For every actionable screen/system, record the current problem, evidence,
expected behavior or design goal, intended player benefit, and what remains.
Describe the proposed layout, flow, typography, palette, icon treatment,
component states, and art direction as relevant. Specify responsive and
input behavior instead of assuming a single screenshot proves usability.

For a material restructure/redesign, compare the recommended direction with
a credible smaller change or keeping the current approach. Add a second
design direction only when it represents a meaningful choice. For a small
local fix, one clear proposal is enough. Explain benefit, tradeoffs, effort,
dependencies, accessibility, migration, and performance uncertainty.

Record the recommendation separately from the user's selected direction.
An existing user instruction to adopt a named or documented recommendation
counts as selection; do not ask again. Otherwise keep selection Pending.
Do not silently turn a suggested art direction into an approved decision.

If visual concepts are requested and suitable tools are available, create
them only as separate report artifacts outside the game. Clearly distinguish
current screenshots, annotations, and proposed concepts. Record any current
image used as a reference and the aspect ratio/state being illustrated.
Never describe a concept as implemented or tested. If tools are unavailable,
provide a concrete written specification and note the missing visual output.
Concept approval does not authorize importing assets or editing the game.

6. PREPARE THE DESIGN BRIEF AND FUTURE IMPLEMENTATION TASKS

Write art-ui-redesign.md using templates/art-ui-redesign.md in OUTPUT_ROOT.
Include baseline, scope/coverage, supported strengths, screen/system inventory,
findings, strategy recommendations, alternatives, tradeoffs, selection state,
and acceptance criteria. Update existing findings and coverage when expanding
an audit; preserve IDs and previous work. Do not duplicate the same problem.
Resolve links for the final report folder; replace template instructions
with links to the actual finding records and future task prompts.

Acceptance criteria must describe observable outcomes in the supported
conditions: legible required information, reachable controls, correct states,
responsive layout, preserved identity, or measured limits when agreed.
List visual comparisons, interaction checks, device/input cases, and needed
player review separately from checks already performed. A good-looking mockup
does not establish runtime behavior or improved task completion.

Prepare scoped future tasks with templates/implementation-task.md or
prompts/02-generate-fix-prompts.md. Reference the exact design direction,
finding IDs, affected systems/assets, dependencies, acceptance criteria,
validation, and rollback. Uncertain causes get investigation tasks. Pending
design choices remain conditional plans. Do not bundle all alternative
directions into one implementation request.

Tasks default to planning. Later execution uses
prompts/03-implement-approved-findings.md only when the user requests it for
the selected scope. Verification uses prompts/04-verify-fixes.md against the
actual implementation, not concept images alone.

7. CLOSE THE REVIEW

Compare the original game's preserved state with the baseline and disclose
the limits of that check. Do not reset unexpected changes away. Summarize
which areas to keep, enhance, restructure, redesign, or investigate, and why.
Link the brief and future tasks. Identify the highest-value remaining evidence
or design decision. Do not claim the game has been redesigned, publish private
captures, implement changes, or deploy as part of this review.
```
