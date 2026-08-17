# CAREV — deploy + install

Two files matter: `index.html` (the app) and `CAREV EV App.dc.html` (the desktop
design-review version with the notes column). Both are standalone — no build
step, no server, no dependencies to install.

## Test locally first

Double-click `index.html`. It opens in your browser and works.

Resize the window narrow (under 820px) and it switches to fullscreen phone
layout; wide, and it shows the phone inside a bezel. Same file, both modes.

## Deploy to GitHub Pages

Same flow as your scout group app.

1. Create a repo — call it `carev` (or anything).
2. Upload `index.html` to the root of the repo.
3. Repo **Settings** → **Pages** → Source: `Deploy from a branch` →
   Branch: `main`, folder: `/ (root)` → **Save**.
4. Wait ~60 seconds. Your link is:
   `https://<your-username>.github.io/carev/`

That URL is what you send to clients. It works on any phone, no install needed.

### Faster alternative

Drag `index.html` onto [app.netlify.com/drop](https://app.netlify.com/drop) —
you get a live URL in about 10 seconds, no account required. Good for a demo you
need in the next five minutes; GitHub Pages is better for something permanent.

## Install it to a phone home screen

Once it's on a URL (this does **not** work from a downloaded file — it needs
`https://`):

**Android / Chrome** — open the link → menu (⋮) → *Add to Home screen* →
*Install*.

**iPhone / Safari** — open the link → Share button → *Add to Home Screen*.
Must be Safari; Chrome on iOS can't install.

It then launches from the home screen with its own icon, fullscreen, with no
browser address bar. It looks and behaves like a native app.

## What's in this build

- **Search** — type in the bar over the map; matches station names and areas.
  Filters and sort stack on top of it.
- **GPS distance** — tap *Use my location*. Real straight-line distance from
  where you are, and the list re-sorts by it. Needs `https://`, so it works on
  the deployed URL but not on a local file — it falls back with a visible note.
- **Trip planner** — pick start and destination, adjust the distance. Cost,
  time, stops and arrival battery all recompute.
- **Petrol price** — editable in the Costs tab, saved between sessions. Reset
  link returns it to the OGRA figure.

## Known limits (worth saying out loud in a demo)

- **Needs internet.** React, Babel and the fonts load from CDNs. It will not
  work offline. Ask me if you want a fully offline build.
- **Data is fake.** Five hardcoded Lahore stations. Prices, availability and
  the map tiles are placeholders. The *arithmetic* on top of that data is real.
- **Distances are straight-line**, not driving distance. Road routing needs a
  paid maps API, so the UI labels them honestly rather than overstating.
- **Not built:** booking, payment, accounts, community, rewards, onboarding.
- Babel compiles in-browser on load, so there's a brief boot screen. Fine for a
  demo; for production you'd precompile.
