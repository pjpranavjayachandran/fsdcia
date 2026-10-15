# 🚍 Transit Journey Planner

A responsive web app built on **OpenStreetMap** data that helps you plan **direct public transport journeys** (bus, metro, train) between two places, and find **essential services nearby** (pharmacy, ATM, toilets and more).

**Live demo:** [add your GitHub Pages link here]

---

## Problem statement

[Describe your user group, e.g. students and commuters] need a quick way to find which public transport routes connect two places, but [describe the limitation you observed when testing openstreetmap.org]. This project provides a focused journey planner that [explain your solution in one sentence].

> Add your own observations and screenshots from testing openstreetmap.org in the section below.

---

## Features

### 🚌 Journey mode
- Enter a start and a destination
- Finds stops near both places, then the bus/metro/train routes that serve both
- Checks the direction of travel
- Shows walking time to the boarding stop, number of stops, the alighting stop and walking time to the destination
- Shows the chosen route on an interactive map

### 📍 Nearby mode
- Search any place, or use your current location
- Choose a category (pharmacy, ATM, hospital, cafe, toilets and more) and a search radius
- Results sorted by distance, with opening hours and wheelchair-access info when available
- Filters for wheelchair-accessible places and places with opening hours listed
- Save favourite places (kept in your browser)

### 🧰 General
- Responsive layout for mobile and desktop
- Form validation with clear error messages
- Loading, empty and error states
- Keyboard shortcut: press **Esc** to clear the forms

---

## Tech stack

| Area | Technology |
|---|---|
| Structure | HTML5 |
| Styling | Tailwind CSS (CDN) |
| Logic | JavaScript (ES6) |
| Map | Leaflet + OpenStreetMap tiles |
| Data services | Nominatim (place search), Overpass API (stops, routes, places) |
| Browser APIs | Fetch API, Geolocation API, localStorage |

---

## How it works

1. The place names are converted to coordinates using **Nominatim**.
2. **Overpass API** returns stops near each point and the transit routes that include those stops.
3. The app keeps the routes found at both ends and checks that the destination stop comes **after** the boarding stop.
4. Options are ranked by total walking distance and drawn on the map.

---

## JavaScript events used

| Event | Used for |
|---|---|
| `click` | Tab switching, location button, result buttons (saved places, "Show on map") |
| `input` | Live slider value, live validation feedback while typing |
| `change` | Filters and sorting update results instantly |
| `submit` | Nearby form and Journey form |
| `keydown` | Esc clears the forms |

## JSON handling
- Category list stored as JSON in the page and read with `JSON.parse`
- API responses (Nominatim and Overpass) read as JSON and converted into clean objects
- Saved places stored with `JSON.stringify` / `JSON.parse` in localStorage
- Missing data handled with defaults such as "Unnamed pharmacy" or "hours not listed"

## Form validation and feedback
- Place fields need at least 3 characters; start and destination must be different
- Red border and inline message for invalid input
- Button disabled and shows "Searching…" while loading
- Clear messages for: no internet, slow or busy server, place not found, location permission denied
- Backup Overpass servers are tried automatically; Nearby mode falls back to Nominatim if all fail

---

## Run locally

1. Download or clone this repository
2. Open `index.html` in a browser (or use the VS Code **Live Server** extension)
3. An internet connection is required for the map and data services

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

## Deploy on GitHub Pages

1. Push the project to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, choose the `main` branch and the `/ (root)` folder
4. Save, then open the link GitHub gives you

---

## Review of the existing OpenStreetMap website

*(Complete this from your own testing. Do not copy these examples.)*

| Feature tested | Steps | What I observed |
|---|---|---|
| Place search | | |
| Directions options | | |
| Finding services near a place | | |
| Mobile experience | | |

## Testing log

| Test | Expected | Result |
|---|---|---|
| Submit empty form | Validation message shown | |
| Unknown place name | Friendly error | |
| Same start and destination | Error message | |
| Journey between two known places | Route options listed | |
| Mobile screen width | Layout stacks properly | |

---

## Limitations

- **Direct routes only.** No transfers between routes.
- **No timetables, fares or live times.** OpenStreetMap does not hold schedule data.
- **Depends on OpenStreetMap coverage.** If routes are not mapped in an area, no result is shown.
- Walking distance is a straight line, not along streets.
- Free public servers can be slow at busy times.

## Future improvements
- One-transfer route planning
- Timetable data (GTFS) for departure times
- Walking directions along real streets

---

## Credits
Map data © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright) (ODbL). Place search by Nominatim and data queries by the Overpass API. Map display by [Leaflet](https://leafletjs.com/).

