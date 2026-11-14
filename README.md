READ-ONLY measurement — no rule, config or test changes. Use a temporary helper under work/
and delete it afterwards; no inline Python. Codes and counts only (no change numbers,
no people's names).

Proposed CC-05 logic to MEASURE (do not implement):
- Reference tasks = tasks whose NAME contains "implementation" or "certification"
  (case-insensitive), status not Cancelled/Canceled/Bypassed (Closed DOES count).
- If any reference task lacks scheduled start or end → fall back to the change window.
- If no reference tasks → fall back to the change window.
- Otherwise: Blocker if any reference task strictly overlaps a freeze period (ET, same
  boundary logic as today); else if the change window overlaps a freeze → Advisory; else
  nothing.
- Exception Work Detail types still suppress, as today.

Run over: (a) the live Pending set, (b) the history replay (all 6,461), and report:
1) CC-05 hits today (current logic)
2) under the proposal: Blocker / Advisory / no finding / fallback-to-window — counts
3) how many current Blockers would become Advisory, and how many NEW Blockers would appear
   (should be ~0; list the reason category if any)
4) distinct task NAMES that matched (normalised, with counts) — top 40 — and separately the
   names containing "post-implementation", "pre-implementation", "recertification", or
   similar prefixes
5) distinct task names that did NOT match but look like work (e.g. "deploy", "install",
   "cutover", "release", "migration") — top 20 with counts, so we can see what we'd miss
6) how many changes have reference tasks with missing dates (fallback)

One table for 1–3 and 6, two short lists for 4–5. No git.