0.54.1 (baseline NOT updated). Constraints unchanged; no git. Verification: UI level (ruff,
tests for changed modules, browser tests -k review only).

A) CV-15 severity by question importance. Config (change_assessment): core = [2 Deployment
   Strategy, 4 Roll Back Type and ETA, 5 User Restoration ETA, 6 Business Impact,
   7 Attestation]; supporting = [1 Justification, 3 Deployment Type, 8 Deferral Y/N,
   9 Deferral justification]; major_if_total_gaps: 3. CV-15 (one finding): Major if any
   core question is missing/unanswered or total gaps >= 3; otherwise Minor. Lifecycle
   unchanged (advisory once Scheduled). CV-14 unchanged.
   Tests: only Q9 -> Minor; Q1+Q3 -> Minor; Q1+Q3+Q8 -> Major; Q6 alone -> Major;
   Q5 alone -> Major. Measure live (awaiting approval): CV-15 Major -> Minor; verdict
   changes.

B) Change Assessment checklist layout (Technical details on): render the checklist as its
   own full-width line ABOVE the entry's Notes block, outside the label/value grid. The
   "Notes" label and notes text keep their normal layout and full width (same as with
   Technical details off); no stray number line. Line: "Questions 1 ✓ 2 ✓ … 9 ✗" then a
   muted legend "✓ answered · ○ no answer · ✗ missing · – not needed". Tooltips name
   each question (e.g. "5 User Restoration ETA"). Wraps cleanly at narrow widths.
   Browser test: with Technical details on, the notes column width equals the width with
   it off; checklist and legend visible; nothing overlaps.

CHANGELOG 0.54.1; pyproject 0.54.1. Report rule set id, CV-15 counts, files. Then stop.