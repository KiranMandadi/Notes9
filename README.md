Pending: Copy Decisions columns and an in-app Clear confirmation. Same standing rules (including Running commands); no git operations unless I ask.

1. Copy Decisions output (both the HTML table and the tab-separated text):
   - Columns: Change | Summary | ORR | Review Decision.
   - Summary: full Remedy summary, not truncated. In the HTML table it wraps within its column. In the text version, replace tabs and line breaks in the summary with single spaces.
   - ORR: the same wording as the table ("4 – Very High"); "—" when missing.
   - Review Decision: "Approved" / "Needs work" (exact on-screen labels).
   - Order: Approved first, then Needs work; within each group ORR highest first ("—" last), then change number.
   - Undecided changes are not included (unchanged). The HTML table keeps today's styling; header row included in both formats.

2. Replace the browser confirm() on "Clear" with a ChangeLens dialog:
   - Centred white card (12 px radius, max-width 440 px) on a dimmed backdrop rgba(11,27,51,0.45); page fonts and colours.
   - Title "Clear all review decisions?" (17 px, 600).
   - Body: "This removes the N decisions recorded in this browser tab. It can't be undone." (N = recorded decisions).
   - If they haven't been copied since the last change: an amber line (#8A4B08) "These decisions haven't been copied yet." with a "Copy Decisions" link that copies without closing the dialog; after copying, the line changes to "Copied N decisions" (#5B6880).
   - Buttons right-aligned: "Cancel" (white, 1 px #CFD7E3 border) and "Clear decisions" (#A61B1B fill, white text). Initial focus on Cancel.
   - Esc and backdrop click cancel. Focus is trapped inside while open and returns to the Clear link on close. role="alertdialog", aria-modal, aria-labelledby/aria-describedby.
   - Build it as a reusable confirm component in the Console code (no new library).
   - No browser confirm()/alert() left anywhere in the Console. The beforeunload leave-page warning stays as is (browsers don't allow styling it).

Tests:
   - unit test for the copy order and text escaping;
   - browser tests for: copied HTML and TSV columns and order (mixed ORR, both decisions, a summary with a tab and a line break); dialog opening on Clear; not-copied line and its Copy link; Cancel, Esc and backdrop keeping decisions; Clear decisions removing them; focus returning to Clear;
   - a check that the code has no confirm( or alert( calls.
Update screenshots; user-guide (Copy Decisions columns, Clear dialog); CHANGELOG (no new version). Run all tests with pytest; report counts.
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: Copy Decisions with Summary and ORR, in-app Clear confirmation"
git push