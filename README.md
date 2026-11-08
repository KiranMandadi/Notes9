cp profiles/enterprise/config/support_groups.yaml ~/support_groups.new.yaml
git restore profiles/enterprise/config/support_groups.yaml

Remedy searches fail with HTTP 414 (URI too long) when support_groups.yaml has more groups, because _qualification in cr_core/remedy/api.py puts every group into one GET URL. Same standing rules (including Running commands); no git operations unless I ask. Do not print group or organisation names.
1. Split the group part of the qualification into batches so each request URL stays under a safe limit (configurable, default 4,000 characters for the full encoded URL). Run one search per batch with the same status/date/other terms, merge the results, and de-duplicate by change id. Keep sorting and paging correct across batches.
2. Run batches with limited concurrency (default 3) to keep load time reasonable. Live data only, no caching.
3. If a single group name alone would exceed the limit, fail with a clear message naming the group by position (group #n).
4. Apply to every caller: Pending, Review search, crq search, crq summary, and the history pull if it builds the same qualification. The duplicate-by-reference check is unchanged.
5. Make crq doctor report the longest request URL length and the number of batches, and say "URL too long" instead of a bare 414.
Tests: unit tests for batching (1 batch at 44 groups, several batches with a large synthetic list), merge and de-duplication, and paging across batches. Do not change the pinned group counts yet. Run all tests with pytest; report counts and the Pending load time before and after (Console access log).
No branches, tags or commits.