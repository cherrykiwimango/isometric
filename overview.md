# Isometric Room — Overview

A 2D pixel-art copy of a real room that stays in sync with what's happening in the real room.

## The idea

- A **pixel-art version of the room**, drawn in an isometric style and animated.
- A **small avatar** lives in it: it walks around, idles, and reacts to things.
- A **camera** watches the real room.
- **Detection pipelines** look at the camera feed and work out what's going on, for example:
  - light on / off
  - laundry bag empty / mid / full
  - dishes washed / not washed
- When something changes, the backend sends an **event** to the frontend.
- The frontend updates the room to match: the lamp turns off, the laundry pile grows, dirty dishes appear in the sink, and the avatar reacts.

## How it flows

```
Camera  →  Detection pipelines  →  Backend (room state)  →  events  →  Frontend (pixel room + avatar)
```

Open `overview.html` for an interactive version of this diagram.

## What exists so far

- `frontend/`: React + TypeScript + Vite, with PixiJS installed. The app is blank for now.
- `backend/`: Python + FastAPI, with a hello endpoint.
- Each project has a `mise.toml`: `mise run install`, `mise run dev`.

## Still to decide

These are intentionally left open and will be decided as the project goes:

- Which camera, and what hardware runs the detection
- How each detection works
- How events get to the frontend, and what they look like
- The art pipeline and how the avatar behaves

A fake event emitter will probably come first, so the frontend can be built before any real detection exists.
