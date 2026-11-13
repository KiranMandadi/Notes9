Answers to your plan — then go.

A) .env.example line 55: replace the real Remedy host with a placeholder
   (https://remedy.example.com, same format as the docs). Touch nothing else in that file except
   adding CHANGELENS_SAVED_VIEWS.

B) Decision 1 changed: Clear all behaves exactly as today in both flag states (keeps approver
   and layout). Afterwards the picker shows "Default" if the result equals Default, otherwise
   "Default" + Modified. Decisions 2–6: agreed.

C) The board, as text (match exactly):

VIEW GROUP (right end of RISK row): divider 1px×24px #DDE3EC, 6px gap after it; label "VIEW"
(11px, 600, letter-spacing .7px, uppercase, #5B6880); picker 236×34px, radius 8, border 1.5px
#CFD7E3 (#E8B266 when Modified; #0E7C74 + ring 0 0 0 3px rgba(14,124,116,.15) when open),
bg #fff, padding 0 10px 0 12px, gap 8px: "▦" #5B6880, name 13px 600 #0B1B33 ellipsis, Modified
dot 7px #D97706, caret "▾" pushed right. Modified actions after the picker, gap 10px:
"Modified" 13px 600 #8A4B08, then buttons-as-links 13px #0E7C74 underlined: "Update" (saved
view only), "Save as…", "Reset" (#5B6880). Unavailable: picker bg #F4F6FA, text #8592A8, icons
#B9C3D3, plus an 18px round "i" (1.5px #8592A8) with tooltip.

MENU: right-aligned under picker, top 40px, width 360, bg #fff, border 1px #DDE3EC, radius 12,
shadow 0 16px 40px rgba(11,27,51,.18), padding 6px 0. Items: padding 9px 14px, 13px, hover
#F4F6FA. Row 1: "✓" (#0E7C74, 14px column) "Default" (600) + right "system defaults" 12px
#8592A8. Divider 1px #EEF1F6 (margin 6px 0). Label "MY VIEWS · SAVED IN THIS BROWSER"
(label style, padding 4px 14px). Each view: name, then summary 12px #8592A8 one line ellipsis.
Divider. "＋ Save current as…" and "⚙ Manage views…" (600 #0E7C74).

STATUS PILL MESSAGES: existing pill. green bg #E3F4EA fg #14532D border #9ED3B4 icon ✓;
info bg #EEF3FA fg #1C3358 border #C9D6EA icon ⓘ; amber bg #FDF0DC fg #6B3A06 border #E8B266
icon ⚠; red bg #FDE8E7 fg #7A1212 border #F3C1BC icon ⚠. "· Undo" underlined #0E7C74.

DIALOG BACKDROP: rgba(11,27,51,.42), dialog top 130px, centred.

SAVE VIEW DIALOG: width 520, bg #fff, radius 16, shadow 0 24px 60px rgba(4,12,28,.35),
padding 24, gap 16.
- Header: "Save view" 18px 600 #0B1B33; close "×" #8592A8 18px right.
- (At limit) banner: 13px #6B3A06 on #FDF0DC, border 1px #E8B266, radius 8, padding 10px 12px:
  "You have 20 views, the most this browser keeps. Delete one in Manage views to save another."
  ("Manage views" underlined, opens Manage). Name field and tags at opacity .45, disabled.
- "View name" 12px 600 #44516A; input 44px tall, radius 10, border 1.5px #0E7C74 + ring
  (focus), 14px; hint 12px #8592A8 "N / 40 characters". Duplicate: border #C2410C, ring
  rgba(194,65,12,.12), hint #A61B1B "A view called “X” already exists. Saving will replace it."
- "This view will remember" 12px 600 #44516A; tags 12px, padding 2px 8px, radius 999, bg #EEF1F6,
  #44516A, e.g. "Approver: Rama Bokka", "ORR: 4, 3", "Risk Level: 5, 4",
  "Status: Scheduled For Approval", "Class: All except Standard", "Date: Next 7 days (rolling)",
  "Layout: List" (only filters that differ from All, plus Approver, Status, Date, Layout always).
- Line 12px #8592A8: "Not saved: search text and results. Changes always load live from Remedy."
- Note box 12px #44516A bg #F4F6FA radius 8 padding 10px 12px: "ⓘ Saved in this browser on
  this computer only. Clearing browser data removes it. Use Manage views → Export to keep a copy
  or move it to another computer." ("Manage views → Export" bold).
- Safari only: amber box (as banner) "Safari may clear saved views if you don't open ChangeLens
  for 7 days — use Export to keep a copy."
- Buttons right, gap 10, 36px tall, radius 8, 13px 600, padding 0 16: "Cancel" (white, border
  #CFD7E3, #1C2A42) and "Save view"/"Replace view" (#0E7C74, white); disabled #E6EBF2/#8592A8.

MANAGE VIEWS DIALOG: width 740, same card style, gap 14.
- Header: "Manage views" 18px 600 + "N of 20 · A–Z" 13px #8592A8; "×" right.
- List: border 1px #E6EBF2, radius 10. First row (bg #F8FAFC): "Default" 600, tag "System",
  "System defaults · always available · can't be changed" #8592A8. Each view row: padding
  12px 14px, border-bottom #EEF1F6, 13px: name 600, summary #5B6880 one line ellipsis; right:
  "Saved D Mon" 12px #8592A8, "Rename" (#0E7C74), "Delete" (#B42318), as link-buttons.
- Rename: inline input 36px, border 1.5px #0E7C74 + ring, hint 12px #8592A8 "Enter to save ·
  Esc to cancel", "Save" button (32px teal) + "Cancel" link #5B6880.
- Delete confirm: row bg #FFF6F5, text #7A1212 "Delete “X”? It's removed from this browser."
  ("Delete “X”?" bold), buttons "Delete" (#B42318 white, 32px) and "Keep" (white bordered).
- Newly imported rows: bg #F3FAF6 briefly.
- Message pill inside dialog (same colours as status pill, 32px).
- Footer (border-top #EEF1F6, padding-top 10): "⤓ Export views", "⤒ Import…" (white bordered
  buttons); right note 12px #8592A8 max 340px: "Saved in this browser only. The exported file
  includes the approver names in your views." + Safari line when Safari.
- "Done" button bottom right (white bordered).

go