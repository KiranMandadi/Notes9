First report opened from Pending shows the Review landing page (site header, empty CRQ box) for 10–12 s on the shared VM, then "Reading CRQ… from Remedy…", then the report. Every later Open in the same page is fine; after a page refresh the first Open shows it again. Same in incognito, so not caching. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI/server only; rule set id unchanged — confirm it at the end.

1. Diagnose and report before fixing:
   - how the overlay creates its iframe on first Open (initial src; when the change number and embed flag are applied — URL vs postMessage after load);
   - what the embedded page renders before it knows the change;
   - the first-Open request waterfall on this machine (HTML, JS/CSS, report API: start, wait, duration) while Pending is still loading scores, and whether those requests queue behind Pending's summary/scoring/Remedy requests (server worker/thread count).

2. Fix:
   a. Create the iframe with the full embedded report URL (change number + embed flag) from the first Open; the server renders the embedded "Reading CRQ<number> from Remedy…" shell directly when those parameters are present. The landing page and site header must never render inside the overlay.
   b. Warm-up: after Pending finishes its first load (including after a page refresh), create the overlay iframe hidden in embedded mode (no change loaded, no Remedy call), so the first Open behaves like later ones.
   c. Page and static file requests must never be blocked by slow Remedy/scoring requests (enough server workers/threads, or static files served separately). Data stays live; no caching of Remedy data.
   d. After 8 s still loading, show "Still working — Remedy is slow to respond."; on failure, an error with Retry inside the overlay (Back to Pending still works).
   e. Review Decision stays hidden until the report has fully loaded; ‹ › stepping keeps its "waiting for previous report" behaviour.

3. Timing: log (server side, codes and milliseconds only, no names) the steps of building a report: Remedy read(s), rule scoring, history lookups, overlap search, rendering. Report the breakdown for 3 changes.

Tests:
   - first Open never shows the landing page or site header (slow mocked report API and a busy Pending load);
   - reload the Pending page, then click Open immediately (before Pending's scores finish): the overlay goes straight to the "Reading…" shell, never the landing page;
   - warm-up iframe present after Pending loads;
   - static requests are served while a slow API request is in flight;
   - slow-load message (time mocked);
   - error state with Retry.
Update screenshots, docs (deploy notes) and CHANGELOG (no new version). Run all tests with pytest; report counts and the rule set id.
No branches, tags or commits.

git status
git add -A
git commit -m "Overlay: embedded report shell on first open, warm-up frame, no landing page flash, load timing"
git push