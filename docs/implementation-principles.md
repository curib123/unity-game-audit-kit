# Default implementation principles

**Default: Editor-first HYBRID.** Use Unity's existing authoring workflow for
authored content and focused C# for behavior. Keep the solution simple, modular,
dynamic and flexible for real requirements, easy to tune, and efficient against
the game's actual performance targets. These are implementation policies; they
do not establish that a game is optimized or that a proposed change will be faster.

## Scope and authorization

Apply this policy to audit recommendations, future task plans, and authorized
implementation. It does not expand permission to change the target game.
`AUDIT_ONLY` and `PLAN_ONLY` keep the original game unchanged: do not open or
import it in Unity just to follow an Editor-first recommendation. Use supplied
evidence and authorized isolated validation as defined in [AGENTS.md](../AGENTS.md).
Carry the chosen approach into the [implementation task](../templates/implementation-task.md).

Respect the actual Unity/package versions, platform constraints, team workflow,
architecture, and selected art/UI direction. Procedural generation, code-authored
content, and established UI-framework patterns remain valid when they fit the
requirements. A different authoring approach alone is not a defect. Explain any
proposed migration through a concrete benefit, bounded cost, and approved scope.

## Choose the smallest useful hybrid

- Prefer existing scenes, prefabs, components, Inspector references, serialized
  tuning, and the project's layout/data tools for authored content and wiring.
- Use simple C# for game rules, state transitions, input responses, interactions,
  validation, and required dynamic runtime behavior.
- Use the current UI workflow: for example, prefab/Canvas authoring or UI Toolkit
  layout and style assets with UI Builder where appropriate. Preserve a working
  framework; this default imposes neither a replacement nor a no-code mandate.
- Keep ordinary tuning and content changes accessible through the owning
  component or established authoring tools when that helps the people doing them.
- Reuse a suitable component, asset, helper, or framework before adding a new
  dependency. Avoid new managers, global event buses, DI frameworks, or ECS solely
  to solve a small local feature. Existing appropriate systems remain valid.
- Choose the simplest implementation that meets the current acceptance criteria.
  Record a real extension need before adding a generic framework for it.

## Modularity and state ownership

- Give each component or module a cohesive responsibility and a clear owner for
  mutable state. Make dependencies visible through references or the project's
  established dependency mechanism.
- Prefer composition and local references when sufficient. A short helper or
  single focused component can be the right boundary. Avoid a separate interface,
  class, service, or event channel for every trivial operation.
- Separate rules, presentation, and persistence where their different lifetimes,
  reuse, or test requirements justify it. Avoid splitting them mechanically.
- Define initialization, subscription, cancellation, teardown, and reset behavior
  for the affected owners. Check scene changes, retries, pooled reuse, and repeated
  sessions where relevant to the actual lifecycle.
- Keep wiring readable and changes local. Explain a new abstraction by the
  concrete duplication, coupling, or lifecycle problem it resolves.

## Configuration and dynamic behavior

- Put local settings on the component that owns them, using serialized fields
  where useful. Introduce shared ScriptableObject or configuration assets when
  several consumers or content variants gain a real authoring/reuse benefit.
- Keep runtime mutable state separate from shared configuration: for example,
  current health belongs to the runtime owner while a reused definition can hold
  starting values. Make any intentional shared mutable state and reset rules explicit.
- Preserve serialization, asset/`.meta` identity, GUID references, and intentional
  prefab overrides. Treat field/type changes and data migration as scoped work.
- Support actual content variations through data or parameters. Prefer suitable
  explicit references or existing stable identifiers over fragile magic-name
  lookups and hardcoded scene indices; follow the project's loading system.
- Make UI and interaction respond to the supported resolutions, safe areas,
  locales, input methods, and content lengths. Select real required cases instead
  of inventing hypothetical platforms or unlimited generality.
- Validate relevant missing/invalid data and define useful defaults or failure
  behavior. Avoid scattering the same setting across unrelated scripts and assets.

