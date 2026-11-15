Window discovery, part 2. Read-only. Same constraints as before (no config.py/.env, no
Remedy writes, no repo changes, scripts under work/ deleted after, codes/counts/values only).

1) SCHW:CHG:TemplatizeFields: describe the row structure for Specialized Windows entries
   (field names/ids for platform, window name, status, per-weekday start/end, time zone,
   any notes/effective dates). Show the full rows for the 36 Platform x Specialized
   Windows pairs used in the discovery, as a table: platform, window, Mon..Sun start-end,
   time zone. Flag rows whose end is earlier than start (overnight) and any "24x7"/blank.
   Also check whether an "Authorized" definition exists on this form or elsewhere.
2) Window exception fields: Window Exception (800000980), ztmp_WindowExceptionFlag
   (800000986), ztmp_WindowExceptionCount (800001516), ztmp_WindowExceptionWorkLogCount
   (800001518): type, menu values, and counts by value over the same 4,867 changes, split
   by Type of Window. Also count Work Detail entries of types Restriction Approval Notes /
   Restriction Exception on those changes, and how they line up with these fields.
3) Report how the Remedy form itself uses these (any active links/filters visible via
   metadata that set the exception flag), only if readable without admin rights.
Then stop.