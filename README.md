# YOU-_ARE_HERE
# End of Year Countdown

A single self-contained HTML page that visualizes the year as a wall of hanging
threads — each thread is one day, physically simulated with Verlet integration
so it sways, stretches, and reacts to touch/mouse like real rope.

No build step, no external libraries. Open `index.html` in any browser.

## Features

- **Live countdown** — days left, and an HH:MM:SS clock ticking down to
  midnight on Dec 31, updated every second.
- **Year progress bar** — percentage of the year elapsed, with day count.
- **Hanging rope canvas** — 50 threads (one per day-ish), each built from
  8 Verlet particle segments with a damped pendulum simulation:
  - Past days render in orange with a glow.
  - Today's thread renders in white with a glow and is highlighted.
  - Future days render in dim gray.
  - Threads respond to mouse drag / touch drag, and can be flicked or snapped.
- **"You are here" marker** — on load, a fading label points at today's
  thread so the viewer immediately knows where "now" sits on the timeline.
  It fades out automatically after ~2 seconds.
- **Adaptive rendering** — expensive effects (shadow blur / glow) are
  scaled back automatically on coarse-pointer (touch) devices to keep
  frame rate smooth on phones; desktop keeps full glow on every thread.
- **GitHub credit button** — a floating icon bottom-right that expands
  into a "Built by" link on tap, matching the page's dark/orange theme.

## Tech

- Vanilla HTML/CSS/JS, single file, zero dependencies.
- Canvas 2D for the rope rendering (no WebGL, no physics library —
  the Verlet/PBD solver is hand-written).
- Responsive layout tuned with `clamp()` for phone-sized viewports.

## Usage

Just open `index.html` in a browser — desktop or mobile. Nothing to install,
nothing to configure. Drag any thread to see it swing; today's thread is
easiest to find via the white glow and the "You are here" label on load.

## Customization

- `THREAD_COUNT` and `SEGMENTS` (near the top of the rope script) control
  thread count and physics resolution.
- Colors live in the `:root` CSS variables (`--orange`, `--orange-bright`,
  `--bg`, etc.) and in `getRopeColor()` for the rope strands themselves.
- The GitHub link/name in the floating button can be edited directly in
  the `.gh-fab` markup near the end of the `<body>`.
  
