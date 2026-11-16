Keep as built (option 1): the new deployment words are correct; a deployment that names no
version should be flagged. Before finishing: add all 70 newly added GEN-01 changes to
work/execsummary_spotcheck.txt (change id, Summary <=100 chars, which trigger word matched),
plus the 2 changes that moved Needs work -> Blocked with every finding that changed on them.
If any trigger word fires on non-deployment text (e.g. "Version: N/A", "rebuild", "build
index"), tighten that word (whole-word / deployment context) and report the new counts.
Then finish the build steps and stop.