# Gratitude Diary (Offline SPA)

A clean, mobile-friendly gratitude diary that runs fully offline in the browser (and inside a WebView wrapper like Capacitor). Write one gratitude entry per day, attach one photo, tag a mood, and track your streak. Data stays on-device with import/export support.

## Features

- Offline-first single-page app (SPA)
- Calendar view with bigger day cells and optional photo thumbnails
- Daily entries with:
  - Free-form text
  - Mood emoji tag
  - One optional photo attachment (with “Remove photo”)
- Entries list view with search
- Streak tracking (current + longest)
- “On this day” resurfacing of past entries
- Import/Export
  - Export: ZIP containing `gratitude_data.json` + `/photos` folder
  - Import: merge entries from ZIP into existing local data
- Mobile UX
  - Hamburger menu navigation
  - Hardware back button behavior:
    - If menu open → back closes menu
    - If in Entries/Stats/Data → back returns to Calendar
    - If in Calendar → back exits app (native OS behavior)

## Screens

- Calendar (home)
- Entries
- Stats
- Data (Import/Export)

## Tech Stack

- Vanilla HTML/CSS/JS (single file)
- IndexedDB for entries storage (text, mood, photo DataURL)
- localStorage for small settings (e.g., longest streak)
- JSZip for ZIP import/export

## Data Model

Each entry is stored in IndexedDB with key `date` in `YYYY-MM-DD` format:

```json
{
  "date": "2026-02-25",
  "text": "Today I'm grateful for ...",
  "mood": "😊",
  "photo": "data:image/jpeg;base64,...",
  "favorite": false,
  "timestamp": 1708890000000
}
