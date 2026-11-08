Same standing rules; no git operations unless I ask.
The 139-group support_groups.yaml is final and confirmed correct (no typos).
1. Update the data-owner record in docs/setup-enterprise.md to 9 organisations / 139 groups (no names). Note that some groups have no recent changes as Manager Group, which is expected.
2. Add to docs/open-items.md: "Pending 'your groups' matches Manager Group (1000000015), not Coordinator Group (1000003229); the field-map comment saying they hold the same value is wrong. Business decision needed before any change." Correct that comment in remedy_field_map.yaml to state the two fields are different.
3. Run all tests with pytest; report counts.
No branches, tags or commits.

python scripts/check.py --update-baseline
python scripts/check.py
git status
git add tests/baselines/enterprise.sha256 scripts/group_counts.py docs/setup-enterprise.md docs/open-items.md profiles/enterprise/config/remedy_field_map.yaml
git commit -m "Support groups: baseline for 139 groups; group_counts diagnostics; Manager vs Coordinator group noted"
git push