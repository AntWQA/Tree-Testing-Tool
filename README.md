# Tree Testing Tool

A moderated tree-testing tool for validating the proposed doTERRA storefront navigation structure. Built for in-person research sessions: a moderator and one participant pass a single device back and forth, working through a set of realistic find-it tasks against the proposed information architecture (IA).

## Hosted version

The live, working copy of this tool is a published Claude Artifact:

**[Open the Tree Testing Tool](https://claude.ai/artifact/KCFQGiyaTbSjVxRFWwjqxi?sk=_Ev9oPLEKzZMbTyYbE3KLg)**

This is the version to actually run sessions with. It has a real shared database behind it, so:

- Every task saves to a shared results ledger as the session runs (not just at the end).
- The ledger, the navigation structure, and the task list all sync live across every device that opens the link.
- Results can be exported as CSV, JSON, or Markdown from the Ledger tab.

Accessible and editable by any WQA team member with a Team license — no separate invite needed, just the link above.

## This repo

`wayfinding-trial.html` is the same tool as a single, self-contained HTML file — the source of truth for the code, and a way to run or inspect the tool outside of claude.ai.

Opened directly (double-clicked, or served from a plain local server) it still runs the full moderator/participant flow, but without the Artifact's shared database:

- Results save to that browser's own local storage instead of a shared ledger — not synced across devices, and cleared if browsing data is cleared.
- Export to CSV/JSON/Markdown from the Ledger tab works the same either way, and is the reliable way to get a copy out.

For running actual participant sessions, use the hosted version above. This file is for reviewing, editing, or archiving the code.

### Running locally

No build step or dependencies — it's one HTML file with inline CSS/JS.

```bash
# Just open it
open wayfinding-trial.html

# Or serve it (needed for some browser features, e.g. connecting a data file)
python3 -m http.server 8080
# then visit http://localhost:8080/wayfinding-trial.html
```

## How the tool works

1. **Setup** – the moderator names a participant (each name must be unique in the ledger) and optionally flags it as a practice run or notes whether the participant is internal (doTERRA staff) or external (a customer).
2. **Per task** – the moderator hands the device to the participant, who reads a scenario and navigates the proposed IA to find the answer, then hands back.
3. **Capture** – the moderator records the participant's confidence (1–5) and any notes, with the option to retake the task or end the session early.
4. **Done** – results save to the ledger (or local storage, if running standalone) and the moderator can start the next participant.

The Content tab lets a moderator edit the navigation structure and task list (as JSON), version each change, and configure how many backtracks still count as a "Direct" success. The Ledger tab shows aggregate per-task stats, the full session log with per-task navigation trails, and export options.

## Project context

This tool lives under the broader **Storefront** project folder, which covers other WQA/doTERRA storefront UX work beyond tree testing.
