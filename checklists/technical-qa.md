# Technical QA checklist

Use this checklist to inspect an existing Unity game and prepare evidence-based findings and future fix prompts. It contains review questions, not audit results. Select checks for the game's intended experience, release stage, supported platforms, and actual architecture.

## Operating boundary

- Keep the original Unity project read-only: do not edit source, scenes, prefabs, assets, `.meta` files, packages, settings, or generated files.
- Opening the Editor, importing, entering Play Mode, executing tests, profiling, and building can write files or execute project code. A repository copy alone does not isolate saves, preferences, accounts, analytics, or remote services.
- Perform those operations only when already authorized, in a disposable project copy with isolated test saves, preferences, output folders, and services. Inspect startup, test, importer, and build hooks before executing them.
- If that authorization or isolation is unavailable, inspect supplied files, logs, captures, and builds statically; mark the affected runtime checks `Blocked` or `Not checked` and state what would unblock them.
- Do not clear the Console, reset or stash another person's work, upgrade Unity, install or update packages, switch the original project's target, or remove caches to make a check pass.
- Store reports under this kit's `reports/<game-slug>/<YYYY-MM-DD>-<short-sha>/`, or another agreed location outside the audited project. Keep original captures private; publish evidence only after sanitization and explicit publication authorization.
- Before and after inspection, record staged, unstaged, and untracked changes separately. Also inventory relevant ignored files and external save/configuration locations; a clean Git diff does not establish that nothing changed.
- Stop a run when it reaches production data, live spending, destructive operations, or unisolated services. Preserve evidence and continue unaffected static checks.

## Recordkeeping and classification

For each applicable section, record the reviewer, date, project revision or snapshot identity, exact scope sampled, evidence paths, limitations, and coverage.

| Field | Allowed values / rule |
| --- | --- |
| Type | `Defect`, `Risk`, `Design opportunity`, `Missing requirement`, `Removal candidate` |
| Confidence | `Confirmed`, `Likely`, `Possible` |
| Severity | `Critical`, `High`, `Medium`, `Low`, `Informational` |
| Coverage | `Checked`, `Partially checked`, `Not checked`, `Blocked`, `Not applicable` |
| Finding ID | Use the shared report's `AUD-001` sequence; checklist IDs identify coverage, not findings. |

`Checked` means the stated scope was inspected; it does not mean it passed. Confirm a defect only when evidence establishes the broken behavior or violated requirement. Static indicators of possible runtime failure are risks until substantiated. Missing features are findings only against agreed requirements or documented game intent; do not impose a standard feature wishlist.

## TQA-01 — Establish the project baseline

- [ ] Identify the real Unity project root, ownership instructions, revision/snapshot, branch if available, and pre-existing local modifications. Record absent Git history as a limitation.
- [ ] Read the exact Unity version and revision, package manifest and lock data, platform support, render pipeline, input solution, scripting backend, and relevant compiler defines.
- [ ] Separate first-party code, embedded packages, vendor assets, samples, generated output, tests, and build artifacts. Attribute findings to the relevant integration or owner.
- [ ] Record intended audience, genre, core loop, milestone, target hardware, minimum supported configuration, required features, and accepted frame-time/memory/loading budgets. Mark unknowns explicitly.
- [ ] Identify boot flow, required scenes, content loading entry points, persistence, network/service use, and supported input devices before choosing samples.
- [ ] Preserve existing Console/log messages with timestamps and available test/build history. Distinguish stale logs from the reviewed revision and pre-existing failures from new observations.
- [ ] Record access limits: source only, serialized assets, existing Editor session, authorized disposable execution, target hardware, audio/video capture, or none.

### Suggested evidence map

These are discovery hints. Verify paths, serialization, active settings, and documentation against the project's exact Unity/package versions; an absent suggested file is not itself a defect.

