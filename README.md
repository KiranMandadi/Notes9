0.53.0 additions before commit (baseline still NOT updated).
Constraints unchanged: never read/search/print cr_core/config.py, cr_core/history/config.py
or .env; no Remedy writes; no crq login; no git; no inline Python — scripts in a file under
work/, deleted after; do NOT run --update-baseline; never touch work/history/; no answer or
attestation text in findings, logs or chat; chat shows codes and counts only.

A) Evidence link
   - CV-15 and CV-17 show "Searched: Work detail › Change Assessment" as a link. Click:
     open Full change details, expand Work detail, expand the latest Change Assessment
     entry, scroll to it, brief highlight (same style as the Notes highlight).
   - CV-14: link "Searched: Work detail" opens the Work detail panel.
   - Internal entry: the link still lands on it ("Internal: text not shown").

B) How to fix (neutral, no "your"; names the questions itself, never "above"; no mention
   of template versions or formats):
   - missing: "Add question 5 (User Restoration ETA) and question 8 (Can this be
     deferred 3 to 5 days? Y/N) to the Change Assessment Work Detail, and answer each."
   - unanswered: "Answer question 2 (Deployment Strategy)."  (combine both when needed)
   - Q8 = N without Q9: "Explain in question 9 why the change cannot be deferred."
   - CV-14: "Add a Change Assessment Work Detail with questions 1–9."

C) Bold headings
   - In Change Assessment entries, render each identified question heading (as written,
     e.g. "4.Roll Back ETA:") bold on its own line, unbroken; answer text below, normal.
   - Notes formatter everywhere: a label is the whole phrase from line start (after an
     optional list number) up to the colon, max 6 words; never split a phrase to bold
     only the last word. Times like "05:03" and URLs are not labels.

D) Checklist line (Technical details only): at the top of the latest Change Assessment
   entry, "1 ✓ 2 ✓ 3 ✓ 4 ✓ 5 ✗ 6 ✓ 7 ✓ 8 ✗ 9 –" (✗ missing, ○ unanswered, – not needed);
   tooltip names each question. Muted, one line.

TESTS: link opens and highlights the entry (CV-15, CV-17) and opens Work detail (CV-14);
fix text for missing / unanswered / Q9 / CV-14, with no format wording; heading
"1.Deployment Strategy:" bold as one unit; Notes formatting tests stay green plus a
regression for multi-word labels; checklist shown only with Technical details. Browser
tests for A, C and D. Existing tests stay green; do not weaken any.
DOCS: CHANGELOG 0.53.0 (add to the entry), user-guide if it describes the fix text.
VERIFY: ruff, full suite, check.py --browser --audit (report the new rule set id).
Then stop.