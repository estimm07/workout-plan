# Full Body 3x/Week — 8-Week Plan (approved spec)

Status: **built into the app** as the `full-body` plan in `index.html`. This file remains the source of truth for its content.

Based on our earlier Full Body draft merged with a reel by @darrenliufitness ("Busy job? Kids? No problem"):
3 full-body days, 2–3 working sets of 5–15 reps, add a little weight each week, finish with core, under 50 minutes.

## Schedule

| Mon | Tue | Wed | Thu | Fri | Sat | Sun |
|---|---|---|---|---|---|---|
| **Full Body A** | Active recovery + incline walk | **Full Body B** | Active recovery + incline walk | **Full Body C** | Optional | Full rest |

The 10-minute incline-walk finisher moves to Tue/Thu so training days stay under 50 minutes.
Active recovery: 20–25 min walk at 3–5% grade, or 15 min mobility.

## Phases

| Weeks | Phase | Main lifts (first 3 slots of each day) | Accessories | Effort |
|---|---|---|---|---|
| 1–3 | Foundation | 2 × 12–15 | 2 × 12–15 | RPE 7, form first |
| 4–6 | Build | 3 × 8–12 | 3 × 10–12 | RPE 8 |
| 7–8 | Strength | 3 × 5–8, rest 2 min | 3 × 10–12 | RPE 8–9 |

Progression: double progression. Hit the top of the rep range on every set, then add weight
(5 lb with dumbbells; smaller jumps where equipment allows, as in the reel's "at least 1 lb a week").

## Equipment setups (chosen per workout)

Each slot has a version per setup. The setup is picked on the Start Workout screen for that
workout (default: the last one used) and recorded with the workout.

- **Home** — dumbbells, adjustable bench, pull-up bar, bands. Our merged version.
- **Home + KB** — same, with kettlebell versions where listed.
- **Gym** — the reel's exact exercises.

Different movements keep separate PR histories (e.g. Hack Squat vs Goblet Squat).
Same-movement swaps share one history (e.g. DB Row and KB Row).

### Day A

| Slot | Home | Home + KB | Gym (reel) |
|---|---|---|---|
| Squat | Goblet Squat, heels raised | KB Goblet Squat | Hack Squat |
| Push | Incline DB Press | Incline DB Press | Incline DB Press |
| Pull | Chest-Supported DB Row | Chest-Supported DB Row | Machine Row |
| Glutes | DB Hip Thrust | DB Hip Thrust | DB Hip Thrust (not in reel; kept for glutes) |
| Shoulders | Lateral Raise | Lateral Raise | Lateral Raise |
| Core finisher | Pallof Press (band) | Pallof Press (band) | Pallof Press (cable or band) |

### Day B

| Slot | Home | Home + KB | Gym (reel) |
|---|---|---|---|
| Hinge | Light DB RDL | KB Deadlift | Romanian Deadlift |
| Push | Seated DB Shoulder Press | Seated DB Shoulder Press | Shoulder Press |
| Pull | Pull-Ups (band-assisted if needed) | Pull-Ups | Lat Pulldown / Pull-Up |
| Legs | Walking Lunges (DB) | Walking Lunges (KB) | Walking Lunges |
| Arms | Overhead DB Tricep Extension | Overhead DB Tricep Extension | Tricep Extensions |
| Core finisher | Dead Bug | Dead Bug | Dead Bug |

### Day C

| Slot | Home | Home + KB | Gym (reel) |
|---|---|---|---|
| Single leg | Bulgarian Split Squat | Bulgarian Split Squat | Split Squat |
| Push | DB Chest Fly (bench) | DB Chest Fly | Chest Fly |
| Pull | One-Arm DB Row | KB Row | Chest-Supported Row |
| Arms | Incline DB Curl | Incline DB Curl | Incline Bicep Curls |
| Rear delts | Band Reverse Fly | Band Reverse Fly | Reverse Pec Deck |
| Core finisher | Suitcase Carry (DB) | Suitcase Carry (KB) | Suitcase Carry |

## Every training day

- Warm-up (5 min): cat-cow, glute bridges, band pull-aparts, bodyweight box squats.
- Main work: the 5 slots above.
- Core finisher (5 min): the day's core slot.
- Optional: pre-workout heating pad / foam roller, post-workout foam roller (and ice if the back is irritated).

## Lower-back care

- Only one hinge a week (Day B), kept light and controlled; stop at mid-shin, neutral spine.
- No conventional deadlifts, no kettlebell swings.
- Shoulder press seated with back support.
- Stop any exercise that causes back discomfort; swap to the Home version or skip the set.

## Build notes for the app

- Use the row-based plan format (`finalizeRowPlan`) in `index.html`; reuse existing exercise ids where
  the movement matches the current plan (e.g. `bench-press`, `hip-thrust`, `rdl`, `bss`, `pullups`,
  `shoulder-press`, `chest-row`, `lat-raise`, `dead-bug`, `goblet-squat`) so PRs carry over.
- Generalize the existing kettlebell `kb`/`kbWeeks` row fields into per-setup versions
  (`home`, `kb`, `gym`), each with its own `ex` id when it is a different movement.
- Add a Home / Home + KB / Gym picker to Start Workout; store the choice per workout
  (e.g. a preference key per week and day) and show it in the workout log.
- `extraSets` and per-phase `targets` follow the Phases table above (2 sets in weeks 1–3, 3 after).
- Add form cues (`EX_INFO`) and muscle groups (`MUSCLE_MAP`) for every new exercise.
