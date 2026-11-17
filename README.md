Change Assessment completeness: measurement only. READ-ONLY: no code, config, rule, doc,
baseline or history-schema changes; no git.
Constraints: never read/search/print cr_core/config.py, cr_core/history/config.py or .env;
no Remedy writes; no crq login; no inline Python — scripts in a file under work/, deleted
after; never touch work/history/; delete work/impact_review.txt now (it holds names);
chat shows codes, counts, group names and normalised headings only — no change numbers,
people's names or note text.

Standard (CES CAB, 13 Nov 2026): Work Detail type "Change Assessment" with
 1 Justification · 2 Deployment Strategy · 3 Deployment Type · 4 Rollback or Backout
 Type and ETA · 5 User Restoration ETA · 6 Business Impact · 7 Rollback or Backout Plan
 Attestation · 8 Can this change be rescheduled (3 to 5 days) - Y/N · 9 Justification
 (if N to #8).

Scope: live (profile groups, Scheduled Start 2026-08-17 to 2026-12-15, Cancelled/Rejected
skipped). Split every count by: CES groups vs other groups (say how CES is identified —
group name prefix or another field — and list the groups counted as CES); class; status
group (awaiting approval / scheduled / closed); submitted before vs on/after 2026-11-13.
Use the latest Change Assessment per change.

Simulated checks (helper only):
 CA-a No Change Assessment Work Detail.
 CA-b Each of the 9 questions missing (match by number + key words, tolerant of the
      variants already seen: "roll back", "rollback eta", "restoration time", "impact
      (worst case scenario)", "attestation or validation sign-off", etc.).
 CA-c Question present but unanswered: blank, "N/A", "NA", "none", "-", "TBD",
      "[todo...]" placeholders, or only the next heading.
 CA-d Q4 or Q5 has no readable time (use the earlier parser incl. number words, "> N",
      "N+", "same as deployment"; "rollback not required (SPR / new deployment)" counts
      as answered for Q4).
 CA-e Q8 not a clear Y/N; CA-f Q8 = N and Q9 missing/unanswered.
 CA-g Q7 present but empty (presence only; never read or print attestation text).

Report:
 1) Counts per check, with the splits above; how many changes would get 0 / 1 / 2+
    findings; and which question is missed most.
 2) Answer-quality signals: top 15 normalised "unanswered" values; how Q8 is written
    (Y/N/Yes/No/other) with counts.
 3) Matching risk: headings that look like a question but didn't match (top 20,
    normalised), and any case where one heading matched two questions.
 4) Incidents within 7 days (history, read live as before) for: complete assessment,
    1-2 questions missing, 3+ missing, no assessment — counts and rates.
 5) Spot-check: work/ca_review.txt with 20 changes (8 complete, 8 with gaps of different
    kinds, 4 with no assessment): change id, group, class, status, each question
    found/missing/unanswered, Q8 value — NO answer text and NO attestation text.
    Do not print it.
 6) Recommend severity per check and whether CES-only or all groups, with reasoning.
Then stop.