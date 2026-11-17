Impact understated: measurement round 2. READ-ONLY, same constraints. Delete
work/impact_review2.txt first (it contains attestation text).
Use Grid B. Changes to the helper classifier:
 1) Q6 extraction stops at the next CAB heading (Q7 attestation etc.); never read Q7 text.
 2) Per-sentence: skip a sentence that contains a no-impact statement — add "no (direct|
    end) users impacted", "no users are (using|impacted)", "without (any )?impact".
 3) Skip benefit/outcome sentences: "expected outcome", "improves", "reduce(s|d) (the )?
    risk", "prevent(s|ion)", "will help", "benefit".
 4) Skip consequence-of-not-doing sentences: "if (the|this) change is not (implemented|
    done|approved)", "if (it|this) is not done", "we (would|will) not be able to",
    "will (expire|be inoperable) when", "otherwise".
 5) Not people: "consumer(s) of", "downstream consumers", "service consumers",
    "<system> consumers" where <system> is one word ending in service/api/app.
 6) Reach D only with customer words (client(s), customer(s), investor(s), account
    holder(s), consumers as people) or business functions (trading, trade confirm(s),
    settlement, payment(s), money movement, T+1). Plain "user(s)" -> C, never D; tool
    users ("<x> console users", "<x> users" where <x> is an internal tool) -> C.
 Fixtures: the 8 from round 1 must still pass; add as NO FLAG: "expected outcome is
 continued secure https availability… reduced risk of client/internal access disruption";
 "improves business user productivity and reduces interruption risk"; "there will be no
 direct users impacted by the password change"; "this may result in delay in batch
 impacting downstream consumers of this file"; "affected client tax applications will be
 inoperable when certificate issued last year expires"; "no business impact… but if the
 change is not implemented, we will not be able to…". Add as FLAG (C or D): "eligible ssp
 clients may be unable to receive a wsj redemption code if the load fails"; "settlement
 obligations, fails, and gencash postings will not be processed systematically".
Report: fixtures pass/fail; live and history flags (B) before -> after; reach D vs C;
work/impact_review3.txt with ALL flagged rows (live + history, Q6 sentence only, <=200
chars, no Q7 text, no names). Then stop.