Impact check: discovery and measurement only. READ-ONLY: no code, config, rule, doc,
baseline or history-schema changes; no git.
Constraints: never read/search/print cr_core/config.py, cr_core/history/config.py or .env;
no Remedy writes; no crq login; no inline Python (-c/stdin/heredoc) — scripts in a file
under work/, deleted after; never touch work/history/; chat shows codes, counts, question
headings and normalised phrases only — no change numbers, names or note text.

Goal: see whether the Change Assessment (Work Detail) can show when the stated Impact is
lower than the assessment suggests. Draft model below; measure only.

1) Find the Change Assessment
   - Work Detail type name(s) used; counts per scope (live: profile groups, Scheduled Start
     2026-08-17 to 2026-12-15, Cancelled/Rejected skipped; history: 6,461 past changes if
     their Work Detail can be read live without excessive calls — report the call cost
     first; if over ~2,000 reads, use a random sample of 1,000 and say so).
   - Is it Public or Internal (Internal notes are stripped today — say if that blocks it)?
   - Question headings found (normalised) and % of entries containing each; confirm the
     numbering (2 Deployment Strategy, 3 Deployment Type, 4 Roll Back (Backout) Type and
     ETA, 5 User Restoration ETA, 6 Business Impact (worst case scenario)); variants.
   - Multiple assessments per change: how often; use the latest.

2) Parse (in the helper only)
   - Q4 and Q5 time: minutes from forms like "< 10 mins", "15 min", "1 hr", "2 hours",
     "30-45 mins" (take the upper bound); "N/A", "none", "not possible", "forward fix",
     blank -> category. Report % parsed, and the 30 most common unparsed values (normalised).
   - Restoration bucket = longer of Q4 and Q5: <=15 min / <=1 h / <=4 h / >4 h-none-unknown.
   - Q2 (+Q3) strategy terms: counts of normalised values; flag "big bang", "no rollback",
     "forward fix", "all at once"; note blue/green, canary, phased, configuration change.
   - Q6 reach (with negation handling — "no impact to clients" is NOT client reach):
     A none/technical only; B one internal team/tool; C broad internal users or one
     external function (consumer, client-facing feature named); D clients/customers/
     consumers broadly or trading/money movement ("all clients", "trading", "any customer").
     Report counts per reach, % unclassified, and the 30 most common phrases per reach.

3) Draft grid (derived Impact; 1 Extensive … 4 Minor)
   D: <=15m 2 | <=1h 1 | <=4h 1 | >4h 1
   C: <=15m 3 | <=1h 3 | <=4h 2 | >4h 2
   B: <=15m 4 | <=1h 4 | <=4h 3 | >4h 3
   A: 4 everywhere
   Strategy "big bang"/"no rollback"/"forward fix only" raises one level (max 1).
   Not derived when Q6 is unclassified or Q4/Q5 both missing (count these).

4) Compare with the stated Impact (Remedy Impact field)
   - Matrix stated x derived (counts), live and history separately.
   - Understated by 1 level and by 2+ levels: counts, by class, ORR and coordinator group
     (group names allowed; no people).
   - Overstated: count only.

5) Evidence for leadership (history)
   - Incident rate after the change (as used by the history comparison) for: derived =
     stated, understated by 1, understated by 2+. Counts and rates with sample sizes.

6) Review file (for me only): work/impact_review.txt with 30 changes — 15 understated
   (mix of 1 and 2+ levels), 10 equal, 5 not derived — each: change id, stated Impact,
   derived Impact, reach + matched phrase, restoration bucket + parsed minutes, strategy
   flag, and Q2/Q4/Q5/Q6 text (<=200 chars each). Do not print it in chat.

Report the numbers, what blocks or weakens the model, and suggested grid or phrase
adjustments. Then stop.