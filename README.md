Change Assessment completeness: build. Constraints unchanged: never read/search/print
cr_core/config.py, cr_core/history/config.py or .env; no Remedy writes; no crq login; no
git; no inline Python; do NOT run --update-baseline; never touch work/history/; delete
work/ca_review.txt now; chat shows codes and counts only.

Standard (CES CAB, 13 Nov 2026), Work Detail type "Change Assessment", latest entry:
 1 Justification · 2 Deployment Strategy · 3 Deployment Type · 4 Roll Back (Backout) Type
 and ETA · 5 User Restoration ETA · 6 Business Impact (worst case scenario) ·
 7 Rollback/Backout Plan Attestation or Validation Sign-Off · 8 Can this be deferred 3 to
 5 days? (Y/N) · 9 Justification on why the change cannot be deferred.
Use the heading matching and variants from the measurement (number + key words; the
disambiguation rules for Q4/Q7 and Q1/Q8/Q9; "(Y/N)" prefix stripped).

Config (new block, e.g. change_assessment in quality_rules.yaml or a profile config file):
 work_detail_type, the 9 questions with variants, unanswered values (blank, na, n/a,
 none, not applicable, tbd, line of dashes, [todo...]), excluded classes [Standard,
 Latent, Emergency], organisations in scope (the 9 "CES - ..." organisations).

Rules (next free ids; neutral wording, no "your"):
 R1 Major — no Change Assessment Work Detail.
 R2 Major — one combined finding listing every gap: questions missing; questions present
    but unanswered; Q7 empty; Q8 = N with Q9 missing/unanswered. Q9 is NOT required and
    "N/A" is valid when Q8 = Y. Q7 counts as answered with either an attestation or a
    "testing not possible … why" statement — presence only, never quote or store Q7 text.
    Message: "Change Assessment incomplete: questions 5, 7 and 8 are missing; question 2
    is unanswered." (names in Technical details, e.g. "5 User Restoration ETA").
 R3 Minor — Q8 present but not a clear Y/N.
 R4 Advisory — Q4 or Q5 answered but with no readable time.
 Same lifecycle as the Exec Summary rule: Major/Minor while awaiting approval; advisory
 once Scheduled/Closed. Excluded classes and out-of-scope organisations: not applicable.
 History replay: not applicable when the assessment isn't stored (no findings).
 Internal entries: read in memory for the rule; the report says the entry is Internal and
 never shows its text. No answer text in findings or logs.

TESTS: complete assessment passes; no assessment -> R1; missing + unanswered -> one R2
listing both; Q8=Y with Q9 N/A or absent passes; Q8=N with Q9 blank -> R2; Q7 "testing
not possible because…" passes; Q7 empty -> R2; Q8 "maybe" -> R3; Q4 "quick" -> R4;
Standard/Latent/Emergency -> none; Scheduled -> advisory; heading variants from the
measurement; no answer text in output. Existing tests stay green.
DOCS: rule catalogue, user-guide, configuration, CHANGELOG 0.53.0, pyproject 0.53.0;
Guide page glossary one line "Change Assessment".
VERIFY: ruff, full suite, check.py --browser --audit (report rule set id).
MEASURE (built code, live scope): R1-R4 counts by status group and class; verdict
changes (to Needs work / Blocked); work/ca_spotcheck.txt with 15 changes (5 R1, 7 R2,
3 complete) — change id, class, status, findings, question numbers only, no text. Then stop.