| Question | Suggested evidence to locate |
| --- | --- |
| Editor version | `ProjectSettings/ProjectVersion.txt`, supplied build metadata, CI configuration |
| Dependencies | `Packages/manifest.json`, `Packages/packages-lock.json`, embedded packages, package ownership notes |
| Renderer and quality | `ProjectSettings/GraphicsSettings.asset`, `ProjectSettings/QualitySettings.asset`, referenced pipeline/renderer assets and platform overrides |
| Player and platform settings | Relevant `ProjectSettings/` assets, platform plugins, actual build command and configuration |
| Scenes included in a build | `ProjectSettings/EditorBuildSettings.asset`, applicable Build Profile assets, custom build scripts, supplied Build Report |
| Input | `.inputactions` assets and input configuration, legacy input settings when used, UI event modules, platform integrations |
| Serialization | `.unity`, `.prefab`, `.asset`, corresponding `.meta` files, assembly definitions; binary assets may require authorized inspection |
| Content delivery | Addressables settings/groups/catalogs if used, AssetBundle tooling, `Resources` directories, streaming/download code |
| Saves and settings | Save subsystem, schema/migration code, test fixtures, discovered device-specific persistent paths and preferences |
| Verification | Test assemblies, existing test results, build/player/editor logs, profiler captures, CI workflow definitions |

## TQA-02 — Architecture and dependency boundaries

- [ ] Trace one representative path from player input through game rules, presentation, persistence, and scene transition; identify ownership and error handling at each boundary.
- [ ] Review assembly references, platform constraints, conditional compilation, editor/runtime separation, and circular or unexpectedly broad dependencies.
- [ ] Check initialization dependencies, service lifetime, singleton/persistent-object behavior, and teardown. Tie coupling concerns to a failure mode or documented maintenance burden.
- [ ] Inspect asynchronous work for cancellation, object lifetime, exception handling, thread assumptions, and repeated or overlapping requests.
- [ ] Review state machines and event subscriptions for duplicate transitions, stale listeners, unintended re-entry, and actions after scene teardown.
- [ ] Inspect plugins and packages for compatible declared versions and known issues relevant to actual use. Verify current advisories against primary sources before alleging a vulnerability.
- [ ] Do not classify file length, preferred patterns, naming, or an unfamiliar framework as a defect without a concrete impact.

## TQA-03 — Unity lifecycle and repeated sessions

- [ ] Trace `Awake`, `OnEnable`, `Start`, update loops, disable/destroy callbacks, and scene load/unload handlers in critical systems; record assumptions about ordering and missing dependencies.
- [ ] Inspect pause, focus loss, suspension/resume, time scale, and quit handling for the supported platform. Avoid assuming all platforms deliver identical shutdown callbacks.
- [ ] Check pooled objects for stale subscriptions, timers, physics state, animation state, ownership, and reset behavior after reuse.
- [ ] Inspect persistent managers for duplication when scenes restart, return to the menu, load additively, or enter through an alternate boot path.
- [ ] Check coroutines, tasks, delayed actions, and callbacks that may outlive their owner or execute twice after recovery.
- [ ] Only if domain reload is disabled in the actual Editor workflow, examine static fields and event registrations across repeated Play Mode sessions; persistence between sessions is documented by Unity.[^domain-reload]
- [ ] Record scene reload configuration separately. An Editor-only repeated-session issue is not evidence of the same behavior in a fresh player process; verify each affected context independently.

## TQA-04 — Scenes, prefabs, serialization, and identity

