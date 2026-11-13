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
- crq doctor shows Saved views on/off
- .env.example: real Remedy host replaced with a placeholder
- Copilot instructions: no command-line or stdin Python
- Docs, SECURITY.md, CHANGELOG (0.48.0) and tests updated"
git push