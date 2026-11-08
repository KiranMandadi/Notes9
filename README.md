   git status
   git add -A
   git commit -m "Pending: Status filter (four approval stages, default Scheduled For Approval, other stages on demand)"
   git push

   Option 1: split the group search. Same standing rules (including Running commands); no git operations unless I ask. Do not print group or organisation names; refer to them by position.
1. In cr_core/remedy, split the group part of the qualification into batches so each full encoded request URL stays under a configurable limit (default 4,000 characters). One search per batch with the same status/date/other terms; merge results and de-duplicate by change id; keep sorting and paging correct across batches. Limited concurrency (default 3). Live data only, no caching. The duplicate-by-reference check is unchanged.
2. If a single group alone would exceed the limit, fail with a clear message naming it by position (group #n).
3. Apply to every caller: Pending, Review search, crq search, crq summary, the audit's Overlaps check, and the history pull if it builds the same qualification.
4. crq doctor: report the longest request URL length and the batch count; say "URL too long" instead of a bare 414.
5. Add a read-only helper scripts/group_counts.py (a file, not inline) that reports, for each group in support_groups.yaml by position, the number of its changes in Remedy over the last 90 days. Flag 0 as "possible name mismatch".
6. Test with the current 44-group file first: 1 batch, results identical to today (40 pending), Pending load time unchanged. Then copy work/support-groups/support_groups-9-orgs-139-groups.yaml into place and report: batch count, Pending total for all approvers, load time (median of 3 loads), group_counts.py results (positions and counts only), and the audit result (check.py --browser --audit).
7. Update the pinned tests to 139 groups and 9 organisations only after step 6 passes. Do NOT run --update-baseline; I will after reviewing.
Unit tests: batching at 44 and with a large synthetic list, merge/de-duplication, paging across batches, the long-single-group error. Run all tests with pytest; report counts.
No branches, tags or commits.


   git status
   git add -A
   git commit -m "Remedy: batch group searches to stay under the URL limit; support groups: 9 organisations, 139 groups"
   git push