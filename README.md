Fixes (0.50.0). UI only unless noted.

1) Tasks: when "need attention" = 0, hide the amber pill AND the whole "Show: All / Needs
   attention" segment. The controls bar then contains only the expand button, right-aligned.
   When > 0, both behave as now.

2) Filter chips (Work detail Type; Relationships Relationship and Request type; any other chip of
   the same component): label and value separated by a 6px gap; label #5B6880 weight 500; value
   #1C2A42 weight 600; caret after a 4px gap. E.g. "Type  All ▾". Active state keeps the teal
   outline with the value in #0B5F59.

3) Alignment — still NOT fixed after two requests. Before changing anything, use the browser
   (DevTools/computed styles) to find which rule moves these elements, and report it:
   a) In Full change details rows, the right-hand description ("22 open · 0 closed · 6 cancelled",
      "91 with notes · 9 attachments", "CIs, Jira, incidents" …) sits higher than the title.
   b) "Expand all tasks" / "Expand all entries" sit higher than the left side of the controls bar.
   Fix the actual cause (not a pixel nudge): the title row and the controls bar are single flex
   rows with align-items:center; no margin-top, position:absolute, float or line-height
   differences on the right-hand items. Measure with getBoundingClientRect: vertical centres must
   match within ±1px at 100% and 110% zoom, in Chrome. Include the measured numbers in your
   report and keep the test you add for it.

4) Relationships — "Affected services": READ-ONLY question first, then fix:
   - Is it read from a Remedy field (which form/field), or computed by ChangeLens (from which
     relationships)? Report this.
   - If computed: add a small muted note under the label: "Derived from the related
     configuration items".
   - Either way, show it full width (not a narrow box) with services separated as small chips
     (wrapping), so a long list reads easily.

Run the Review browser tests and ruff only. Report the cause found for item 3, the measured
centres, the answer for item 4, files and counts. Then stop. No git.