- [ ] Sample the boot scene, a representative gameplay scene, a heavy scene, shared UI prefabs, and important prefab variants. Explain the sample and excluded content.
- [ ] Inspect missing scripts, required serialized references, invalid object/file IDs, prefab overrides, variant inheritance, and broken scene dependencies without saving or reserializing assets.
- [ ] Distinguish intentionally optional or runtime-populated references from required references before reporting a defect.
- [ ] Review asset/`.meta` pairing, duplicated identities, unresolved GUID references, merge artifacts, and case-sensitive path assumptions. Unity uses metadata to retain asset identity; never regenerate or repair it during the audit.[^metadata]
- [ ] Resolve reference context before declaring a GUID missing: account for packages, generated content, built-in assets, sub-assets, and unloaded or unavailable dependencies.
- [ ] Inspect serialized-field renames and type changes against repository history and migration support where available; identify affected existing content rather than assuming all renames break data.
- [ ] Check scene loading by name/index against the effective build scene list. Unity versions supporting Build Profiles may use a profile-specific scene override; also inspect custom build-script scene lists.[^profiles]
- [ ] If binary serialization or absent dependencies prevents inspection, record the limitation; do not convert serialization settings to enable the audit.

## TQA-05 — Asset loading and memory ownership

- [ ] Identify the systems actually used: direct references, `Resources`, Addressables, AssetBundles, custom loaders, or a combination. No individual system is mandatory.
- [ ] Follow load, completion, cancellation, release/unload, and retry paths across scene changes and failed requests.
- [ ] If Addressables is active, inspect handle and instance ownership, dependencies, catalog/profile selection, failure paths, and release behavior using documentation for the installed version.[^addressables]
- [ ] Review remote content compatibility, offline behavior, cache/version assumptions, and integrity checks where required. Do not refresh catalogs or download live content without authorized isolation.
- [ ] Inspect `Resources` and direct-reference reachability for unexpectedly included or retained content; use build/memory evidence before claiming an actual size or memory regression.
- [ ] Treat an unreferenced asset as a possible removal candidate until dynamic loading, editor tooling, platform variants, remote content, and licensing/ownership needs are checked.
- [ ] Do not delete candidates or run cleanup tools. Record dependencies, expected benefit, uncertainty, and a future validation plan.

## TQA-06 — New game, saves, loading, and migration

- [ ] Map what persists: progression, inventory, world state, unlocks, settings, bindings, account data, and cloud data. Record actual storage locations and schema versions.
- [ ] Check whether new game/reset/slot deletion affects only the intended data, communicates consequences, and preserves unrelated profiles and settings according to the design.
- [ ] Follow save and load error paths for absent, partial, corrupt, incompatible, read-only, or unavailable storage; inspect recovery and player messaging.
- [ ] Review interrupted writes and durability strategy, duplicate save requests, ordering, checkpoint ownership, and resume behavior. Do not infer reliability from the presence of a save method alone.
- [ ] Verify migration expectations against supported released versions and representative authorized fixtures; preserve originals and record schema/source-build identities.
- [ ] Review default values, changed identifiers, removed content, numerical bounds, timestamps/time zones, and localization-independent formats where relevant.
- [ ] Inspect local/cloud conflict handling, account switching, logout, offline progress, and retry/idempotency only where those features exist.
- [ ] Run destructive or corrupt-save scenarios only against isolated disposable fixtures. If safe isolation is absent, retain a static risk assessment and a blocked validation task.

## TQA-07 — Input and platform interaction

- [ ] Verify only declared device/platform support; select applicable keyboard/mouse, controller, touch, accessibility input, or specialist hardware paths.
- [ ] Review gameplay and UI action maps, focus, cursor lock, selected controls, event-system ownership, simultaneous inputs, and blocked actions during transitions.
- [ ] Check device reconnection, hot swapping, prompts, dead zones, hold/toggle behavior, rebinding and conflicts where supported; distinguish an unavailable feature from a broken promised feature.
- [ ] Review touch safe areas, orientation, multi-touch ownership, interrupted gestures, and platform back/navigation actions when applicable.
- [ ] Inspect platform permissions, text entry/IME, locale-sensitive input, and window/focus behavior against the actual supported matrix.
- [ ] Use [playtest scenarios](playtest-scenarios.md) for runtime evidence; source inspection alone cannot establish responsiveness or ease of use.

