# Orrery — Solar Stopwatch

A solar-system-themed stopwatch. The timer sits at the center like a sun, and every lap you record places a real planet — in order, Mercury through Neptune — onto an orbit ring around it, so your lap history is drawn around the clock as you go.

Single self-contained HTML file. No build step, no dependencies to install — just open it in a browser.

## Files

| File | Description |
|---|---|
| `solar-stopwatch.html` | The app. Open directly in any modern browser. |

## Getting started

1. Download `solar-stopwatch.html`.
2. Double-click it, or open it via **File → Open** in your browser.
3. That's it — everything runs client-side, no server or install required.

## Features

**Core timing**
- Start, pause, and reset, accurate to the millisecond (uses `performance.now()`, not `setInterval`, so it won't drift)
- Lap recording while running, showing both the split (time since the last lap) and the running total
- Reset is only available while stopped, to avoid losing a run by accident

**Mission Log (lap panel)**
- Every lap lists its planet, split, and total time
- Once you've logged 2+ laps: fastest / average / slowest split stats appear
- Once you've logged 3+ laps: the fastest split is highlighted teal and the slowest is highlighted red in the table
- **Copy Log** button exports the full lap list as plain text to your clipboard

**Orrery display**
- The timer itself is the "sun" at the center, with a soft pulsing glow while running
- A comet sweeps the outer ring continuously while running, as a visual cue that time is passing
- Each lap adds a planet to the display, in real solar-system order and color (Mercury → Neptune); hover a planet for its name and lap number
- Past 8 laps, the sequence cycles back to Mercury with a "(2)" marker, so the display stays readable indefinitely

**Customization**
- Three color themes — **Solaris** (gold/amber), **Nebula** (violet/magenta), **Aurora** (teal/cyan) — switch via the swatches in the top right
- Sound on/off toggle (soft tones on start/pause/lap/reset)
- Millisecond-precision toggle (switch between centiseconds and full milliseconds)
- Focus mode — hides the log panel and centers just the orrery for a distraction-free view

**Accessibility & responsiveness**
- Full keyboard control (see shortcuts below)
- Visible focus outlines on every interactive element
- `aria-live` region announces state changes for screen readers
- Respects `prefers-reduced-motion` (disables the pulse, comet sweep, and pop-in animations)
- Responsive layout, down to mobile widths

## Keyboard shortcuts

| Key | Action |
|---|---|
| `Space` | Start / pause |
| `L` | Log a lap |
| `R` | Reset (only while stopped) |
| `C` | Cycle color theme |
| `M` | Mute / unmute |
| `F` | Toggle focus mode |

## Browser support

Built with standard HTML5, CSS (custom properties, `color-mix`), and vanilla JavaScript (Web Audio API for sound, Clipboard API for log export). Works in current versions of Chrome, Edge, Firefox, and Safari. No frameworks, no external JS libraries, no internet connection required after the page loads (Google Fonts are fetched on load; the app still functions without them, just with fallback fonts).

## Customizing further

Everything lives in one file, organized into three blocks:

- `<style>` — color tokens are defined as CSS custom properties at the top (`--a1`, `--a2`, `--glow` per theme, plus shared tokens like `--teal`/`--red` for the fastest/slowest highlights). Change these to retheme the app.
- `PLANETS` array (in the `<script>` block) — edit names, colors, or orbit radius to change what appears as you lap.
- Sound tones are generated with the Web Audio API in the `beep()` function — adjust frequency/duration there if you'd like different tones.

## License

Provided as-is for personal or educational use. No warranty.
