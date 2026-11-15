0.52.1 additions (same release as the Exec Summary fix; baseline still NOT updated).
Constraints unchanged: never read/search/print cr_core/config.py, cr_core/history/config.py
or .env; no Remedy writes; no crq login; no git; no inline Python (-c/stdin/heredoc) —
scripts in a file under work/, deleted after; do NOT run --update-baseline; history.db
schema unchanged, no people stored; chat shows codes, counts and task names only — no
change numbers, people names or note text. Keep work/execsummary_spotcheck.txt.

A) CC-06 (change window length)
   - Severity -> advisory (0 points). Threshold stays 8 h in config (window_max_duration).
   - limit_note: "History shows more problems above 8 h for non-mainframe changes; no
     office limit."
   - Skip entirely when ANY of:
     (a) all usable implementation tasks pass CC-10;
     (b) no usable implementation task and the change window itself is inside the allowed
         hours (the CC-10 fallback passes);
     (c) Type of Window = Specialized and the window is 24x7 or allows > 24 h continuously;
     (d) a window exception is recorded (CC-10 exception Work Detail types);
     (e) the existing reason-in-Notes / Deployment strategy / Backout plan exemption.
   - Message: "Change window is <duration>, longer than <threshold> h." Neutral wording,
     no "ChangeLens flags".
   - Update open-items D24 (no office limit; advisory only).

B) CV-13 (stale tasks) message
   - One line: "<n> tasks are entirely outside the change window (<window, ET>)."
   - Then one entry per distinct task: task name and ET times, each with exactly one
     "View task n" link (n = Remedy sequence). Every listed task gets a link; no duplicate
     links; no repeated window text; no truncated "is…".

TESTS
   - CC-06: advisory severity; skip cases (a) (b) (c) (d) (e) each; still shown for an
     Authorized change whose implementation task fails CC-10 and window > 8 h.
   - CV-13: 3 stale tasks incl. two with the same name -> 3 entries, 3 unique links, one
     header line.
   - Existing tests stay green; do not weaken any.

DOCS: rules docs / regenerated catalogue, user-guide if it mentions 8 h, open-items D24,
CHANGELOG 0.52.1 (add to the existing entry). Version stays 0.52.1.

VERIFY: ruff; full test suite; scripts/check.py --browser --audit (0 mismatches apart from
the expected baseline step; report the new rule set id).

MEASURE (built code, same scope as the window check: profile groups, Scheduled Start
2026-08-17 to 2026-12-15, Cancelled/Rejected skipped):
   - CC-06: before (Minor) -> after (advisory shown / skipped by a, b, c, d, e).
   - Verdict changes caused by A (Needs work -> Ready, Blocked -> Needs work, any worse).
   - CV-13: count unchanged before/after (message only).
Report files changed, test counts, audit result, rule set id and the measurement; then stop.