Pending: add a Status filter with on-demand loading for non-default stages. Same standing rules (including Running commands); no git operations unless I ask.

1. Data:
   - Default load is unchanged: one live Remedy query for Scheduled For Approval only, same speed as today.
   - The other three approval stages (Request For Authorization, Planning In Progress, Scheduled For Review) are fetched live only when the user ticks one of them or chooses All stages. Fetch only the stages ticked, then score them like the rest.
   - Live Remedy data only, no caching (shared mode included). No other statuses ever appear on Pending.
   - Refresh reloads the default stage plus any stages already loaded in this page view.
   - Opening a URL with status=all or a list loads those stages on page load.

2. Filter button "Status", right after Class: Class · Status · Date · Organisation · Group · Approver · Clear all. Same look and behaviour as the Class multi-select:
   - Values in lifecycle order: Request For Authorization, Planning In Progress, Scheduled For Review, Scheduled For Approval. "All stages" at the top, indeterminate (–) when only some are ticked.
   - Default: Scheduled For Approval only. Button reads "Status Scheduled For Approval" in the normal white style.
   - Unloaded stages show "Loads when selected" (#5B6880) instead of a count and are always enabled. Once loaded, they show their count; a loaded stage with 0 is disabled unless ticked (same as other filters).
   - While a stage is loading: a small spinner and "Loading…" on that line in the popover. The table keeps showing what is already loaded, with a slim "Loading other approval stages…" note above the results line. Scores fill in as today.
   - On fetch failure: that stage shows "Couldn't load — Retry" in the popover; nothing else on the page breaks.
   - Popover note: before loading, "Other approval stages are not included by default." After loading, "Other approval stages are not included by default. (N hidden)".
   - URL: no status parameter for the default; status=all for all four; otherwise a comma list of short codes (rfa, planning, review, approval). Approver and search text still never go in the URL.
   - "Clear all" resets Status to the default and does not unload stages already fetched.

3. Status filters everything downstream: header count, View by tile counts, "Showing N of M", calendar, and the Review decisions total. Copy Decisions still copies every recorded decision.

4. Empty state: if the default shows nothing, show "No changes at Scheduled For Approval. Show other approval stages" (link ticks All stages and loads them). After loading, if there are changes, the normal table appears.

5. Phone: Status sits in the filter row like the others.

Docs: user-guide (filters section, explain on-demand loading), CHANGELOG (no new version), decisions.md entry ("Pending Status filter: four approval stages, default Scheduled For Approval, other stages fetched on demand to keep the default load time unchanged").
Tests: unit tests for the status list, default, and the fetch only requesting ticked stages; browser tests (with the Remedy calls mocked) for default button text and note, "Loads when selected", loading state, counts after load, failure + Retry, URL round-trip including load on open, Refresh reloading loaded stages, Clear all reset, empty-state link, and the decisions total following Status. Update screenshots. Run all tests with pytest; report counts.
Report the default Pending load time before and after (from the Console access log) to confirm it is unchanged.
No branches, tags or commits.