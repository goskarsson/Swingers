# Swingers Golf 2026

Live dashboard for the Swingers golf group — stableford net scoring, best-8-of-18 rounds rule.

🔗 **Live site:** `https://<your-username>.github.io/<repo-name>/`

---

## Deploying to GitHub Pages

1. Create a new repository on GitHub (e.g. `swingers-golf`)
2. Upload the contents of this `github-publish/` folder to the repository root
3. Go to **Settings → Pages**, set Source to `main` branch, folder `/root`
4. The site will be live at `https://<your-username>.github.io/swingers-golf/`

---

## Adding a new round

Open `index.html` and `player.html` in a text editor. Find and update three sections:

### 1. Add the week to WEEKS_2026
```js
const WEEKS_2026 = [
  {id:"V1", label:"Vika 1", date:"21.5.2026", course:"Hvaleyrarvöllur"},
  {id:"V2", label:"Vika 2", date:"28.5.2026", course:"Hvaleyrarvöllur"},
  {id:"V3", label:"Vika 3", date:"4.6.2026",  course:"Hvaleyrarvöllur"},  // ← add new week
];
```

### 2. Add stableford scores to SCORES_2026
```js
const SCORES_2026 = {
  "Biggi": {V1:19, V2:26, V3:31},   // ← add score for new week
  ...
};
```

### 3. Add hole-by-hole data to HOLE_DATA (for player stats + gross table)
```js
const HOLE_DATA = {
  "V3": {
    "Biggi": {
      s: [5,4,4,3,4,3,5,4,4, 4,4,3,5,4,4,5,3,4],  // gross scores per hole
      p: [3,3,2,1,3,2,2,2,3, 3,1,2,2,2,3,1,0,3]   // net stableford per hole
    },
    ...
  }
};
```
`s` = gross strokes on each hole (18 values).  
`p` = net stableford points per hole (0=double bogey or worse, 1=bogey, 2=par, 3=birdie, 4=eagle).

---

## Bikar (Cup) — recording match results

The cup bracket auto-populates seeds from the standings after week 4. When matches are played, update `BIKAR_RESULTS` in `index.html`:

```js
const BIKAR_RESULTS = {
  QF: [
    [34, 28],      // Seed 1 beat Seed 8 — scores this week
    [null, null],  // not yet played
    [null, null],
    [null, null],
  ],
  SF: [[null, null], [null, null]],
  F:  [null, null],
};
```

---

## Course: Hvaleyrarvöllur

| Hole | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 |
|------|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|----|----|----|
| Par  | 5 | 4 | 4 | 3 | 4 | 3 | 5 | 4 | 4 |  4 |  4 |  3 |  5 |  4 |  4 |  5 |  3 |  4 |

Total par: 72

---

## File structure

```
github-publish/
├── index.html       Main dashboard (standings, stat cards, bikar bracket)
├── player.html      Individual player page (season chart, hole stats)
├── SwingersLogo.jpg Club logo
└── README.md        This file
```
