# Audit reports

No target game has been supplied or audited yet. This folder contains no game findings.

For a real audit, create a separate folder such as `<game-slug>/<YYYY-MM-DD>-<short-sha>/`. Use the actual date and baseline commit; use `unknown-ref` and explain why if there is no commit. Keep the folder outside the original target game's checkout.

Suggested outputs:

- `audit-report.md`: summary, highest-impact findings, strengths, limitations, and next steps.
- `findings.md`: complete evidence-backed records with stable `AUD-001` IDs.
- `coverage.md`: actual checks and results, blocked checks, and sampling limits.
- `implementation-prompts.md`: future implementation or investigation tasks.
- `playtest-log.md`: executed session evidence or clearly labeled unexecuted protocols.
- `removal-candidates.md`: dependency and validation review for proposed removals.
- `art-ui-redesign.md`, when relevant: screen/art-system strategies, design proposals, alternatives, selection state, and acceptance criteria using the [redesign brief](../templates/art-ui-redesign.md).

Use the [templates](../templates/audit-report.md). Create only the files relevant to the audit and make omissions clear in the report. Preserve previous runs unless an update was requested.

This repository is public. Writing a local report does not authorize committing or publishing it. Keep original proprietary captures, personal data, and unredacted logs in an appropriate private evidence location; cite sanitized identifiers in shareable reports.
