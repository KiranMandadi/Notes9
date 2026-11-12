Rule updates: freeze windows, Risk Level 4–5 Notes questions, Exec Summary, CV-02 advisory. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. Never read .env. Do not run --update-baseline; I will.

STEP 1 — measure only, then STOP and report (no rule pack or calendar edits yet):
For each change below, run it against the 6,461 audit changes and the live pending list (all approvers) using a temporary helper under work/ (delete it afterwards), and report: findings added/removed, score changes (from → to, counts), status changes (counts), and 5 example changes each (change number, rule, the text matched or missing). Also list any existing rule that already checks the same thing (to avoid duplicates).

A. Freeze windows (calendar.yaml, US Eastern, apply to all changes incl. Emergency):
   - keep: 26 Oct 2026 09:00 → 2 Nov 2026 21:00; 4 Nov 2026 09:00 → 8 Nov 2026 21:00
   - replace 11–15 Nov with: 13 Nov 2026 09:00 → 15 Nov 2026 09:00
   - replace 21 Nov–6 Dec with: 27 Nov 2026 09:00 → 2 Dec 2026 09:00
   - remove: 18–31 Dec 2026

B. Risk Level 4–5 (field 1000000180 = "Risk Level 4" or "Risk Level 5"):
   - Work Detail types Business Justification, Risk Assessment, Technical Design and Test Plan are NOT required (the missing-Work-Detail-types finding must not ask for them). Risk Level 1–3 unchanged.
   - New rule: Notes must answer questions 6, 6a, 7, 8 and 9 of the template (block headed "Required for Risk Level 4 and 5 CRQs…"). Wording:
     6. To further address impact; how would an unexpected failure be recognized and what would the customer experience be?
     6a. Will the unexpected failure impact Client Service & Support (CS&S) call volumes or directly?
     7. Are there any production mainframe and/or distributed batch job schedules that could be impacted? If Yes describe.
     8. List the individuals/departments that have been notified regarding this activity (Include all impacted parties) and when notification will be or was sent.
     9. Is evidence of Organizational CAB Review populated in the Work Info Item?
   - One Major (−20) when one or more are unanswered, listing them ("Notes questions 6a and 9 are unanswered"). None when all answered.
   - Question 9 answered "No" counts as answered, plus an advisory (0 points): "Organizational CAB evidence is not in Work Info — the change won't be selected for HRCAB."

C. Exec Summary — changes not yet approved only (Draft, Request For Authorization, Request For Change, Planning In Progress, Scheduled For Review, Scheduled For Approval); never for Scheduled, Implementation In Progress, Completed, Closed, Rejected, Cancelled. Notes must answer:
     1. What is changing, and why are we changing it?
     2. How will we control production impact during and after implementation?
     3. Is there an exceptional recovery risk associated with this change?
   - Found anywhere in Notes; "Exec Summary" heading and the "DO NOT REMOVE…" line are not checked.
   - One Major (−20) when one or more are unanswered (or the section is missing), listing them. "No" is a valid answer to question 3.

D. CV-02 (top levels of Urgency, Impact and Priority): change from active Minor to advisory ("Worth a look", 0 points). Condition and wording unchanged.

Rules for B and C:
   - Match questions by wording, case-insensitive, tolerant of extra spaces/line breaks, a missing "?", formatting, and any leading number, letter or bullet ("1.", "1)", "6a.", "a.", "•", "-", "*") or none.
   - An answer is the text after the question on the same line or following lines, up to the next question or the end of the block. Not an answer: blank, "N/A", "NA", "-", "TBD", "None", or only template text (e.g. "If No, the change will not be selected for review…").
   - Record match offsets so evidence highlighting works.

STEP 2 — only after my go-ahead: apply A–D, bump the affected pack versions, update the rules catalogue, user-guide and CHANGELOG (no new version), add unit tests (numbered/bulleted/plain question formats, N/A-style answers, 9 = "No", status scoping for C, risk 1–3 vs 4–5 for B, CV-02 advisory), run python scripts/check.py --browser --audit and all tests with pytest, and report old/new rule set id, mismatches and every score/status difference.
No branches, tags or commits.