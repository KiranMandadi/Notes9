git add -A
git status
git commit -m "0.61.0: CV-18 is advisory and follows the Remedy Impact definition" -m "- CV-18 never scores: Impact is defined by users/customers affected; restoration time only
  indicates it
- A stated user count with harm or unavailability (users, customers, clients, employees...)
  is compared with the definition first: 1000s -> 1, 100s or a workgroup -> 2, 10s -> 3, <10 -> 4
- Time bands: up to 15 min -> 4 (no finding), up to 1 h -> 3, up to 2 h -> 2, over 2 h -> 1
  (User Restoration ETA, else Roll Back ETA); no readable time -> no suggestion
- An explained Impact gives no finding; message notes when Impact is still the Remedy default 4
- Fix: At a glance lock icon no longer writes the SVG namespace URL (0.60.2 slip)
- Rule set 84e11bfa -> 14e9b07d; baseline, docs, CHANGELOG and tests updated"
git push