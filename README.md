Console readability: render at 100% the way it looks today at 110% browser zoom. Same standing rules; no git operations unless I ask. UI only; rule set id unchanged — confirm it.
1. Scale the Console's design tokens by 1.10 (round to the nearest 0.5 px): font sizes, line heights, letter-spacing where in px, spacing/padding/gaps, control heights (chips, buttons, inputs, search), border radii, icon sizes, table row padding, popover widths, the overlay toolbar and report widths. Prefer changing the shared tokens/variables over editing individual rules; convert any hard-coded px sizes you touch into tokens.
2. Page width: change the 1360 px max width to 1496 px, but never wider than the viewport minus 32 px side gutters (e.g. max-width: min(1496px, 100vw - 64px)), so 1440 px laptops have no horizontal scroll. Keep the phone layout as is.
3. Apply to every page: Review landing, Pending (list, calendar, filters, popovers, overlay), Quality report, Rules, footer. The favicon and logo artwork stay the same shapes, scaled only as the header scales.
4. Check at 1440×900 (laptop) and 1920×1080 (desktop) at 100% browser zoom: no horizontal scroll, no clipped chip labels, filter rows still two rows (RISK, SCOPE) at 1920 and wrapping cleanly at 1440, Review decisions bar and table results row each on one line at 1920.
Tests: run the full browser suite (layout checks, readability test: nothing under 12 px, contrast), update any pixel thresholds that change by the 1.10 factor, and add a test that body text is at least 14 px and the page has no horizontal scroll at 1440 px. Update screenshots. One CHANGELOG line.
List decisions under "Decided".
No branches, tags or commits.


git status
git add -A
git commit -m "Pending: View by replaced by Risk filters; fixed ORR/Risk Level defaults; pill in results row; Show only <name>; approver clear button"
git push