0.56.0 (baseline NOT updated). Constraints unchanged: never read/search/print
cr_core/config.py, cr_core/history/config.py or .env; no Remedy writes; no crq login;
no git; any heredoc, python -c or python - is a stop condition (ask instead); scripts in a
file under work/, deleted after; never touch work/history/; chat shows codes and counts
only. Verification: UI level (ruff, tests for changed modules, browser tests -k review
and -k pending only). Live measurement only for item 1.

1) "No impact" rules (Q-VAGUE-01 Major, Q-VAGUE-03 Minor): judge the whole answer under
   the question (up to the next question heading / Notes-template line), not single
   sentences. Reported only when the answer is bare: "No impact" (or variants) with fewer
   than 8 other words in that answer and no reason. Not reported when the same answer
   explains why — including sentences AFTER the phrase (e.g. "unaffected", "remains on",
   "continues to run", "not consumed by", "isolated to", "no production traffic") or any
   explanation of 8+ words. Keep existing reason words; thresholds and words in config.
   Tests: "No impact. The PostgreSQL function change deployed is consumed by DC4
   application instances. Production traffic continues to run on YugabyteDB in DC1 and
   is unaffected by this change." -> not reported; "No impact" / "No impact." alone ->
   reported; "No impact expected" -> reported.
   Measure live (awaiting approval): Q-VAGUE-01/03 before -> after (cleared / kept /
   added — added must be 0); verdict changes. Update the rule's explanation text.

2) Report header tiles: the labels "Blockers", "Major", "Minor" at 14px, semi-bold, the
   column-heading text colour, 4px more space below the number. Numbers and tile colours
   unchanged.

3) New review decision "On hold":
   - Order everywhere: Approve · On hold · Needs work (overlay buttons; Pending row icons
     on hover).
   - Icon ⏸, neutral blue-grey (e.g. text #3A5A80, border #B8C7DA, fill #4A6A90 when
     selected); row left edge and status message in the same colour ("⏸ Recorded for
     CRQ…: On hold · Undo").
   - Same store as today (one decision per change, shared overlay <-> Pending).
   - Filter: All · Not decided · On hold · Decided, each with its count (changes awaiting
     approval only). "Decided" = Approve + Needs work.
   - Keyboard: A, H, N. Copy decisions lists "On hold".

4) Tooltips on the decision buttons (overlay and Pending row), styled like the existing
   row tooltip (not native title), on hover and keyboard focus: not selected "Approve
   (A)" / "Put on hold (H)" / "Needs work (N)"; selected "Approved · click to clear" /
   "On hold · click to clear" / "Needs work · click to clear". aria-labels include the
   change number.

5) Copy decisions: before the table, a heading line "Review decisions · <date> ·
   Approver: <approver filter or All>" and a summary line "Approved n · On hold n · Needs
   work n · Not decided n (m awaiting approval)", counted over the rows being copied. In
   both the plain-text and the rich (table) formats.

Guide (Pending section: On hold, filter), user guide, CHANGELOG 0.56.0, pyproject 0.56.0.
Tests: item 1 cases; On hold record/clear/undo, overlay <-> Pending sync, filter counts,
keyboard H; tooltips on hover and focus; Copy decisions summary counts and order; tile
label size. Report rule set id, item 1 measurement, files and test counts. Then stop.