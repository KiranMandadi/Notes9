Re-measure once more with these adjustments (still step 1; don't proceed to step 2):

1. Numbers, versions, dates and ratios COUNT as words again (as the current rule does). Do not drop them.
2. Words inside bracketed tags COUNT (remove only the brackets).
3. Still drop: ticket keys (letters, hyphen, 3+ digits), Remedy record numbers (CRQ/INC etc. with 5+ digits), single characters and standalone punctuation (e.g. a lone "-").
4. Splitting unchanged: spaces, - / _ : and | , ;. Letters-then-digits names (Db2, EC2, Java17) count.
5. #7 losing the finding is accepted.

Report the same table: Q-COMPLETE-04 findings, mismatches, gains/losses, score changes (count, min/max), status changes (from→to), each of the 7 cases, and the shapes of any new findings with your "genuinely too short?" view. Update the unit tests for the new rules (numbers and tag words count; ticket keys, record numbers and lone punctuation don't). No branches, tags or commits.