# Post-mortem — 2026-09-18 → 2026-09-19

## What worked
- Scout-cleared liquid entries (JUP, WIF, Fartcoin, BONK, POPCAT) beat fresh snipes.
- Holding JUP/WIF into green tape captured real mark-up.
- Banking process > gambling narratives.

## What failed / cost edge
1. **Fartcoin early full exit at +4%** — Should have trailed and kept the runner while adding BONK/POPCAT from SOL dry powder.
2. **Double ~$5 SOL send** — Retry routine raced live send.
3. **Phantom auth downtime** — Blocked trail exits/adds when tape moved.
4. **Inventory thinking** — Sold a winner to make room instead of spending dry powder.

## Forward ops
- Trail open: JUP, WIF, BONK, POPCAT.
- Check this file + `desk/rails.md` before inventing new rules.
- Cache market notes under `markets/` to save usage.
