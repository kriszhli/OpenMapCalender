# Open Map Calendar

Plan time and place together.

Open Map Calendar is a shared planning app where each event can include locations and routes, so your schedule is not just "when" but also "where" and "how you move." It is designed for personal trip planning, team itineraries, and day-by-day logistics where map context matters.

## Why It Feels Better Than a Normal Calendar

- You can see your timeline and map at the same time.
- Events support start and destination points, so movement is part of planning.
- Route lines can be `simple`, `precise`, or `hidden` per event.
- In Day view, map interactions are tuned for closer planning (including fine pinch zoom).
- Calendar data is shared, so multiple people on the same hosted instance stay in sync.

## What You Can Do

- Create multiple calendars (work trips, weekend plans, project schedules).
- Add, edit, color-code, rename, and delete events.
- Set start and destination locations per event.
- See event pins on the map with always-visible time/title labels.
- Auto-connect single-location events to the previous event's endpoint on the same day.
- Use precise route caching to avoid repeated provider requests for unchanged routes.

## Mini User Guide

### 1. Create or open a calendar
- Click **Calendars** in the top controls.
- Choose an existing calendar or create a new one.

### 2. Add events
- Drag on a day column to create a time block.
- Give it a title and optional notes.
- Add a start location (`📍`) and/or destination (`🏁`).

### 3. Understand map behavior
- Pins display labels in the format `time | Title`.
- If an event has both start and destination, its route is drawn directly.
- If an event has only one location, it connects from the previous event endpoint on that day.
- If there is no valid previous endpoint, no route is drawn for that event.

### 4. Route mode button (single button cycle)
- Click the route button on an event to cycle:
  - `simple` -> `precise` -> `hidden` -> `simple`
- `simple`: fast curved route.
- `precise`: provider-based route, cached after first fetch.
- `hidden`: keeps location pins but hides route line.

### 5. Day view planning
- Switch to **Day** view for focused planning.
- Use pinch/zoom for finer map inspection while scheduling that day.

## Collaboration and Persistence

- Calendar state is persisted on the server (file-backed).
- Connected clients on the same hosted instance stay synchronized.
- Precise route geometry is cached in event data and reused when still valid.
- Cached route data is removed when locations change or when a route is no longer applicable.

## Run It

### For normal use (hosted/LAN)
```bash
npm install
npm run host
```

Then open the printed URL (for example `http://192.168.1.15:3000`) from any device on your network.

### For development
```bash
npm install
npm run dev
```

- App UI: `http://localhost:5173`
- API server: `http://localhost:3000`

## Engineering Reference

### Tech Stack
- React + TypeScript
- Vite
- Express
- Leaflet
- Framer Motion

### Project Structure
- `/Users/kris/AI/Interactive_Calender/src` - frontend app
- `/Users/kris/AI/Interactive_Calender/server.js` - API + hosted static server
- `/Users/kris/AI/Interactive_Calender/calendars` - per-calendar persisted data
- `/Users/kris/AI/Interactive_Calender/scripts/dev.js` - dev runner for API + Vite

### Scripts
- `npm run dev` - API + Vite dev server
- `npm run dev:client` - Vite only
- `npm run start` - Express server
- `npm run build` - TypeScript build + Vite build
- `npm run host` - build + Express hosting
- `npm run lint` - ESLint

### Data (High Level)
Persisted calendar state includes:
- date range and view settings
- events keyed by day index
- event metadata (title, notes, color, locations)
- route mode and cached precise route geometry when available

## GitHub

Remote:
- `origin`: [https://github.com/kriszhli/OpenMapCalender.git](https://github.com/kriszhli/OpenMapCalender.git)
