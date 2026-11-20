0.57.0 change: one restriction pill per change on the Window line, and the Freeze lock fix.

1) One pill. On the Window line show Today/Tomorrow (unchanged), then at most ONE
   restriction pill, chosen by precedence:
     Freeze > Freeze · exception > Critical awareness > High awareness
   Colours and icons unchanged (Freeze: lock; Critical/High: triangle; exception: text only).
2) Tooltip on that pill lists every overlapping period, grouped in this order:
   - restricted periods: "Name · Change Restriction · <Ddd d Mon HH:MM> – <Ddd d Mon HH:MM> ET",
     then "Blocked unless an approved freeze exception is recorded" (Freeze) or
     "Exception recorded in Work Detail (<type found>)" (Freeze · exception);
   - awareness periods: "Name · Critical awareness · …" / "Name · High awareness · …",
     critical first, then by start.
   Same styled tooltip as today; one line per entry.
3) Lock fix: in tagIcon (pending.js) the Freeze pill must render the lock
   (rect x=5 y=11 width=14 height=9 rx=2 + path M8 11V8a4 4 0 0 1 8 0v3); awareness pills
   render the triangle. Check the phone card copy too.
4) Review At a glance and Calendar unchanged (they keep showing freeze and awareness
   separately). No change to logic, rules, scores or calendar.yaml.
5) Tests: one restriction pill per row in each combination (freeze + critical, freeze +
   high, exception + critical, critical + high, awareness only); tooltip lists all
   overlapping periods in the order above; Freeze pill contains the lock shape (rect + arc),
   awareness pill the triangle path. Docs: user-guide sentence on the precedence. CHANGELOG
   line under 0.57.0.
Verification: ruff; tests for the changed modules; browser -k pending and -k review.
Ground rules as before; any heredoc, python -c or python - is a stop condition.