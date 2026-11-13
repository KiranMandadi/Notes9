Task: Pending page — one clear loading/status message above the table, plus a small spacing fix.
Mock-up (agreed): "Pending - loading and status messages" board. Follow it exactly.

Files likely involved: cr_core/ui/static/pending.js, console.css (and console.js only if the
progress-cursor helper lives there). Don't touch server.py unless a request can't be cancelled
without it — if so, stop and tell me first.

1) ONE place for every load/refresh message
   - Remove today's loading/refresh/error texts wherever they currently appear (inside the
     table, the results row, or elsewhere on the page). No message inside the table while loading;
     existing rows stay until the new data replaces them.
   - Add a single status pill on the line directly above the table, LEFT side. The
     "Review decisions · Decided N of M · Copy Decisions" group stays on the RIGHT of the same line
     (margin-left:auto). The line keeps a fixed min-height (36px) so nothing jumps when the
     pill appears or disappears.
   - Pill: height 34px, radius 999px, padding 0 14px, gap 10px, 13px / weight 600, 1px border.
   - Container: role="status" aria-live="polite"; in the Failed state use role="alert".

2) States (exact colours/text)
   a) Loading a stage (user ticks a status that loads on demand):
      bg #EEF3FA, text #1C3358, border #C9D6EA, no shadow.
      Teal spinner 14px (border 2px rgba(14,124,116,.22), top #0E7C74, 0.8s linear).
      Text: "Loading <stage names joined with 'and'>…"  then " · Cancel" (link, #0E7C74, underlined).
      Table stays at full opacity.
   b) Refreshing (header ↻ Refresh button):
      Same pill and colours as (a), text "Refreshing from Remedy… · Cancel".
      Header button shows "Refreshing…" with bg #E6EBF2 and is disabled while running.
      Table opacity 0.85 (transition 150ms) until the new rows render.
   c) Slow: if (a) or (b) is still running after 10 seconds, the same pill turns amber:
      bg #FDF0DC, text #6B3A06, border #E8B266, amber spinner (rgba(138,75,8,.3) / #8A4B08).
      Text: "Still working — Remedy is slow to respond · Cancel" (link #8A4B08).
      Refresh keeps the 0.85 table fade during Slow.
   d) Failed: bg #FDE8E7, text #7A1212, border #F3C1BC, icon "⚠".
      Text: "Couldn't load <stage> — Remedy didn't respond · Retry" (link #A61B1B)
      (for refresh: "Couldn't refresh — Remedy didn't respond · Retry").
      Previous rows stay on screen at full opacity. Retry re-runs exactly the same request.
      Stays until Retry, a new load, or a filter change. Error codes only — never show raw
      server text, URLs, logins or stack traces.
   e) Done: bg #E3F4EA, text #14532D, border #9ED3B4, icon "✓".
      Text: "Updated HH:MM · N changes" (ET, same format as the header "as of" time,
      N = total changes loaded). Header "as of" time updates too.
      Pill fades out after ~4s (opacity to 0 over the last 0.8s, then removed).

3) Progress cursor — in EVERY in-flight case
   While (a), (b), (c) or a Retry is running, set cursor: progress on the page (same mechanism
   reports already use when opening). Clear it on Done, Failed or Cancel. Make sure it is always
   cleared even if the request throws (finally block). Use "progress", not "wait", so the page
   stays clickable.

4) Cancel
   - Uses AbortController on the in-flight fetch(es). No new server work.
   - Cancel on a stage load: abort, un-tick the stage(s) that were being loaded so the filter
     matches what's on screen, clear the pill.
   - Cancel on refresh: abort, keep the previous rows, restore table opacity and the Refresh
     button, clear the pill.
   - A newer load/refresh supersedes an older one (abort the old one; ignore late responses).
   - The existing single-flight /api/status protection must not change.

5) Motion
   Under prefers-reduced-motion: no spinner rotation (static ring) and no fade animation.

6) Small fix carried over: add 6px space above the row status pill on the Window column's
   third line (it currently sits too close to the second line).

Must not change
- Live Remedy data only, no caching of any kind, no change to rules/scoring/filters/defaults.
- ChangeLens logo, header layout, Technical details toggle, icons.
- Approver login and search text never go in the URL.

Standing rules
- Never read, search or print cr_core/config.py, cr_core/history/config.py or .env.
- No git commands. No inline Python. Don't run --update-baseline. Never run crq login.
- Replies: codes and counts only.

Testing (tiered — not the full gate)
- Run the UI/static tests for the Pending page and any test touching pending.js.
- Add/adjust tests for: Slow switch at 10s (fake timers), Cancel aborts and un-ticks,
  superseded request ignored, cursor cleared on success/failure/cancel, Done text format.
- Report: files changed, tests run and pass/fail counts. Then stop for my review.
- Add a CHANGELOG entry under "Unreleased": "Pending: one clear loading/status message above
  the table (loading, refreshing, slow, failed, updated), progress cursor while loading,
  Cancel/Retry; spacing above the row status pill."