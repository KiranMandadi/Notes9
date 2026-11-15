Diagnosis and measurement only (same 0.52.1 work; baseline still not updated). Usual
constraints; codes, counts and CI counts only — no change numbers, host names or note text.
1) INF-01: explain how it decides the hosts/CIs are "not named" (fields searched, how the
   CI list in the message is built). Why does the message list related CIs while saying
   none are named? Show file/function names.
2) Measure (live scope as the window check, Cancelled/Rejected skipped): INF-01 hits;
   of those, how many have >= 1 related Configuration Item with status not Disposed/
   Retired; how many have none. Simulate: pass when a usable related CI exists, else the
   current text check. Majors cleared / added.
3) Disposed or retired CIs related to changes: count of changes; is there an existing rule?
4) Certificate rule (the "expiry date, chain and endpoints" Major): how is the Certificate
   platform detected (which categorization fields/values)? For the hits, the categorization
   values that triggered it, with counts. How many are patching/OS changes where
   certificate is only one of several categorizations? Propose how to avoid misfires.
5) Propose fixes for 2-4. Then stop.