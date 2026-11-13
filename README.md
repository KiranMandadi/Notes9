Pending table, Quality column only: score number to 13px, font-weight 600, colour #1C2A42,
line-height 1.2, font-variant-numeric: tabular-nums. Pill below and its 4px gap unchanged,
centring unchanged. Pending table only. Update any test that checks the score size; run only
the Pending browser tests for the Quality column. Report counts, then stop. No git.

git status
git diff --stat
git add -A
git status
git commit -m "0.48.0: Saved views on the Pending page (flag, off by default)" -m "- New flag CHANGELENS_SAVED_VIEWS (default false in .env.example); off = Pending unchanged, no browser storage
- View picker at the right end of the Risk row; Default plus up to 20 views saved in the user's browser
- Save as, Update, Reset, Rename, Delete with Undo, Replace on duplicate names
- Import/Export (JSON, validated, 100 KB max); damaged or blocked storage handled safely
- Modified detection with no false alarms; values no longer in config skipped with a message
- Rolling date presets in ET; past custom ranges flagged
- Safari 7-day storage note; inline SVG icons for consistent rendering across browsers
- Pending table: Window and Quality pills share one size/style; SVG ticks in the status pill
- crq doctor shows Saved views on/off
- .env.example: real Remedy host replaced with a placeholder
- Copilot instructions: no command-line or stdin Python
- Docs, SECURITY.md, CHANGELOG (0.48.0) and tests updated"
git push