Review answers — please fix, then stop.

1) Failed save: keep the Save view dialog OPEN, keep the typed name, and show the red message
   inside the dialog above the buttons (bg #FDE8E7, text #7A1212, border 1px #F3C1BC, radius 8,
   padding 10px 12px, 13px). The status line is not used for this case.

2) Add a browser test: picking view B while view A's load is in flight aborts A, ignores A's
   late answer, and ends with B's filters and rows.

3) test_security.py burst test: first explain in 3–4 lines why it had to change. With the flag
   OFF the two new scripts must not load, so flag-off behaviour must be unchanged. Restore the
   original test for the flag-off case exactly as it was; if the flag-on page needs its own cap,
   add it as a NEW test rather than loosening the existing one. Don't change the server's
   request limit.

4) Icons: no Unicode symbols anywhere in the picker, menu or dialogs (they render differently
   on Mac/Windows and across browsers). Use small inline SVGs, 14px, currentColor:
   - picker grid icon and the picker caret (caret = the same chevron and size the filter chips use)
   - selected tick in the menu (12px check, stroke 2, #0E7C74) in a fixed 14px column so Default
     and every view line up
   - "Save current as…" plus and "Manage views…" gear — same size and weight as each other
   - dialog close ×, Export / Import icons, ⓘ / ⚠ / ✓ in messages and notes

5) Menu spacing: items padding 9px 14px; dividers 1px #EEF1F6 with margin 6px 0 and no extra
   spacer elements; no blank space between the last view and the divider before
   "Save current as…"; "Save current as…" and "Manage views…" directly one after the other.

6) Add this line to .github/copilot-instructions.md in the rules section:
   "Never run Python from the command line with -c or from stdin (python -, python3 -,
   heredocs), even if empty. Use a file under work/ and delete it afterwards, or ask."

Check the picker, menu and both dialogs in the browser at 100% and 110% zoom.
Run only: ruff, the saved-views browser tests, and test_security.py (plus the new test).
Report files changed and pass/fail counts, then stop. No git.