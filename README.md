## Workout Tracker

A minimalist, Apple-style web app for logging workout sessions. Runs as a single HTML file directly in the browser, with no build process or external dependencies.

## Features

- **Day view with navigation**: Move between days using arrow buttons, jump back to the current day with the "Back to today" button. You can't navigate into the future.
- **Add exercises**: Choose from a predefined list (Bench Press, Squat, Leg Press, Lat Pulldown, Treadmill) or create your own exercises with a name and category.
- **Three categories**: Free weight, Machine, and Cardio — each with its own icon and its own weight increment step.
- **Set tracking**:
  - Strength exercises: weight, reps, optional warm-up flag.
  - Cardio exercises: duration in minutes instead of weight/reps.
  - Sets can be added or removed at any time.
- **Per-exercise stats**: Training volume and estimated one-rep max (using the Epley formula) for strength exercises; total time for cardio.
- **Personal records & suggestions**: When a new record (weight × reps) is hit, a hint appears recommending a weight increase for next time.
- **Rest timer**: After each confirmed set, a 3-minute countdown starts automatically and can be skipped.
- **Finish workout**: A session can be marked "finished" (locking the input fields) and reopened for editing later if needed.
- **Autosave**: All input is saved continuously — no manual save needed.

## Technical structure

- **Plain vanilla JavaScript**, no frameworks; the UI is regenerated as an HTML string via a `render()` function on every state change.
- **State** is held centrally in a `state` object (current date, exercise list, exercises active in today's workout, sets, expanded cards, personal records, rest timers, etc.).
- **Data persistence** via a `window.storage` API (`get`/`set`) with JSON serialization. Stored keys:
  - `workout:<date>` — the sets for a given day
  - `finished:<date>` — whether that day's workout was marked finished
  - `custom-exercises` — user-created exercises
  - `best-ever` — personal records per exercise
- **Icons**: Hand-written inline SVGs (dumbbell, machine, cardio, arrows, plus, timer, etc.), no external icon library.
- **Styling**: Plain CSS using CSS variables for colors (`--blue`, `--bg`, `--text`, `--muted`, `--border`), modeled on the iOS design system (rounded cards, shadows, SF Pro–like system font).

## Usage

1. Open the file `mygym_tracker_milestone10_picker.html` in a browser.
2. Use "Add exercise" to pick an exercise or create a new one.
3. Enter sets (weight/reps or duration) — the app saves automatically.
4. Optionally finish the workout with "Finish workout"; reopen it with "Edit".
5. Use the arrows in the date bar to view past workout days.

## Known state / notes

- The filename suggests "Milestone 10" with a focus on the exercise picker — likely a checkpoint in iterative development.
- The end of the HTML file has a few stray/orphaned closing tags (`</p></div></body></style></title>W</head>`) that have no functional effect but could be cleaned up.
- The app is designed for a max width of 480px (mobile-first approach).
