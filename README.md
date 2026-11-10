Report speed: sign-in reuse, batched overlap queries, faster history lookup. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. Never read .env. Data stays live: no caching of any Remedy data (changes, overlaps, approvals). Results must be identical before and after.

Baseline first: run crq timing for CRQ000002484053, CRQ000002289292, CRQ000002299314 (3 runs each, median per step) and report it.

1. Reuse the Remedy sign-in:
   - Keep the session token in server memory only (never on disk, never logged, never sent to the browser), shared by requests that use the same configured account.
   - Renew it shortly before it expires; on a 401/expired-token response, sign in again once and retry the request once; never loop.
   - Sign out (release the token) on crq ui --stop / shutdown.
   - Thread-safe: concurrent requests must not trigger parallel sign-ins (one sign-in at a time, others wait for it).
   - The CLI (crq search, crq get, audit) may keep signing in per run if simpler; say which you chose.
   - Respect any existing auth settings; no change to how credentials are read.

2. Batch the overlap lookups: replace the per-item Remedy requests (28 for CRQ000002484053) with as few combined queries as possible (OR-qualifications, split into batches under the same URL-length limit used for support groups; limited concurrency). De-duplicate results. The overlaps found must be exactly the same as today.

3. History lookup: profile the ~1.7 s per report; add the missing indexes (or fix the query) in history.db. Local data only; history.db is never committed; no schema change that loses data (indexes only, created if missing at start-up).

4. Verify after each step, before starting the next; stop and report if any finding, score, overlap or status changes:
   - python scripts/check.py --browser --audit: 0 mismatches, same rule set id, "overlap search missed 0";
   - crq timing for the same 3 changes (3 runs each, median per step), shown as before → after per step.

Tests: token reused across reports; re-sign-in on expired token with one retry; no parallel sign-ins under concurrency; token never in logs or responses; overlap batching gives identical results to the per-item path on fixtures (including the URL-limit split); history indexes created idempotently. Update docs (operations: sign-in reuse, sign-out on stop) and CHANGELOG (no new version). Run all tests with pytest; report counts and the rule set id.
No branches, tags or commits.

git status
git add -A
git commit -m "Report speed: reuse Remedy sign-in, batched overlap queries, history indexes"
git push