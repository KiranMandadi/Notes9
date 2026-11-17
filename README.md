Impact understated: measurement only. READ-ONLY: no code, config, rule, doc, baseline or
history-schema changes; no git. Verification level: none (measurement). Usual
constraints (no config.py/.env, no Remedy writes, scripts under work/ deleted after,
never touch work/history/; chat shows codes and counts only).

Input: latest Change Assessment, CAB question "Business Impact (worst case scenario)" (Q6,
incl. old "Impact" variants already matched) and restoration time = longer of Q4 / Q5
(existing parser). Skip Internal entries, Standard/Latent/Emergency, Cancelled/Rejected.

Classifier (in the helper only):
 a) SKIP the answer if it contains a no-impact statement anywhere: "no impact", "no
    business impact", "no customer/client/consumer impact", "not impacted", "no impact is
    (expected|anticipated)", "will not impact", "zero impact".
 b) HARM = a people/business noun + a harm verb in the same sentence:
    nouns: customer(s), client(s), consumer(s), user(s), advisor(s), investor(s),
      account holder(s), trading, trade(s) confirm(ation)s, settlement, money movement,
      payment(s), login/log in, statements, T+1, SLA
    verbs: unable / not able / cannot / can't / won't be able / may not be able,
      impacted, disrupted, delayed, delay, fail(ure)s, outage, down, unavailable,
      errors, at risk, interrupted
 c) NOT people: "client" followed by secret, certificate, cert, TLS, SSL, id, app,
    application, library, side, config; system names from a config list (start with
    "Client Central"); "job(s)", "batch", "downstream job(s)", "abend(s)" alone.
 d) Reach: D = customers/clients/consumers/investors/trading/trade confirms/settlement/
    money movement/payments/T+1 broadly ("all", "any", "customers", plural);
    C = one named function or internal users broadly. Else not derived.
 Grids (derived Impact, 1 Extensive … 4 Minor), restoration <=15m / <=1h / <=4h / >4h-none:
  Grid A: D 2/1/1/1 · C 3/3/2/2      Grid B: D 3/2/1/1 · C 3/3/2/2
 Flag = derived impact higher (smaller number) than the stated Impact.

Acceptance (must hold, use as fixtures — normalised text, no ids):
 FLAG: "A failure or output mismatch could interrupt TCN processing, produce incorrect
   confirm fields or file links, or delay Trade Confirm delivery and put the T+1 SLA at
   risk" (stated 3) ; "During market open if an issue occurs, customers may not be able to
   reset password using Forgot your login application" (stated 4).
 NO FLAG: "…the program is not live and segmentation output remains in SHADOW mode";
   "There will be no impact as the maintenance is done one rack/node at a time. In case,
   if there is a client impact, the client apps need to switch to the other zone";
   "Low Risk, No business or consumer impact is expected… batch application";
   "No impact is anticipated… can handle trades with existing 8-digit account id";
   "If there are any batch abends… it may impact downstream FAST application jobs";
   "No impact is expected as current cert is still valid… Client Central functions".
 Report pass/fail per fixture first.

Report (live, awaiting approval; and history read live as before):
 1) Flags per grid (A, B) by stated Impact and class; % of assessments with Q6 answered.
 2) Incidents within 7 days (history) for flagged vs not flagged, per grid, with counts.
 3) Top 20 HARM phrases that caused flags, with counts; top 10 phrases skipped by (a)/(c).
 4) work/impact_review2.txt: 25 flagged (mix of grids, stated 3 and 4) and 10 near-misses
    (HARM found but skipped) — change id, stated, derived A/B, reach, restoration,
    the Q6 sentence that triggered (<=200 chars). No Q7 or other text. Do not print it.
 Recommend grid, phrase changes and severity. Then stop.