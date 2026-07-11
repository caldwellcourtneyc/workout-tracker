# Workout Tracker

A single-file, phone-first workout tracker. Pick a workout, log weight and reps
per set, watch the progress ring fill, and track each machine's weight over time.

**[Try it live](https://workout-tracker-zeta-five-83.vercel.app)** — your data
stays in your own browser; nothing is sent to a server.

## How it works

- **Everything is in `index.html`.** No build step, no dependencies. Open it in a
  browser and it runs.
- **Data lives on the device** (browser localStorage). Nothing is sent anywhere.
- **Backup / sync between devices** is manual on purpose: the Data tab exports a
  JSON backup file (one-click save to a linked file on desktop, share sheet on
  phone) and re-imports it elsewhere. That JSON file is the source of truth
  that travels between your phone and desktop.

## Structure

- A shared **exercise library**: each machine is defined once (name, model,
  location, settings, target sets/reps).
- **Workouts** are ordered pick-lists that reference those exercises, so the same
  machine in two workouts shares one progress history.
- **Sessions** are dated logs of what was actually done.

## Deploy

Static site. On Vercel it serves `index.html` at the root with no config.
Any static host (GitHub Pages, Netlify) works the same way.

## Customizing

The starter exercise library and workouts live in the `seed()` function in
`index.html` — edit them there, or just use the in-app Library and Workouts
editors, which is what they're for.

## License

MIT — see [LICENSE](LICENSE).
