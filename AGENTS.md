# AGENTS.md

## Project

A single-file, phone-first strength-training tracker. Users select workouts,
record weight and repetitions, review progress, and manage an exercise library.
Workout data remains on the user's device.

## Setup

No installation or dependencies are required.

Open `index.html` directly in a browser.

## Run

Open `index.html` locally. There is no development server or build step.

## Test And Verify

There is no automated test suite.

After changes:

- Open `index.html` in a browser.
- Check the phone-sized and desktop layouts.
- Exercise the changed workflow with existing and newly seeded data.
- Confirm export and import still preserve all workout data.
- Check the browser console for errors.

## Build And Deploy

There is no build command. Vercel serves `index.html` at the site root.

The GitHub repository is connected to Vercel. Do not push, merge, or deploy
without Courtney's explicit approval.

## Architecture

Everything is implemented in `index.html` using HTML, CSS, and vanilla
JavaScript.

Data is stored in browser `localStorage` under `braindeux_workout_v2`:

- Exercise library: shared exercise definitions and settings.
- Workouts: ordered exercise references.
- Sessions: dated workout logs and completed sets.

The `seed()` function supplies starter data only. Existing users normally have
independent data in browser storage.

Backup and device-to-device sync use exported JSON files. There is no backend.

## Conventions

- Keep the application dependency-free and single-file.
- Preserve the offline-first, local-storage-only architecture.
- Discuss any backend, account, or automatic-sync proposal before building it.
- Treat stored user data as durable and provide migrations for schema changes.
- Escape user-controlled text before inserting it into HTML.
- Keep controls usable on a phone during an active workout.
- Prefer the in-app editors over seed changes for user-specific exercises.

## Known Traps

- Changing `seed()` does not update exercises already stored on a user's device.
- Schema changes must preserve older exports and existing local data.
- Third-party media requests alter the otherwise local-only privacy model.
  Load external media only after an explicit user action.
- A failed import can replace important workout history; preserve the existing
  confirmation and validation flow.

## Done Criteria

A change is complete when:

- Existing workout data remains intact.
- The changed workflow works at phone and desktop sizes.
- Export/import remains compatible.
- The app produces no new browser-console errors.
- Any new online dependency has a clear offline fallback.
