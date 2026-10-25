# Zimbabwe RTA Tracker

A public tracker of confirmed road traffic accidents in Zimbabwe, manually recorded
with full sourcing. The goal is to turn careful records into dashboards and evidence
that can convince leadership to act on road safety.

## The standard (locked)

1. **Confirmed means published by the ZRP Twitter handle or in a newspaper.**
   The person logging an accident enters it only after it is confirmed.
2. **One record per incident.** If ZRP and a newspaper both report the same crash,
   it is one row with two sources — never two rows.
3. **Headline stats count confirmed records only.** Anything marked
   `verified=no` is kept out of totals and charts.
4. **Unknown stays blank — never a guessed zero.** A blank fatality or injury
   count means "not reported", not "nobody died".
5. **Coverage log.** `data/coverage.csv` records which days and provinces were
   actually monitored, so "no accidents recorded" is never confused with
   "nobody was watching".

## How to add an accident

1. Open `data/accidents.csv` on GitHub and edit it (pencil icon).
2. Append one row per accident, following the header columns.
3. Fill in only what the source actually says; leave the rest blank.
4. Commit with a message like `Add accident: Harare, 2026-10-26`.

### Field notes

- `location_type`: `intersection`, `main_road`, or `other`.
- `controlled_intersection`: `yes` / `no` (only when `location_type` is
  `intersection`; otherwise leave blank).
- `dual_carriageway`: `yes` / `no` (only for main roads; otherwise blank).
- `speed_limit_kmh`: the speed limit around the area, if known.
- `suspected_cause` (fixed list): `speeding`, `reckless overtaking`,
  `drunk driving`, `vehicle defect`, `road condition`, `pedestrian-related`,
  `weather`, `fatigue`, `other`, `unknown`.
- `source_type`: `ZRP Twitter` or `newspaper`.
- `verified`: `yes` for confirmed records; `no` keeps a row out of the totals.

## The website

`index.html` is a static page that reads `data/accidents.csv` and renders the
dashboards: totals, breakdowns by province and by suspected cause, and the full
incident table. Every edit to the CSV updates the site automatically once
GitHub Pages is enabled (Settings → Pages → Deploy from branch → `main`).

## What this is not

This is a record of *reported and confirmed* accidents, not a claim to count
every accident in Zimbabwe. Underreporting is real, and every chart on the site
says so.
