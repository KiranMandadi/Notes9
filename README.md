Console crash fix + Review search card polish. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. Rule set id unchanged — confirm it at the end. Data from Remedy stays live; history.db reuse is local data only.

PART A — /api/status pile-up (do first)
The local Console aborted (CPython fatal error take_gil) holding 100 request threads, all /api/status, each running "crq history status", which reads all 6,461 past changes from history.db on every call.
1. Diagnose and report first:
   - every caller of /api/status (page load, polling, overlay frame, warm-up frame, retries) and how often each fires per open page;
   - what produced 100 concurrent calls;
   - reproduce with 3 browser tabs on Pending plus the overlay open for 10 minutes, and report the peak concurrent /api/status calls before the fix.
2. Fix:
   a. /api/status must not reload history per call. Answer from the in-memory history already used for reports (reloaded only when history.db's modified time or size changes), or from a status summary computed once per history.db version.
   b. Single-flight: concurrent /api/status requests share one in-progress computation; never more than one history read at a time.
   c. Embedded pages (overlay frame, warm-up frame) make no /api/status call; only the top-level page does.
   d. Polling: no faster than once per 60 s, paused while the tab is hidden, never overlapping (next poll waits for the previous one).
   e. Server safety: cap request worker threads at a sensible limit and give /api/status a short timeout; a slow status never blocks page, static or report requests.
3. Re-run the same 10-minute reproduction and report peak concurrent calls, /api/status median time and the first report load time.

PART B — Review search card
4. Remove the card's footer line "Read live from Remedy · nothing in Remedy is changed" (the points row below already says it). Spacing: 18 px between status line and button, 4 px more above the button; the card may shrink.
5. Input validation (hard limits, no error states):
   - Accept digits only; ignore any other typed character.
   - Maximum 12 digits; further typing is ignored.
   - Paste: strip a leading "CRQ" (any case), spaces and other non-digits, then keep at most 12 digits.
   - Any 1–12 digits is valid and left-padded with zeros: status "✓ CRQ<12 digits>" (#1E6B45), button teal and enabled, Enter submits. Empty: "You can paste the whole number, including CRQ." (#5B6880), button disabled.
   - Remove the "Numbers only", "Up to 12 digits" and "CRQ followed by 12 digits" messages and the red border state; restore padding of short numbers (e.g. 2484053 → CRQ000002484053).
Keep unchanged: ChangeLens logo, navigation, headline/eyebrow/subtext, the three points row with its icons, the footer Technical details toggle, and the favicon.

Tests:
- Part A: concurrent /api/status calls trigger one history read; embedded pages make no status call; polling stops while hidden and never overlaps; status refreshes after history.db changes; static and report requests are served while status is slow.
- Part B: letters ignored; 13th digit ignored; paste "CRQ000002484053", "crq 2484053" and "CRQ 0000 0248 4053" normalised; 7 digits valid and padded; Enter submits; empty disables; footer line absent.
Run python scripts/check.py --browser --audit (0 mismatches) and all tests with pytest; report counts and the rule set id. Update screenshots, docs/operations.md and CHANGELOG (no new version).
No branches, tags or commits.


