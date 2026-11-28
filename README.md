0.61.3: scoring speed and Remedy load. No change to results.

1) Parallel related reads back to 4 for Pending (your numbers show 6 makes each Remedy reply
   slower and saves little). Keep the back-off code.
2) Q-COMPLETE-10 and Q-COMPLETE-11: parse the Details field against the Exec Summary template
   once per change and share the result between both rules (and any other rule that parses
   it). Results must be identical.
3) Profile the scoring time that is not inside rules (about 17 s of 34 s on 571 changes):
   report the top 5 steps by total time. Fix only if the fix is a pure reuse/caching within
   a single change's scoring (no cross-request cache; shared mode stays live) and results
   stay identical; otherwise report.
4) Tests: identical findings, scores and messages on the contract fixtures and on a recorded
   sample before/after (byte-for-byte on findings JSON). CHANGELOG 0.61.3; pyproject 0.61.3.

Verification: ruff; all non-browser tests incl. test_security; browser -k pending. Re-run the
live profile (Planning In Progress) and report before -> after: total, first scored rows,
scoring time, Remedy request-seconds. Rule set must stay 14e9b07d.
No git, no baseline, no audit. No heredocs, python -c, python - or stdin; do not read the
config files or .env; never delete anything under work/history/; delete temp files in work/.