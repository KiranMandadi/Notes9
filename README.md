0.57.0 fix: remove the local-time tooltip.
The Window times on Pending carry a native browser tooltip converting them to the viewer's
local time ("= <day>, <time> GMT+5:30 (your time)"). It is not needed: remove it. Times
stay shown in ET as today. Remove it wherever the Console shows it (Pending, Review, overlay,
Calendar), plus any helper code, docs and tests that exist only for it. Report where it was
removed.
Result: hovering a Today/Tomorrow, Freeze, Freeze · exception or awareness pill shows only
its styled tooltip, with no native tooltip on top.
Add a browser test: hovering an awareness pill shows its styled tooltip and no element on
the Window line carries a native title. No other change.
Verification: ruff; tests for the changed modules; browser -k pending and -k review.
Ground rules as before; any heredoc, python -c or python - is a stop condition.