Status message styling (Pending): it currently looks like a filter chip (white + teal outline).
Change all states to a status-message style, distinct from chips:
- border-radius 8px (not 999px), NO border, padding 0 14px 0 16px, height 34px,
  left accent bar via box-shadow: inset 3px 0 0 <accent>.
- loading/refresh: bg #E6F4F2, text #0B1B33, accent #0E7C74 (spinner unchanged)
- slow: bg #FDF0DC, text #6B3A06, accent #D97706
- failed: bg #FDE8E7, text #7A1212, accent #C0392B
- done: bg #E3F4EA, text #14532D, accent #2E9E5B
Progress bar, Refresh icon, elapsed counter and timings unchanged. Update the style assertions
in the Pending browser tests; run them and ruff only. Report files and counts; then stop. No git.