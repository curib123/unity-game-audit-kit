# Playtest session — [session ID / game]

This template describes a session only after it is run. Keep proposed protocols labeled as such; never convert an AI persona's predicted reaction into a human observation.

## Session identity and permission

| Field | Value |
| --- | --- |
| Execution status | [Protocol only — not run / Partially executed / Executed / Blocked] |
| Date / start–end (UTC) / observer | [values] |
| Participant / observation source | [human participant / agent-operated runtime / source analysis only] |
| Perspective | [actual participant profile with consent / hypothetical AI persona / none] |
| Target repo / original path / baseline | [URL, path, commit, dirty snapshot] |
| Isolated copy and operation authorization | [path, exact permission reference; original stays unchanged] |
| Unity / renderer / build identity / type | [versions, artifact, Development/Release, source association] |
| Platform / OS / hardware / display | [device, CPU/GPU/RAM, resolution, scale, refresh rate] |
| Input / controls / locale / settings | [keyboard/mouse, controller, touch; mappings and relevant settings] |
| Save / account / services | [approved disposable state and endpoints; no secrets] |
| Recording / logs / evidence root | [toolkit paths, capture permissions and provenance] |

If runtime access or a safe isolated environment is unavailable, mark the session `Blocked` or `Protocol only — not run`. A source inspection or imagined walkthrough is not a played session.

## Protocol — planned actions

- Goal and tested question: [specific uncertainty or acceptance criterion].
- Starting state and setup: [scene, save fixture, tutorial state, settings].
- Scenario and success condition: [player task and observable completion].
- Stop condition / time budget: [timeout, error, data/service safety boundary].
- Permitted tooling and runtime operations: [recording, profiler, inputs, reset].

| Step | Planned action / control | Expected signal and source | Evidence to capture |
| --- | --- | --- | --- |
| [1] | [action] | [requirement or hypothesis] | [screenshot/log/timing] |

## Execution log — actual actions only

Use `Not run` for an unexecuted step and leave its result unknown. Do not infer duration, success, frame rate, or reproduction frequency from a planned protocol.

| Time (UTC / elapsed) | Step / exact input | Actual state or outcome | Status | Evidence |
| --- | --- | --- | --- | --- |
| [timestamp / elapsed] | [executed action] | [observed result] | [Pass / Fail / Inconclusive / Blocked / Not run] | [relative path] |

## Observations and interpretation

| Observation ID | Direct observation / exact participant quote | Source | Interpretation or hypothesis | Finding / coverage link |
| --- | --- | --- | --- | --- |
| [OBS-001] | [what happened; quote only if actually said] | [human / runtime capture / AI analysis] | [clearly labeled inference] | [AUD-### / coverage] |

- AI persona assumptions, if used: [experience, goals, constraints; no claim of human validation].
- Contradictory or successful cases: [observed evidence / not checked].
- Audio observations: [actual listening conditions and evidence / not heard].
- Art/layout observations: [actual screen, resolution and state / unobserved variants].
- Performance observations: [measurement tool, build type, sample window / unmeasured].

## Results, limits, and follow-up

- Scenarios actually completed: [list with evidence; none if not run].
- Findings established: [IDs and confidence / none established].
- Coverage: [Checked / Partially checked / Not checked / Blocked / Not applicable; specific boundaries].
- Unexecuted protocol steps and reasons: [list].
- Environment or participant limitations: [effect on generalization].
- Next smallest useful test: [protocol and prerequisites; planned only].
- Isolated-state cleanup actually performed: [approved action and evidence / not performed].
- Original baseline integrity verification: [read-only check and result / not verified].
