0.64.1: CV-19 wording and split headings.
1) Message: "Change Assessment: <count in words> question(s) don't/doesn't match the template
   wording:" (one..nine in words; singular/plural correct), then the lines as today. Fix text
   "Use the current Change Assessment template wording for this question" / "these questions".
   Headline uses the same wording rule.
2) Split heading: when a heading line is followed by a line that starts with the bracketed
   part of the template question (e.g. "(worst case scenario)", "(Backout)", "(Y/N)"), treat
   that bracketed text as part of the heading for the wording match, and read the rest of that
   line as the answer. Example: "6.Business Impact:" then "(worst case scenario): ..." matches.
3) Tests: one/five in words, singular/plural; split "(worst case scenario)" matches and its
   answer is read; a different bracketed text on the next line does not match.
CHANGELOG 0.64.1; pyproject 0.64.1. Verification: ruff; crq rules validate; tests for changed
modules plus test_security; browser -k review. Report old -> new rule set ID and live CV-19
counts before -> after (all pages, codes and counts only), score and verdict changes.
No git, no baseline, no audit. Usual rules: no heredocs, python -c, python - or stdin; do not
read the config files or .env; never delete anything under work/history/.

git add -A
git status
git commit -m "0.64.1: clearer template-wording message; split headings accepted" -m "- CV-19 message starts 'Change Assessment:' and spells the count in words, so it is not read
  as a question number; fix text singular/plural
- A bracketed part of the template question starting the next line (e.g. '(worst case
  scenario)') counts as part of the heading
- Rule set <old> -> <new>; baseline, docs, CHANGELOG and tests updated"
git push