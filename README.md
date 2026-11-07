Accuracy fix for the summary word-count rule (the rule behind the 7 audit mismatches; confirm its code). Two steps; stop after step 1.

Standing rules: no git operations unless I ask; never read, search or print cr_core/config.py or cr_core/history/config.py; never read .env; GET requests only to Remedy; codes and counts only in replies (no change numbers or text).

Definition of a content word (use one shared helper in both the rule and the audit's independent check):
- split on whitespace and on - / _ :
- strip surrounding punctuation and brackets; drop bracketed tags such as [Synthetic]
- do not count: pure numbers, version strings (e.g. 3.2.1, v2), ticket or ID tokens (letters followed by digits, e.g. CRQ123, ABC-1234 after splitting), single characters
- the threshold stays the same as now

Step 1 (measure only, no rule change committed):
- implement the helper behind a flag, run the full accuracy audit with and without it, and report: mismatches before and after; how many past changes gain or lose this finding; score changes (count, and min/max delta); status changes (count by from→to); confirm #1, #2, #3 and #7 still get the finding and #4, #5 and #6 no longer do.
- add unit tests for the helper: hyphenated words, slashes, underscores, colons, IDs, versions, numbers, bracketed tags, mixed cases like the 7 shapes.
- stop and report. Don't change the rule pack version or docs yet.

Step 2 (only after I approve): make it the default, remove the flag, bump the rule pack's minor version, note the change and its measured impact in CHANGELOG and decisions.md, update the rule's description if it mentions how words are counted, and rerun the full suite and audit (expect 0 mismatches).

No branches, tags or commits.