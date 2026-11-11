Two small follow-ups. Same standing rules; no git operations unless I ask.
1. Old quality notes files that still contain a "questions" key: ignore that key silently instead of rejecting the file with INVALID_NOTES. Any other unknown key is still rejected as today. Add a unit test (notes file with "questions" loads fine; one with another unknown key still fails).
2. Rename the test test_back_to_top_on_every_long_page_and_in_the_overlay_and_no_question_for_the_owner: split it into two clearly named tests — test_back_to_top_on_every_long_page_and_in_the_overlay and test_report_has_no_question_for_the_owner — same assertions, no behaviour change.
Tests: UI tier — ruff, the notes unit tests, and the two browser tests by name. CHANGELOG: no entry needed for the test rename; one line under 0.46.0 for item 1.
No branches, tags or commits.

git status
git add -A
git commit -m "Remove Question for the owner from the report; ignore legacy questions key in notes"
git push