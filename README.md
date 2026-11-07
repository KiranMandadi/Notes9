Pending: rename the first View by tab label from "ORR" to "Operational Risk Rating (ORR)". Keep the short "ORR" everywhere else: the "Grouped by ORR" caption, the table column header, the sort label, the cards ("4 – Very High"), the compact sticky header and the URL value (view=orr). Add a tooltip "Operational Risk Rating" on the ORR column header. Check the tab row still fits on one line at 1280 px and wraps cleanly on phone. Update tests and CHANGELOG (no new version). Run the browser tests; report counts. No branches, tags or commits.

git status
git add -A
git commit -m "Pending: remove Viewed; Review Decision pill wording; only Open opens a report; spell out Operational Risk Rating (ORR)"
git push