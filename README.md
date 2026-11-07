Use the narrower ID definition and re-measure (still step 1; don't proceed to step 2).

Content words: split as now (spaces, - / _ :, plus | , ;). Do NOT count only:
- ticket keys: letters, a hyphen, then 3 or more digits (e.g. ABC-1234) — check the key before splitting on hyphens
- CRQ/INC (and other Remedy) record numbers
- pure numbers, version strings (3.2.1, v2), dates and ratios (9/9, 2026-11-07)
- bracketed tags and single characters
Letters-then-digits names such as Db2, EC2, Java17, A9 DO count as words.

Re-run the full audit with the flag on and report the same table as before: Q-COMPLETE-04 findings, mismatches, gains and losses, score changes (count and min/max), status changes (from→to), and whether each of the 7 cases has the finding. For any remaining new findings, give their shapes only (no text) and whether each looks genuinely too short. Update the unit tests (Db2, EC2, Java17 count; ABC-1234, CRQ numbers, versions, dates don't). No branches, tags or commits.