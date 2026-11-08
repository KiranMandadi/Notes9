Read-only check, no code changes, no git. Do not print group or organisation names; use positions from support_groups.yaml.
For each of the 65 groups flagged 0 by scripts/group_counts.py:
1. Which Remedy field does the ChangeLens group filter match on (field id and label)?
2. Does a support group with this exact name exist in Remedy's support group list? Report: exists exactly / exists with a case or spacing difference / not found.
3. Over the last 90 days, how many changes does it have in other group fields (e.g. manager group, coordinator group, task assignee group)? Report counts per field.
4. Summarise: likely typo (not found or near-match), real group but not used in the searched field, or real group with no recent changes.
Extend scripts/group_counts.py only if needed to do this (file, not inline), read-only. Report positions, categories and counts only.


   python scripts/check.py --update-baseline
   python scripts/check.py
   git status
   git add profiles/enterprise/config/support_groups.yaml tests/baselines/enterprise.sha256 docs/setup-enterprise.md
   git commit -m "Support groups: verified names; baseline updated"
   git push