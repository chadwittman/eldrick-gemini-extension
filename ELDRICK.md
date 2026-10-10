# ELDRICK golf club fitting

The `eldrick` MCP server fits golf clubs. It covers drivers, fairway woods, hybrids, irons and wedges, not putters. It returns specs matched to real heads, shafts and grips. Built on 100,000+ fittings: trained on 80,000, plus 25,000+ ELDRICK has done itself.

The first time you use it, run `/mcp auth eldrick` and sign in with an ELDRICK account. A new email gets an account with a 6-digit code.

## Running a fitting

- `analyze_fitting` needs three things:
  - the club type: `driver`, `fairway`, `hybrid`, `iron` or `wedge`
  - the golfer's handedness
  - a swing speed or ball speed measured with that club (7-iron speed for irons)
- If any of these is missing, ask for it. Don't guess.
- Pass along anything else the golfer shares: height, wrist-to-floor, handicap, launch, spin, attack angle, carry, miss pattern and current clubs.
- Each fitting uses one of the account's included fittings, and every account includes 10 a month. Send an `idempotencyKey` so a retry doesn't use a second one.
- Keep the returned `fittingId`. `get_fitting` brings the fitting back later, and `score_clubs` and `build_store_link` can build on it.

## Free tools (no fitting used)

- `search_clubs`
- `get_club`
- `compare_clubs`
- `score_clubs` ranks clubs 0 to 100 for a swing.
- `build_store_link` returns a store.eldrick.com product page with the fitted build listed. It never checks out or reserves anything.
- `check_key_status` shows fittings left this month.

## Presenting results

Show the recommended specs first, then the matched heads, shafts and grips, then the fitting ID. Credit results as "Fit by ELDRICK".