## TQA-08 — Tests, compilation, builds, and release configuration

- [ ] Inventory existing Edit Mode, Play Mode, integration, content validation, and platform tests; map critical requirements to coverage and record meaningful gaps.
- [ ] Inspect test setup/teardown, external-service calls, filesystem writes, timing assumptions, and fixtures before execution; tests are executable project code.
- [ ] Record test identity, runner/package version, revision, filters, environment, result counts, failures, skipped tests, and full evidence path for any authorized run.
- [ ] Separate compilation evidence, Editor behavior, build completion, player launch, and device smoke testing. Passing one does not establish the others.
- [ ] Inspect effective target/profile, enabled scenes, defines, backend, architecture, stripping, managed/native plugins, permissions, signing references, and development/release differences.
- [ ] Use the project's existing build procedure in an authorized disposable environment; inspect pre/post-build callbacks and isolate output, credentials, and upload/publish steps.
- [ ] Check failures against the exact build log. Do not automatically upgrade packages, change settings, or introduce a new test framework to complete an audit.
- [ ] Treat unsupported hardware, unavailable licenses/toolchains, missing secrets, and inaccessible CI artifacts as explicit coverage limits rather than product failures.

## TQA-09 — Performance and stability

- [ ] Establish the agreed hardware, resolution, quality, frame-time target, memory budget, load-time expectation, session duration, and representative content before judging performance.
- [ ] Separate **measured behavior** from **suspected cost**. A loop, allocation, draw call, large texture, or scene-wide search is a hypothesis until connected to relevant measurements.
- [ ] For existing captures, verify revision, capture date, build type, device, scene, workload, and profiler configuration before reusing conclusions.
- [ ] For authorized captures, record warm-up, sample interval, route, repetitions, raw trace location, thermal/power state, frame cap/VSync, and profiling overhead.
- [ ] Report frame-time distribution and stalls with CPU/GPU context when available; do not rely only on average FPS or compare unlike capture conditions.
- [ ] Investigate main/render thread work, physics, animation, UI rebuilds, garbage collection, allocation frequency, and loading spikes only where evidence points.
- [ ] Review shaders, overdraw, lights/shadows, render features, batching, LODs, and culling in the actual renderer and target context. Avoid universal optimization prescriptions.
- [ ] Compare memory after equivalent warmed-up states over repeated transitions; distinguish retained caches, pending cleanup, and a demonstrated leak.
- [ ] Record scene/load/save latency, prolonged-session stability, repeated retries, and content extremes relevant to the game's intended use.
- [ ] If the audit has only Editor or static evidence, explicitly limit claims about release builds, target devices, battery use, thermal behavior, and peak performance.

## TQA-10 — Asset, rendering, and audio health

- [ ] Inspect representative textures/sprites, meshes, animation clips, materials, shaders, fonts, audio, video, and import settings against their actual use and platform overrides.
- [ ] Check missing materials/shaders, unsupported renderer features, broken animation bindings, texture/color-space mismatches, sprite slicing, compression artifacts, and incompatible platform plugins where evidenced.
- [ ] Review unexpectedly large/duplicate payloads with dependency or build evidence; resolution, polygon count, and audio size have no universal acceptable maximum.
- [ ] Inspect audio mixer routing, mute/pause behavior, voice limits, looping, spatialization, load mode, and import compression for relevant assets; listen only in an authorized run or supplied recording.
- [ ] Separate audible defects and rendering failures from stylistic preferences. Support art/style consistency observations with representative screenshots and the game's visual intent.
- [ ] Check attribution, licensing records, and source provenance when in scope; absent documentation is uncertainty requiring owner review, not proof of infringement.
- [ ] Identify sample/debug assets or unused systems only as removal candidates until reachability and release dependencies are established.

## TQA-11 — Multiplayer and online systems, when applicable