## Fast iteration and measured performance

- Favor a short edit–tune–validate cycle: simple scene/prefab wiring, understandable
  fields, focused code, and limited new dependencies. Account for the maintenance
  cost of new tooling as well as its initial convenience.
- Avoid needless work in identified hot paths. Refresh on change when suitable;
  per-frame work remains appropriate for behavior that needs continuous updates.
- Cache only with clear ownership, lifetime, and invalidation. Pool when measured
  allocation/creation churn or an established project pattern justifies the reset
  and lifecycle complexity. Inspect reused state and subscriptions.
- Record the relevant frame-time, memory, loading, or other agreed budget and its
  requirement source. Use `Unknown` when no target is supplied; never impose a
  universal FPS threshold or claim that architecture alone guarantees speed.
- Support improvement claims with baseline and changed measurements on the same
  device, build configuration, quality settings, and representative workload.
  Record revisions, capture conditions, measurement method, and evidence paths.
- Keep static cost hypotheses separate from measured results. If profiling or
  target hardware is unavailable, state the limit and the check still required.

## Example routing decisions

These examples illustrate a decision process, not required architecture. Reuse the
project's existing solution when it already meets the need.

| Feature | Editor/content work | Focused code and configuration | Validation |
| --- | --- | --- | --- |
| Health HUD | Author layout, references, styling, and visibility states in the current UI workflow. | Health owner exposes changes; a small presenter updates the view. Keep local display tuning on its owner. | Damage/heal/death, owner replacement, scene teardown, supported screens and locales. |
| Spawn waves | Author spawn points and prefab references. | Small wave controller owns progress; local fields or shared wave data according to actual reuse. | Wave limits, missing references, restart, active-object lifecycle; measure peak workload. |
| Item variants | Reuse prefabs and author content definitions through existing tools. | Shared item definitions if reuse warrants them; per-instance charges/durability stay with the runtime owner. | Variant data, independent instance state, equip/drop/reload behavior as supported. |
| Procedural room | Author reusable pieces and placement constraints where useful. | Existing generator or focused generation code owns runtime assembly; expose relevant parameters. | Required seeds, bounds, references, regeneration/reset, and representative generation cost. |

## Editor access, automation, and handoff

When Editor tools are unavailable, complete safe authorized file/code work that
can be done correctly with the available evidence. Identify the exact remaining
manual Editor steps: asset and object paths, component additions, reference
assignments, field values, prefab overrides, and validation commands/scenarios as
applicable. Mark uncertain details explicitly. Do not rebuild an authored project
at runtime merely to bypass missing Editor access or claim scenes are wired from
code inspection alone. Report completed work and unverified integration separately.

Use existing Editor tooling first. Custom Editor automation needs a real repeated
task or justified scale, bounded paths/operations, and a reviewable preview or
documented expected results before execution. Inspect actual results afterward.
Keep automation within the authorized scope; install no unsolicited packages.

Include this compact handoff in the task plan and update it after execution:

- **Editor changes:** affected scenes/prefabs/UI, object paths, wiring and overrides.
- **Code changes:** focused behaviors, responsibilities, and affected files.
- **Data:** local fields/shared definitions, defaults, references, migration needs.
- **Reason:** why this split fits the requirement and existing project constraints.
- **State owner:** runtime owners, dependencies, lifetime, reset and teardown rules.
- **Dynamic cases:** required variations, content limits, UI/input/platform cases.
- **Performance target and evidence:** budget or `Unknown`, baseline/comparison,
  environment and capture paths; clearly label unmeasured expectations.
- **Validation remaining:** performed checks and results, exact manual Editor steps,
  blocked checks, and the evidence needed to verify integration and behavior.

Use [official Unity references](reference-sources.md) for the target's exact
Editor/package versions when checking prefab, serialization, configuration,
UI authoring, lifecycle, or profiling details. Engine documentation supports those
mechanics; project evidence and acceptance criteria determine the recommendation.
