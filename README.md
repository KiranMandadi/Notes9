Build: "Impact may be understated" advisory (0.53.0, same release; baseline NOT updated).
Usual constraints. Delete work/impact_review3.txt first. Verification level: UI (ruff,
tests for the changed modules, browser tests -k review only). No full suite, no audit.

Logic = round-2 helper (Grid B, per-sentence skips, Q6 cut at next CAB heading and at
attestation wording) with these changes:
 1) Flag ONLY reach D (customer words or business functions: client(s), customer(s),
    investor(s), account holder(s), trading, trade confirm(s), settlement, payment(s),
    money movement, T+1, statements). Reach C never flags.
 2) More consequence-of-not-doing skips: "if (the |this )?(crq|change) is not
    (approved|implemented|done)", "if the jobs were not on hold".
 3) Skip sentences that end with "?" (template sub-questions).
 4) Not people: "upstream consumers", "downstream consumers", "<x> consumers" (any),
    "internal ... consumers"; skip sentences with preproduction / pre-production /
    non-prod / sit / uat environments.
 5) Flag when derived (Grid B) < stated Impact number. Not for Standard/Latent/Emergency,
    Cancelled/Rejected, Internal entries, history replay.

Rule: next free id in team-validation, ADVISORY (0 points), title "Impact may be
understated". Message: 'The Change Assessment describes customer impact ("<sentence,
<=160 chars>") with restoration up to <time>; this suggests Impact <n> – <label>, but the
change states <m> – <label>. Confirm the Impact level, or explain why it is lower.'
Never include Q7 text or names. Link "Searched: Work detail › Change Assessment" as for
CV-15. Phrase lists and grid in config (change_assessment.impact_check).

Tests: all 16 round-2 fixtures + new NO FLAG: "the client is impacted only during
implementation when the tool is down"; "swat applications will be temporarily unavailable
to the users during change window"; "if crq is not approved, we cannot validate the files
… bad client experience"; "if the jobs were not on hold, the reversals cannot be
validated…"; "how would an unexpected failure be recognized and what would the customer
experience be?"; "new query/save endpoints become unavailable to upstream consumers";
"preproduction users of sit_phx will not be able to update jobs". FLAG: "customers may not
be able to create/update/delete trusted contact"; "some customers won't be able to download
their statements/documents while the issue persists".
Docs: rule catalogue, user-guide (one paragraph), CHANGELOG 0.53.0.
Report: rule id, live flag count, and write work/impact_live.txt listing each live flag
(change id, stated, derived, sentence <=160 chars) for my review. Then stop.