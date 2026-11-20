0.57.0 polish: Freeze pill icon.
Add a small inline SVG lock before the "Freeze" pill text wherever the Freeze pill appears
(Pending Window column, Review, overlay). Same size, stroke, colour and spacing as the
awareness triangle: viewBox 24, stroke currentColor, stroke-width 2, round caps/joins,
fill none:
  rect x=5 y=11 width=14 height=9 rx=2
  path M8 11V8a4 4 0 0 1 8 0v3
Icon and text vertically centred, same pill height as today. "Freeze · exception" stays
text-only (grey). Tooltip, colours, order and logic unchanged. No other change.
Extend the existing pill browser test: the Freeze pill contains the lock icon; the
Freeze · exception pill contains no icon.
Verification: ruff; browser -k pending and -k review. Ground rules as before; any heredoc,
python -c or python - is a stop condition.