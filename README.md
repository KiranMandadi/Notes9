Pending loading/status — more visible (design: "Pending - loading v2" board; ignore its "Done"
what-changed highlight and the Reduced-motion switch). UI only.

1) Progress bar: a 3px bar on the TOP edge of the table card (inside its rounded border), shown
   while loading a stage or refreshing. Indeterminate animation: a 35%-wide segment sliding
   left→right (1.1s ease-in-out, infinite) on a faint track. Teal #0E7C74 on
   rgba(14,124,116,.12); amber #D97706 on rgba(217,119,6,.15) in the slow state. Hidden when
   failed or done. Under prefers-reduced-motion: a static full-width stripe.

2) Status pill (same position/line as now), stronger:
   - loading/refresh: bg #FFFFFF, text #0B1B33, border 1.5px #0E7C74, shadow
     0 1px 3px rgba(11,27,51,.10); spinner 15px, border 2.5px rgba(14,124,116,.2), head #0E7C74;
     "· Cancel" #0E7C74 underlined.
   - slow: bg #FFF7EB, text #6B3A06, border #D97706, amber spinner; text "Still working — Remedy
     is slow to respond (N s)" where N counts up every second (muted #8A4B08); "· Cancel".
   - failed: bg #FDE8E7, text #7A1212, border #E5877F, "⚠ … · Retry" (#A61B1B).
   - done: bg #E3F4EA, text #14532D, border #7CC49B, "✓ Updated HH:MM · N changes", fades after
     ~4s (no new/gone counts, no row highlight).

3) Refresh button: the ↻ icon rotates (0.9s linear) while refreshing; label "Refreshing…" as
   now. Static under prefers-reduced-motion.

4) Table dim while refreshing/slow: opacity 0.7 (was 0.85). Loading a stage keeps full opacity.

5) No flicker: show the bar and pill only if the request takes longer than 300 ms; once shown,
   keep them visible for at least 600 ms. Cancel/Retry/superseding still work as today. The
   progress cursor follows the same timing.

6) Keep all existing behaviour: Cancel un-ticks a loading stage, newer loads supersede, 10 s
   switch to slow, aria-live status, progress cursor cleared on done/failed/cancel.

Tests (fake timers): no bar/pill for a 200 ms response; bar+pill shown at 400 ms and kept until
≥600 ms; slow at 10 s with the counter text updating; done pill text; refresh icon rotation
class present only while refreshing; reduced-motion static stripe. Run the Pending browser tests
and ruff only. Report files and counts; then stop. No git.