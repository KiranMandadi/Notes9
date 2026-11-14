Relationships (0.50.0). UI only.

1) Remove the "Affected services" block (label, note and chips) from the Relationships panel in
   the Console and the saved HTML report. Do NOT remove the underlying affected_services data:
   first report where else it is used (rules, At a glance, overlaps, history, crq get) and keep
   those uses unchanged. The Relationships table, filters and counts stay as they are.

2) Relationships table: the Status column is vertically centred while the other cells are
   top-aligned, so Status sits lower than Relationship / Request type / Summary, and the STATUS
   header sits lower than the other headers. Make every cell (headers and rows) align to the
   first text line: align-items:start, the same padding-top on all cells, and the same header
   style.

Tests: remove or adjust the Affected services browser checks; add a check that the Status cell
and the Relationship cell share a top edge (±1px) in a row whose summary wraps onto two lines;
confirm the rule set id is unchanged (7066972d). Run the Review browser tests and ruff only.
Report where affected_services is used, files changed and counts. Then stop. No git.