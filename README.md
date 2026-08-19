# Spaced Review (Revisão Espaçada)

A single-file, static web app for spaced-repetition review, laid out as a pinboard of draggable sticky notes.

## Features

- **Drag-and-drop board** with six stages: Inbox → 24 hours → 7 days → 28 days → 6 months → Mastered.
- **Automatic scheduling**: dropping a card into a stage recalculates its next review date/time from that moment, using that stage's interval.
- **Due tracking**: cards past their review date are flagged so you know what to review first.
- **Rich text cards**: bold, italic, and underline (via a small formatting toolbar or `Ctrl+B` / `Ctrl+I` / `Ctrl+U`).
- **Time zone aware**: timestamps are stored in UTC and displayed in a time zone you pick from a dropdown.
- **CSV import/export** for backups or moving your cards between devices/browsers.
- **Multi-language UI**: Portuguese, English, and Spanish, auto-detected from the browser and switchable at any time.
- **Built-in help**: a "Help" button opens a short guide to the stages, intervals, and controls, in whichever language is selected.
- **Light/dark theme**, following the system preference.

## Getting started

Open `index.html` in any modern browser. That's it, no install and no server required.

## How it works

Cards move through six columns representing a spaced-repetition schedule. When you drag a card into a column, its next-review timestamp is set to "now + that column's interval":

| Stage | Interval |
|---|---|
| Inbox | due immediately |
| 24 hours | +1 day |
| 7 days | +7 days |
| 28 days | +28 days |
| 6 months | +6 months |
| Mastered | no further review |

Cards whose next-review time has passed are highlighted as due, both on the card itself and as a count badge on its column.

## Data & privacy

All data lives in your browser's `localStorage`; nothing is sent to a server except:

- the Google Fonts stylesheet/font files (Fraunces, Work Sans, Kalam), and
- a single anonymous hit-counter request on page load (see [Visitor counter](#visitor-counter) below).

Use the **Export CSV** / **Import CSV** buttons to back up your cards or move them to another device or browser. Importing merges by `id`: existing cards are updated, new ones are added.

CSV columns: `id, content, stage, created_at, moved_at, next_review_at` (timestamps in ISO 8601 UTC; `content` may contain `<b>`, `<i>`, `<u>`, and `<br>` tags).


