0.56.0 polish (UI only). UI level (browser tests -k pending only).
1) Copy decisions: remove "Not decided n" from the summary line. It becomes
   "Approved n · On hold n · Needs work n" (plain-text and rich formats).
2) Pending row hover controls: apply the same rule as the decision icons to the copy icon
   and the "Remedy ↗" link (and anything else shown only on row hover): visible on hover
   or keyboard focus (:focus-visible / :has(:focus-visible)), hidden when the pointer
   leaves after a mouse click. Opening Remedy in a new tab must not leave the row's
   controls showing.
3) Tooltips on the CRQ line use the same styled tooltip as the decision icons (immediate,
   not the native title): copy icon "Copy", then "Copied" for ~1.5 s after a click;
   Remedy link "Open in Remedy". Remove the native title tooltips there; keep aria-labels
   with the change number (e.g. "Copy CRQ000002488429").
Tests: summary line without "Not decided"; click copy and Remedy on row 1, move pointer
to row 2 -> row 1 controls hidden; keyboard focus still shows them; copy tooltip "Copy"
then "Copied"; no native title on these controls. Then stop.