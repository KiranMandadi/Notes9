Option 1: profile the build (python -m cProfile on crq timing, output to work/), speed it up where possible, and warm the history pool at Console start. The in-memory history must reload automatically when history.db changes (check its modified time before each use) so it is never stale after crq-load refresh; never hold Remedy data in memory. For before/after, use the Console's own steps log (5+ runs per change, median per step), not crq timing, and repeat the baseline if Remedy is slow at the time.

git status
git add -A
git commit -m "Report speed: reuse Remedy sign-in, batched overlap queries, history indexes"
git push