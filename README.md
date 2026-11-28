0.61.2: faster Pending list, from your profile. Build: extra, (b), (c), (d). Not (a).

1) Extra: fetch the id list for the search once, then read each page's rows from it; no
   re-reading of earlier pages per support-group batch. Same results, fewer requests.
2) (b) Pipeline: score page N while page N+1 is being read. Pages still read one after
   another; total Remedy requests unchanged.
3) (c) Progressive rows: Pending shows each page's scored rows as soon as that page is
   scored (sorted within what is loaded so far), with a small "Scoring… <n> of <total>"
   note; the final sort and counts apply once all pages are done. Filters and counts must
   be correct at the end and never show a partial count as final.
4) (d) Parallel related reads: IN_FLIGHT 4 -> 6. If Remedy replies slowly or with 429/503,
   back off automatically to 4 for the rest of that request and log the back-off (counts
   only). Keep related_batch_size as is.
5) Report only, no change: the 5 slowest rules by total scoring time over the 571 changes,
   and why each is slow.
6) No change to rules, scores, caching (shared mode stays live), or what any row shows.
7) Tests: same rows, scores and order as before on a 450-change fake Remedy (results
   identical); progressive rows appear before the last page; back-off on a 429; request
   count lower than before. CHANGELOG 0.61.2; pyproject 0.61.2; operations doc.

Verification: ruff; all non-browser tests incl. test_security; browser -k pending.
Re-run the live profile (Planning In Progress) and report before -> after: total time,
time to first scored rows, Remedy requests, back-offs. Rule set must stay 14e9b07d.
No git, no baseline, no audit. No heredocs, python -c, python - or stdin; do not read the
config files or .env; never delete anything under work/history/; delete temp files in work/.

git add -A
git status
git commit -m "0.61.2: faster Pending list" -m "- Change list fetched once; no re-reading of earlier pages per batch
- Next page is read while the current one is scored
- Rows appear as each page is scored, with a progress note
- Parallel related reads 4 -> 6 with automatic back-off on slow replies or 429/503
- Same rows and scores; rule set 14e9b07d unchanged"
git push