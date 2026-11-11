Review Decision timing. Same standing rules; no git operations unless I ask. UI only; rule set id unchanged — confirm it.
1. Show the Review Decision group (accent bar, title, Approve / Needs work) as soon as the quality score and the findings ("Issues to fix") have rendered. Do not wait for overlaps, history comparison or any other section that loads after.
2. Still hidden while "Reading … from Remedy…" is showing and if the report fails to load.
3. Sections still loading (Overlapping changes, At a glance "Overlaps" line, past-change comparison) show their own small placeholder, e.g. "Checking overlapping changes…", and fill in when ready.
4. ‹ › stepping: the "waiting for previous report" behaviour applies only until the score and findings are shown, not until overlaps finish.
Tests: with overlaps mocked slow (e.g. 5 s), Review Decision is visible as soon as score + findings render and before overlaps arrive; still hidden while reading and on failure; overlap placeholder shown then replaced. Update screenshots; CHANGELOG (no new version). Run the browser tests with pytest; report counts.
No branches, tags or commits.


git status
git add -A
git commit -m "Remedy link: shorter label, text link on Pending rows"
git push