- [ ] Mark this section `Not applicable` with rationale for games without relevant online features; do not invent networking requirements.
- [ ] Identify networking framework/version, authority model, session ownership, server/client boundaries, persistence, transport, and required player counts.
- [ ] Review join/leave, disconnect/reconnect, scene synchronization, late join, ownership transfers, timeout and retry paths, and host migration only if promised.
- [ ] Inspect client-controlled values, authoritative validation, duplication/replay handling, rate limits, and synchronization of critical game state.
- [ ] Use authorized test peers and isolated services for latency/loss/ordering scenarios; record topology, network conditions, participant roles, and server/client logs.
- [ ] Distinguish a local multi-instance check from real cross-device/network validation; do not infer Internet reliability from one localhost session.

## TQA-12 — Platform, privacy, security, and CI scope

- [ ] Map supported platforms and store/distribution requirements to current authoritative documentation or provided acceptance criteria; date any compliance review and avoid claiming certification.
- [ ] Inspect requested permissions, telemetry/analytics/ads, account data, crash logs, third-party SDKs, consent flows, and data retention/deletion behavior only where used and in scope.
- [ ] Review trust boundaries for remote content, URLs, files, user-generated input, save deserialization, and privileged operations relevant to the game; avoid unsolicited intrusive security testing.
- [ ] If a secret is encountered, record a redacted location and exposure context without reproducing its value, exercising it, or sending it to a scanner/service.
- [ ] Review CI definitions for pinned/reproducible inputs, cache assumptions, toolchain versions, tests, artifacts, secret handling, signing, and automatic publication boundaries.
- [ ] Read existing CI results when available. Do not trigger remote builds, deployments, signing, purchases, account changes, or messages solely to satisfy this checklist.
- [ ] State whether review covered configuration, implementation, observed behavior, external policy verification, or only supplied documents; these support different conclusions.

## TQA-13 — Close the audit without changing the game

- [ ] Re-record original-project staged/unstaged/untracked state and relevant ignored/save/configuration locations; compare with the baseline and disclose limits of the comparison.
- [ ] Preserve other people's changes. Do not reset unexpected changes away; stop the responsible activity, capture evidence, and report attribution as known or uncertain.
- [ ] Record authorized writes confined to the disposable copy and evidence output, plus any unexpected external effects. A disposable copy is not proof of complete isolation.
- [ ] Make every finding traceable to exact files/assets/objects, revision, log timestamps, capture frames, or reproducible scenario IDs; protect personal data and credentials.
- [ ] Deduplicate shared root causes; separate demonstrated defects, risks, design opportunities, missing requirements, and removal candidates.
- [ ] Explain severity through player/release/data impact and confidence through evidence; include the smallest next investigation and a measurable validation target.
- [ ] Include sampled healthy behavior, blocked checks, excluded platforms, unresolved assumptions, and all remaining coverage gaps without calling the entire game tested.
- [ ] Prepare future fix prompts with affected `AUD-###` IDs, scope, constraints, expected behavior, evidence, and acceptance checks. The audit itself makes no remediation changes.

## Versioned Unity references

The references below support particular Unity mechanics, not findings about a project. Select the matching Editor/package documentation before applying them; URLs verified 2026-10-28.

[^profiles]: Unity 6.0, [Build Profiles window reference](https://docs.unity3d.com/6000.0/Documentation/Manual/build-profiles-reference.html), including profile scene overrides.
[^domain-reload]: Unity 6.0, [Enter Play mode with domain reload disabled](https://docs.unity3d.com/6000.0/Documentation/Manual/domain-reloading.html), including static state and event subscriber persistence.
[^metadata]: Unity 6.0, [Asset metadata](https://docs.unity3d.com/6000.0/Documentation/Manual/AssetMetadata.html).
[^addressables]: Addressables 2.7, [Managing Addressable asset memory](https://docs.unity3d.com/Packages/com.unity.addressables@2.7/manual/memory-assets.html); use the installed package's version for ownership and release rules.
