# Reproducible playtest scenarios

This is a test design library, not a record of completed playtests. Select scenarios that match the game's requirements, supported platforms, and available evidence. Replace every generic action, checkpoint, route, and expected behavior with project-specific details before execution.

## Before running anything

- Apply the [technical QA operating boundary](technical-qa.md#operating-boundary). Opening Unity, tests, Play Mode, builds, and player launches may write project files, preferences, saves, logs, or remote data.
- Execute only when already authorized in a disposable project/build environment with isolated saves, accounts, preferences, and services. Confirm the actual data paths; a copied project may still use the original game's save location.
- Record the original staged, unstaged, untracked, relevant ignored, and external-data baseline. Preserve existing Console messages; never clear logs or reset other work to simplify a test.
- Without safe execution access, use static inspection or supplied recordings/logs. Mark runtime scenarios `Blocked` or `Not checked`; a walkthrough of code is not an executed playtest.
- A human participant's consented actions and observations, an actual tool-operated run, a supplied recording, and an AI's hypothetical player perspective are different evidence. Label which occurred; never present a simulated persona as a real participant.
- Derive expected behavior from agreed requirements or documented game intent. When neither resolves a design choice, record the uncertainty or a `Design opportunity`, not an invented defect.

## Run record and evidence convention

Create one record per scenario and matrix cell, retaining failed attempts as well as successful repetitions. Evidence paths below are relative to this kit's `reports/<game-slug>/<YYYY-MM-DD>-<short-sha>/`, or another agreed output location outside the original game project; replace placeholders with real existing files.

| Field | Record before or during each run |
| --- | --- |
| Identity | Scenario ID, run ID, date/time and time zone, operator, actual participation/evidence method |
| Build | Revision/snapshot, build identifier, Unity version, platform, build/profile configuration, Editor or standalone player |
| Environment | OS/device, input device, display/aspect ratio, quality, locale, audio output, relevant accessibility settings |
| State | Start scene/checkpoint, isolated account/slot, save/schema fixture, progression, seed if supported, service/network state |
| Procedure | Exact input sequence, timing, route, repetition count, acceptance-criterion source |
| Result | Expected and actual observations, frequency, time to failure/recovery, log/video timestamps, affected scope |
| Coverage | `Checked`, `Partially checked`, `Not checked`, `Blocked`, or `Not applicable`; explain limits |
| Finding | Linked `AUD-###` IDs, if any; `Checked` does not imply the expectation was met |

Use `evidence/playtests/PT-001/<run-id>/run.md` for the run record and add only captured evidence such as `video.mp4`, `screenshots/`, `player.log`, `trace.data`, or `fixture-manifest.md`. Filenames are examples, not claims that files exist. Keep original captures private. Sanitize identifiers and logs, exclude secrets and private player data, and publish evidence only when explicitly authorized.

## Representative coverage matrix

Select high-risk combinations and record omitted combinations. Do not claim every cross-product was tested because one example worked. Use the same named route and starting state when making comparisons.

| Dimension | Representative choices, only if supported |
| --- | --- |
| Hardware/platform | Primary target, minimum target, another important target; exact devices/builds recorded |
| Input | Keyboard/mouse; supported controller family; supported touch device; relevant assistive input |
| Display | Minimum supported size, common aspect ratio, widest/narrowest supported ratio, safe-area device |
| Progression | Fresh profile, mid-game/checkpoint, late-game/content-heavy state, supported migrated save |
| Session | Cold launch, warm retry, scene return, suspension/resume, representative long session |
| Locale/content | Default and longest supported strings, supported non-Latin/RTL locale, largest relevant content state |
| Connectivity | Normal; supported offline mode; authorized simulated timeout/recovery; relevant multiplayer topology |
| Settings | Defaults and meaningful supported extremes for graphics, audio, controls, and accessibility |

Prioritize the first playable loop, progression integrity, required input, navigation, recovery, and release-blocking paths. Add genre-specific routes using the same record format: for example, puzzle undo, combat respawn, vehicle recovery, or strategy turn resolution, only when relevant.

## PT-001 — Fresh launch and first meaningful action

- **Preconditions:** Isolated fresh profile; agreed boot entry point; supported device; first-run expectations documented.
- **Actions:** Cold launch, record every screen, follow the presented instructions, and attempt the first intended meaningful action without undocumented setup.
- **Expected:** Required disclosures/onboarding are usable; the goal and next action can be identified; the player reaches the intended start state without a blocker. Record observed hesitation rather than inventing a universal time limit.
- **Evidence:** `evidence/playtests/PT-001/<run-id>/`: boot-to-action recording, time markers, initial state, logs, actual participant notes if collected.

## PT-002 — Complete one core loop

- **Preconditions:** Named starting checkpoint and representative objective; known success/progression rule and reward expectations.
- **Actions:** Perform the main verb, respond to feedback, complete the objective, collect the expected outcome, and begin the next loop using a fixed route.
- **Expected:** Rules and feedback match the intended action; objective/reward state updates once; the player can continue. Enjoyment and pacing judgments remain attributed observations or design hypotheses.
- **Evidence:** `evidence/playtests/PT-002/<run-id>/`: route, before/after state, recording with action/outcome timestamps, relevant logs.

## PT-003 — Failure, retry, and completion boundaries

- **Preconditions:** Repeatable fail and win/end states appropriate to the game; disposable progression; documented retry/reset rules.
- **Actions:** Trigger the selected failure, retry twice, then complete the objective; revisit the completion screen or next stage as the flow permits.
- **Expected:** Failure and success are clear; retry restores the intended state; rewards, penalties, listeners, and scene transitions are not duplicated; the next valid action is available.
- **Evidence:** `evidence/playtests/PT-003/<run-id>/`: trigger steps, state comparison for each attempt, transition recording and logs.

## PT-004 — Save, quit, and resume

- **Preconditions:** Supported save route; isolated slot; named checkpoint and state inventory including settings expected to persist.
- **Actions:** Change the selected state, save through the normal flow, quit normally, cold launch, and load/continue; repeat once at another representative checkpoint.
- **Expected:** Persisted and intentionally reset values match the save contract; location/progression are coherent; loading does not duplicate grants or lose confirmed progress.
- **Evidence:** `evidence/playtests/PT-004/<run-id>/`: state inventory, save/schema identity, save and load timestamps, screenshots/logs; sanitized fixtures only if allowed.

## PT-005 — New game, reset, and profile boundaries

- **Preconditions:** Disposable existing progression; supported new-game/reset/slot actions; another isolated slot if supported; documented deletion scope.
- **Actions:** Start each relevant destructive flow, cancel once, then confirm against disposable data; inspect the new run and any unrelated supported slot/settings.
- **Expected:** Consequences and selection are clear; cancellation preserves state; confirmation resets exactly the intended data; unrelated profiles/settings follow the design contract.
- **Evidence:** `evidence/playtests/PT-005/<run-id>/`: confirmation UI, before/after state and fixture identities, logs; no real player saves.

## PT-006 — Supported save migration

- **Preconditions:** An approved copy of a supported old-version fixture, its source build/schema, and defined migration expectations; no live cloud account.
- **Actions:** Load the fixture in the reviewed build, inspect key progression/settings/content references, save normally, then relaunch and reload the migrated copy.
- **Expected:** Supported values survive or change according to the migration specification; repeated loading does not reapply grants; unsupported versions receive the agreed handling.
- **Evidence:** `evidence/playtests/PT-006/<run-id>/`: fixture manifest, migration logs, before/after state inventory; original fixture preserved.

## PT-007 — Missing, corrupt, or incompatible save

- **Preconditions:** Authorized disposable fixtures for each relevant failure, isolated storage, and documented recovery behavior; static review only if fixtures cannot be isolated.
- **Actions:** Launch/load each selected fixture separately; follow offered retry, recovery, cancellation, or new-game options without overwriting the preserved fixture.
- **Expected:** The game follows its recovery policy, explains the problem, and avoids silently replacing recoverable progress. Record unspecified recovery behavior as an open design question.
- **Evidence:** `evidence/playtests/PT-007/<run-id>/`: fixture identity and fault description, error UI, recovery sequence, logs and resulting test state.

## PT-008 — Interrupted writes and unavailable storage

- **Preconditions:** Explicitly authorized fault setup confined to disposable storage/processes; known interruption point or existing fault-injection support; no full-disk or permission changes on a real user environment.
- **Actions:** Use the approved interruption/storage-failure method during a representative save, restart in the isolated environment, and attempt the documented recovery.
- **Expected:** Previously committed data remains recoverable according to the save contract; failure is surfaced; retry does not duplicate progression. If the interruption point is uncertain, limit the conclusion.
- **Evidence:** `evidence/playtests/PT-008/<run-id>/`: fault method/timing, storage state, recovery trace, relevant logs and preserved test fixtures.

## PT-009 — Scene and content transition repetition

- **Preconditions:** Named menu/gameplay/secondary-scene route, expected persistent systems, fixed iteration count, existing memory/log observation method.
- **Actions:** Traverse the route repeatedly, including a permitted back/cancel during loading; inspect player state, UI ownership, audio, and loaded content after each transition.
- **Expected:** The intended state and controls return; content and persistent systems do not duplicate; cancellation and failed loads follow the documented behavior.
- **Evidence:** `evidence/playtests/PT-009/<run-id>/`: route and iteration log, recordings, errors, equivalent-state memory observations if actually captured.

## PT-010 — Pause, focus loss, and suspension

- **Preconditions:** Supported platform lifecycle actions and expected pause policy, including any intentional online continuation; isolated active session.
- **Actions:** Pause/resume, change focus, and use supported suspend/resume paths at idle and during one critical transition; record exact sequence and duration.
- **Expected:** Time, input, audio, timers, cursor/focus, and network state behave according to policy; returning does not accept stale inputs or strand the player.
- **Evidence:** `evidence/playtests/PT-010/<run-id>/`: lifecycle sequence, before/after state, synchronized video/audio and logs where available.

## PT-011 — Keyboard and mouse path

- **Preconditions:** Keyboard/mouse is supported; named gameplay and menu route; default or explicitly supported custom bindings.
- **Actions:** Complete the route, navigate/back out of nested menus, enter text where relevant, and exercise rebinding/conflicts only if supported.
- **Expected:** Required actions and focus are reachable; prompts match inputs; typing does not unintentionally trigger gameplay; binding changes follow documented behavior.
- **Evidence:** `evidence/playtests/PT-011/<run-id>/`: device/layout, bindings, navigation sequence, screenshots/video and observed failures.

## PT-012 — Controller, reconnection, and supported switching

- **Preconditions:** Supported controller model and connection method; named route; expected disconnect/pause and device-switch policy.
- **Actions:** Complete the route, navigate nested menus, reconnect during a safe point, and switch devices only if the game supports that flow.
- **Expected:** Focus remains visible/recoverable; controls and glyphs match; duplicate actions and inaccessible mouse-only dependencies do not block the supported route.
- **Evidence:** `evidence/playtests/PT-012/<run-id>/`: device/connection, exact reconnect point, focus/glyph recording, logs.

## PT-013 — Touch and mobile interruption

- **Preconditions:** Touch target supported; actual device or clearly labeled emulator; supported orientation and platform navigation behavior.
- **Actions:** Run the core route with taps/drags/holds as applicable, test relevant simultaneous touches, interrupt a gesture, and exercise supported rotation/back navigation.
- **Expected:** The intended gesture and target receive input; controls stay usable within safe areas; interrupted gestures recover without stuck actions or unintended purchases.
- **Evidence:** `evidence/playtests/PT-013/<run-id>/`: device/safe-area/orientation, touch sequence recording, input symptoms and logs.

## PT-014 — UI layout, navigation, and localization

- **Preconditions:** Named essential screens; selected supported resolutions/aspect ratios/locales; long but valid content fixtures.
- **Actions:** Open each screen, traverse focus order, show representative tooltips/modals/errors, and test the selected display/locale combinations using existing supported settings.
- **Expected:** Essential content/actions remain visible, legible, reachable, and ordered; text does not obscure meaning; modal dismissal and return focus work as intended.
- **Evidence:** `evidence/playtests/PT-014/<run-id>/`: screen matrix, exact size/locale/content, annotated screenshots and focus-path recording.

## PT-015 — Settings, defaults, and persistence

- **Preconditions:** Existing options and documented apply/cancel/reset behavior; disposable preferences; selected meaningful supported extremes.
- **Actions:** Change each selected setting, apply/cancel where offered, leave and return, restart, then exercise reset-to-default against the isolated preferences.
- **Expected:** Value, preview, actual effect, and persistence agree with the UI contract; rejected settings recover; reset scope is clear and consistent.
- **Evidence:** `evidence/playtests/PT-015/<run-id>/`: settings matrix, before/after values, visible/audible effects, restart comparison and logs.

## PT-016 — Accessibility and alternate perception/control

- **Preconditions:** Agreed audience/requirements and available accessibility options; selected tasks involving text, color, sound, timing, and motor input.
- **Actions:** Attempt the tasks using relevant supported alternatives, text scales, reduced motion, captions, hold/toggle choices, or assistive input; record obstacles and workarounds.
- **Expected:** Agreed accessibility requirements are met; essential information is available through required channels. Unspecified improvements are `Design opportunity` candidates, with their affected players explained.
- **Evidence:** `evidence/playtests/PT-016/<run-id>/`: settings, task route, screenshots/captions, attributed participant observations; simulations do not establish disabled-user usability.

## PT-017 — Audio feedback and mix transitions

- **Preconditions:** Known output device/volume and audio settings; representative quiet, intense, menu, dialogue, and transition states where present.
- **Actions:** Run those states, pause/resume, adjust supported buses/mute, retrigger representative sounds, and change scenes while listening or reviewing an actual recording.
- **Expected:** Intended cues are audible and synchronized; music/loops transition as designed; mute and pause behave consistently; clipping, missing cues, and masking are evidenced.
- **Evidence:** `evidence/playtests/PT-017/<run-id>/`: audio/video capture, timestamps, output/settings, repeated cue sequence; disclose capture-chain limitations.

## PT-018 — Invalid order, rapid repetition, and boundaries

- **Preconditions:** Selected critical controls and valid input/content limits; fixed repetition counts; non-production data and spending disabled.
- **Actions:** Cancel/reopen a flow, press an action repeatedly, submit boundary/invalid text where supported, and attempt a known out-of-order action through the normal interface.
- **Expected:** State remains coherent; unavailable actions explain their status; submissions/rewards/transitions do not duplicate; recoverable errors retain appropriate input.
- **Evidence:** `evidence/playtests/PT-018/<run-id>/`: exact sequence/count/input, timestamps, state before/after, UI and logs; avoid uncontrolled stress or intrusive attacks.

## PT-019 — Offline mode, download failure, and recovery

- **Preconditions:** Relevant online/content-delivery feature; isolated authorized service or approved network simulation; documented offline/retry contract.
- **Actions:** Trigger a representative request, apply the selected timeout/disconnect, cancel or retry as offered, restore service, and repeat the affected action.
- **Expected:** Waiting/error/recovery are understandable; retries preserve intended state and do not duplicate operations; supported offline behavior matches the contract.
- **Evidence:** `evidence/playtests/PT-019/<run-id>/`: service/network conditions, request/response timing without secrets, player logs, recovery recording.

## PT-020 — Representative performance and endurance

- **Preconditions:** Agreed device/build/quality budgets, named route, warm-up, capture method, repetitions, and session duration; execution/profiling already authorized.
- **Actions:** Complete the fixed route, include the selected content-heavy state and repeated transition, then maintain the agreed session duration with equivalent-state captures.
- **Expected:** Compare measured frame times, stalls, memory, loading, and stability with agreed budgets; report missing budgets or instrumentation instead of inventing pass thresholds.
- **Evidence:** `evidence/playtests/PT-020/<run-id>/`: raw traces, route/timing, sample conditions, distribution summaries, errors; distinguish suspected cost, measured regression, and target-device limits.

## PT-021 — Multiplayer session lifecycle

- **Preconditions:** Multiplayer exists; approved test accounts/peers/services; supported topology/player count; documented authority and recovery expectations.
- **Actions:** Join, play the same objective, leave/disconnect one peer, rejoin if supported, and test late join or host migration only if part of the design.
- **Expected:** Session/progression ownership remains valid; state converges within the agreed behavior; unsupported recovery is explained rather than assumed to exist.
- **Evidence:** `evidence/playtests/PT-021/<run-id>/`: roles/topology, synchronized peer/server logs and recordings, network conditions and exact timing; localhost coverage labeled.

## PT-022 — Permissions, account boundaries, and service choices

- **Preconditions:** Relevant existing permission/account/consent flows, current agreed acceptance criteria, authorized isolated accounts; real purchases and production changes excluded.
- **Actions:** Deny/defer then grant the selected permission where supported; sign out or switch test accounts as applicable; exercise provided privacy/service choices.
- **Expected:** The game communicates resulting limits and follows the agreed data/account behavior; unavailable optional services do not unexpectedly expose another test account's state.
- **Evidence:** `evidence/playtests/PT-022/<run-id>/`: redacted UI/flow recording, test-account labels, authorized observations/logs; no claim of legal compliance from this scenario alone.

## PT-023 — Repeated Editor sessions, conditional

- **Preconditions:** Domain reload is already disabled in the project's actual workflow; authorized disposable Editor copy; isolated data; current scene reload setting recorded.
- **Actions:** Enter/exit Play Mode three times without changing reload settings, repeat one named action each run, and compare counters/listeners/state; compare a fresh player run only if separately available and authorized.
- **Expected:** Each Editor session begins and ends according to the intended workflow; duplicate callbacks or stale state are documented. Do not extrapolate an Editor-only failure to player builds.
- **Evidence:** `evidence/playtests/PT-023/<run-id>/`: reload settings, per-session observations, retained Console/log timestamps; see the versioned reference in technical QA.

## After every session

- Record actual actions, deviations, incomplete steps, raw evidence, and coverage before interpretation. If a procedure was interrupted, do not mark the whole matrix cell `Checked`.
- Attempt a bounded, safe reproduction when useful; record failures/attempts and the changed conditions. Do not keep running once sufficient evidence exists or risk rises.
- Create or link `AUD-###` findings using the shared Types, Confidence, and Severity. Preserve distinctions between what happened, its suspected cause, and a proposed fix.
- Record positive observations only for the checked build, route, device, and conditions. One successful run does not establish general reliability or player satisfaction.
- Compare the original-project final staged/unstaged/untracked baseline and relevant ignored/external-data observations; disclose unexpected changes without resetting them.
- Keep authorized disposable-copy writes and evidence artifacts separate from the original; record isolation limitations, remaining gaps, and future validation needs.
- Deliver reproducible findings and future fix prompts. Do not apply fixes, alter assets, publish builds, or manufacture participant quotes to close the audit.
