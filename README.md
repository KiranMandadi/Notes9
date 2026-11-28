One more for 0.61.3: the field map (remedy_field_map.yaml) is ChangeLens config, not Remedy
data, so load it once per process and reuse it across changes and requests; reload it when
the file's modification time changes. Do the same for any other config file reloaded per
change (report which). Remedy data stays live and uncached. Results must stay byte-for-byte
identical; re-run the scoring time on the 571 changes and report before -> after. Same rules.


git add -A
git status
git commit -m "0.61.3: faster scoring, lighter Remedy load" -m "- Exec Summary parsed once per change and shared by Q-COMPLETE-10/11/12; each line
  normalised once
- Platform keywords found in one pass over the text
- Config files (field map) loaded once per process, reloaded when changed; Remedy data
  stays live
- Pending back to 4 parallel Remedy reads; back-off lowers to 2 on slow replies or 429/503
- Scoring 34 s -> ~17 s on 571 changes; results byte-for-byte identical; rule set 14e9b07d"
git push