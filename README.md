0.54.1: CV-15 severity by question importance (baseline NOT updated). Quick level.
Constraints unchanged; no git.
Config (change_assessment): core = [2 Deployment Strategy, 4 Roll Back Type and ETA,
5 User Restoration ETA, 6 Business Impact, 7 Attestation]; supporting = [1 Justification,
3 Deployment Type, 8 Deferral Y/N, 9 Deferral justification]; major_if_total_gaps >= 3.
CV-15 (missing or unanswered questions, one finding): Major if any core question is a gap
or total gaps >= 3; otherwise Minor. Same lifecycle (advisory once Scheduled). Message
unchanged except severity. CV-14 unchanged.
Tests: only Q9 missing -> Minor; Q1+Q3 -> Minor; Q1+Q3+Q8 -> Major; Q6 alone -> Major;
Q5 alone -> Major. Measure live (awaiting approval): CV-15 Major -> Minor count; verdict
changes. CHANGELOG 0.54.1; pyproject 0.54.1. Report rule set id. Then stop.