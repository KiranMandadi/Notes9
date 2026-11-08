Read-only check, no code changes, no git. Explain how support_groups.yaml and the Pending Organisation/Group filters work:
1. How are the Organisation and Group filter values on Pending generated: from support_groups.yaml, from the loaded change data, or both? Name the function(s) and file(s).
2. Does support_groups.yaml limit which changes the Pending fetch pulls from Remedy (the "changes for your groups" scope)? If yes, how is it applied to the query?
3. The file's expected structure (keys, nesting), with one example entry using placeholder names, not real ones. Are names matched exactly (case, spaces)?
4. Is it covered by the enterprise baseline hash (tests/baselines/enterprise.sha256)? Would editing it need check.py --update-baseline?
5. Is it read at Console start-up only, or on every load or Refresh?
6. What else uses it: history pull, Review, Rules, Executive brief, Copilot agents, tests?
7. If I add new organisations and groups: what will change on Pending, and what is needed (restart, baseline, tests, VM update)?
Codes, file paths and counts only. No inline Python. Do not print real group or organisation names.