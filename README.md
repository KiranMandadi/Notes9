Review landing page: compact search card on the right (mock-up "Review landing - search card (proposed)", option B), plus a ChangeLens favicon. Same standing rules from .github/copilot-instructions.md (including Running commands); no git operations unless I ask. If you ask me something and get no answer, stop and wait. UI only; rule set id unchanged — confirm it.

Keep unchanged — do not touch, replace or restyle: the ChangeLens logo and top navigation; the "CHANGE QUALITY CONSOLE" eyebrow, headline and subtext wording; the three points row ("Straight from Remedy", "Rules decide, history informs", "Ready in seconds") with its current text, icons and style; and the footer with the Technical details toggle. Only the search area changes, plus the favicon below.

1. Hero becomes two columns inside the navy band (same 1360 px page width): left = eyebrow, headline, subtext (unchanged); right = a 440 px search card, vertically centred against the text, 64 px gap. Remove the full-width search panel.
2. Search card: white, 16 px radius, shadow 0 24px 60px rgba(4,12,28,0.35), padding 26px.
   - Title "Review a change" (18 px, 600, #0B1B33); line under it "Enter the change number to see its quality report." (13 px, #5B6880).
   - Label "Change number" (12 px, 600). Input 48 px tall with the existing "CRQ" prefix block, IBM Plex Mono 16 px, placeholder 000002484053. Focus: 1.5 px #0E7C74 border + 3 px rgba(14,124,116,0.15) ring.
   - Status line under the input (12 px), keeping today's validation and paste/normalising logic: empty "You can paste the whole number, including CRQ." (#8592A8); valid "✓ CRQ<12 digits>" (#1E6B45); "Numbers only" / "Up to 12 digits" (#A61B1B, input border #C2410C).
   - Full-width button "Review change →", 46 px, 10 px radius: teal #0E7C74 with white text when valid (hover #0B5F59), #E6EBF2 / #8592A8 and disabled otherwise. Enter submits when valid.
   - Footer line, centred, 12 px #8592A8: "Read live from Remedy · nothing in Remedy is changed".
3. Autofocus the input on page load; "/" still focuses it if it does today.
4. The three points row sits on the light background directly under the hero, as today.
5. Narrow screens (< 1024 px): stack — text first, then the card at full width (max 480 px), then the points.
6. Favicon: use the existing ChangeLens logo mark (the icon part of the header logo, same shape and colours — do not redraw it) as the browser tab icon on every Console page (Review, Pending, Rules, reports, overlay pages). Provide favicon.svg plus 32 px and 16 px PNG fallbacks and a 180 px apple-touch-icon, served from the static folder with the existing cache-busting, and referenced from every page's <head>. Make sure it is clearly visible on light and dark browser tabs.
Tests: card present and 440 px at 1440/1920; status line and button states (empty, valid, letters, too long, pasted "CRQ000002484053"); Enter submits only when valid; layout stacks under 1024 px; points row, logo and footer unchanged; every page's <head> links the favicon and the files are served (200). Update screenshots, user-guide; CHANGELOG (no new version). Run the browser tests with pytest; report counts and the rule set id.
No branches, tags or commits.


git status
git add -A
git commit -m "Review landing: compact search card beside the headline; ChangeLens favicon"
git push