0.64.0 fix: CV-19 should not list a heading for a template question that is already present
with the exact template wording. Example: "5. User Restoration ETA:" matches, so the extra
"4B. Restoration Time" heading must not be listed as reworded. Only list a question when no
heading for it matches exactly. Add a test for this case, re-run the live CV-19 counts (all
pages, codes and counts only) and report before -> after. Same rules; no git, no baseline.


git add -A
git status
git commit -m "0.64.0: Change Assessment questions must match the template wording" -m "- New Minor rule: reworded Change Assessment questions are listed once per change with the
  template wording to use; answers are still read by meaning
- Numbering, bullets, case and punctuation are ignored; different words and typos are not;
  Internal entries are never read
- Deferral question: template prompt lines are skipped; Yes/No with a reason counts as Y/N
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"
git push