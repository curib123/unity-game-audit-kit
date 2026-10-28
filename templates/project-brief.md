# Project brief — [game name]

This is an intake template, not evidence that an audit or playtest occurred. Use `Unknown` for missing information; continue the checks that available evidence supports.

## Project and baseline

| Field | Value / evidence |
| --- | --- |
| Game name / slug | [name] / [safe directory slug] |
| Target repository URL and original local path | [URL] / [absolute path] |
| Branch / full commit SHA | [branch] / [SHA or unavailable] |
| Dirty state | [clean / dirty / unknown; tracked, untracked, ignored/generated considerations] |
| Baseline evidence | [read-only status capture, source snapshot, timestamp] |
| Unity version | [exact version; ProjectVersion.txt or other source] |
| Render pipeline / version | [Built-in / URP / HDRP / custom / unknown; evidence] |
| Target platforms / supported devices | [platforms, OS versions, minimum hardware; source] |
| Current build | [artifact, build ID, commit association, Development/Release/other, backend] |
| Audit date / auditor | [YYYY-MM-DD UTC] / [name or agent] |
| Product owner / decision source | [name or document; do not contact without authorization] |

## Product intent

- Audience and player needs: [known audience, experience level, access needs].
- Genre, core loop, session length, game modes: [confirmed intent / unknown].
- Current milestone and release constraints: [prototype, vertical slice, production, live; source].
- Intended experience and differentiators: [requirements or owner statements].
- Art direction, UI/layout rules, audio direction, tone: [reference documents and approved exceptions].
- Monetization, online services, persistence, localization: [known constraints / unknown].
- Success criteria: [observable goals and source; distinguish proposals from requirements].

## Audit scope and permissions

| Scope item | In scope? / authorization / limits |
| --- | --- |
| Source, scenes, prefabs, settings, assets, existing logs | [read-only paths and exclusions] |
| Gameplay, progression, onboarding, navigation, feedback | [flows and intended depth] |
| UX, accessibility, layout, input, localization | [platforms, aspect ratios, input methods] |
| Art, animation, visual consistency, audio, style | [reference quality bar and constraints] |
| Stability, performance, builds, saves, services | [allowed evidence and tests] |
| Removal candidates | [review only; no deletion authorization implied] |
| Isolated copy creation and Unity import/open | [explicit authorization, destination, permitted tooling] |
| Isolated builds and runtime sessions | [explicit authorization, commands/flows, devices] |
| Services, network, test accounts, save data | [allowed endpoints/accounts; default no live writes] |
| Out of scope | [paths, platforms, flows, sensitive data] |

The original game stays unchanged. Unity imports, builds, tests, play sessions, caches, and saves must use an authorized isolated copy and approved output/data locations. If that cannot be arranged, record runtime coverage as `Blocked` or `Not checked` and continue read-only work.

## Available evidence and environment

| Evidence / access | Location or reference | Verified availability | Restrictions |
| --- | --- | --- | --- |
| Requirements / design references | [reference] | [verified / unavailable / unknown] | [limits] |
| Source / assets / existing build | [reference] | [status] | [limits] |
| Screenshots / recordings / logs | [reference] | [status] | [provenance and privacy] |
| Hardware / OS / graphics API | [details] | [status] | [limits] |
| Display / resolution / scale / input | [details] | [status] | [limits] |
| Test accounts / saves / service fixtures | [reference, no secrets] | [status] | [allowed use] |

## Questions, assumptions, and blockers

| Item | Known evidence | Working assumption or unanswered question | Effect on coverage |
| --- | --- | --- | --- |
| [item] | [source / none] | [explicit assumption / question] | [affected checks] |

Missing access, absent requirements, and unperformed tests are coverage gaps. A `Missing requirement` finding needs evidence of a required behavior that is absent; it is not a label for missing audit information.

## Deliverables

- Output root: `[toolkit-root]/reports/[game-slug]/[YYYY-MM-DD]-[short-sha]/`, outside the target game. Use `unknown` for the SHA suffix only when unavailable and explain why.
- Files as needed: `audit-report.md`, `findings.md`, `coverage.md`, `implementation-prompts.md`, `playtest-log.md`, `removal-candidates.md`, and evidence files.
- Expected handoff: [decision maker, format, scope and date].
- Fixes and removals require later explicit authorization for specific finding IDs and scope.
