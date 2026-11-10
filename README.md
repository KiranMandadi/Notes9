"Open in Remedy" deep link. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI only; rule set id unchanged — confirm it at the end. Never read .env; I will add the setting myself.

1. New optional setting REMEDY_CHANGE_URL_TEMPLATE (read with the other settings): a URL with a {crq} placeholder. Document it in docs/setup-enterprise.md and the .env example with a placeholder host (no real host names in the repo). If unset or without {crq}, no links are shown anywhere.

2. Build links only for a validated change number (^CRQ\d{12}$), URL-encoding it into the placeholder; anything else → no link. No credentials, tokens or session ids in the link; do not log the generated URLs.

3. Report header (full page and Pending overlay): "Open in Remedy ↗" link right after the change number and its copy icon (13 px, #9FD0CA on the navy header, underlined on hover). target=_blank, rel="noopener noreferrer", title "Opens this change in Remedy in a new tab — approve or reject from its Approvals section".

4. Pending list: a small ↗ icon next to the copy icon after the change number, shown only on row hover/focus; same link, target, rel and title. Not on calendar bars or the Executive brief.

5. Opening the link must not affect the Console tab: the overlay, Pending state and recorded Review Decisions stay as they are.

Tests:
   - link built from a template with a sample host;
   - no link when the setting is unset, has no {crq}, or the number is malformed;
   - encoding of the number;
   - target and rel attributes and title text;
   - Pending ↗ hidden by default and shown on hover/focus;
   - overlay stays open after clicking the link.
Update user-guide and CHANGELOG (no new version). Run all tests with pytest; report counts and the rule set id.
No branches, tags or commits.


Add this line to .env yourself, locally and on the VM, with your real host and no cacheid:
   REMEDY_CHANGE_URL_TEMPLATE=https://<your-host>/arsys/forms/onbmc-s/SHR:LandingConsole/Default+Administrator+View/?mode=search&F304255500=CHG%3AInfrastructure+Change&F1000000076=FormOpen&F303647600=SearchTicketWithQual&F304255610=%271000000182%27%3D%22{crq}%22


   git status
   git add -A
   git commit -m "Open in Remedy deep link from the report header and Pending rows"
   git push