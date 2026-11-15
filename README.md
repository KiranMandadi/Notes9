Guide polish (0.51.0). UI only.

1) Pending miniature: eyebrow "CHANGES" (not "PENDING APPROVAL"), matching the real page.

2) Pending miniature realism: chips show values like the real page — RISK: "ORR 4 – Very High,
   3 – High", "Risk Level 5, 4, 3", "Impact All", "Quality All"; SCOPE: "Status Scheduled For
   Approval", "Class All except Standard", "Date Any", "Group All", "Approver A. Approver";
   active ones with the teal outline. Replace "2 changes loaded" with the real green status
   message style "✓ Updated 09:24 · 2 changes". Keep hotspot positions on the right elements.

3) Glossary: lay out as rows of two (grid with aligned rows: ORR | Risk Level, Freeze |
   Advisory, Stale task | Step) so each pair shares a top edge.

4) Data handling tiles: identical internal layout — icon, title and text top-aligned
   (align-items: start), same padding; icons and titles on one line across all four tiles.

5) Report miniature: give "Compared with past changes" and "Full change details" the same
   layout as the Issues card — white card, bold heading row, then one row per item (gap 7px):
   - Past changes: heading "Past changes · 42 similar"; rows with a neutral grey pill label
     (same pill size as Major/Minor, min-width so labels align) + text:
     Start | Usually 21:00 · Window | 2× the usual length · Approvals | About 3 days
   - Full change details: heading "Full change details"; rows "› Summary and notes",
     "› Tasks  6", "› Work detail  4", "› Relationships  2" (chevron and count muted).
   Re-place the hotspot numbers so each sits on the top-left of its block (Verdict, Issues,
   Past changes, Full change details on the left; At a glance on the right; Score on the ring).

6) Sections 01 and 03: the numbered list on the right has a visible vertical divider from
   the miniature — border-left 1px solid #DDE3EC, padding-left 22px, running the full height
   of the section content (align-self: stretch). Same on both sections.

Check at 100% and 110%. Run the Guide browser tests and ruff only. Report files and counts;
then stop. No git.