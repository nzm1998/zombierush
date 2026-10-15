# ZombieRush — WebGL demo

Playable WebGL build of ZombieRush, a top-down car-vs-zombie survival game
built in Unity 6.

**Play:** https://nzm1998.github.io/zombierush/

## Controls

| Key | Action |
| --- | --- |
| `W` `A` `S` `D` | Drive |
| `Q` | Switch weapon |
| `R` | Reload |
| `F` | Use 引诱剂 (lure — pulls every zombie onto the car) |

Weapons fire automatically at the nearest target; the wheel is all yours.

## Notes

- **Desktop only.** The game is keyboard-controlled, so phones and tablets
  are not supported.
- **Click the canvas once** before playing: browsers only give the page
  keyboard focus and audio after a user gesture, so the first few seconds
  are silent until you interact.
- The build is ~17 MB and loads in a few seconds on a normal connection.
- Best times are stored in the browser (IndexedDB), so they survive a
  reload but are per-browser.

## Deploying an update

This repository contains only the built files. After rebuilding in Unity
(`ZombieRush ▸ Build WebGL`), copy `Builds/WebGL/` over this folder and push:

```bash
cd /Users/nzm/zombierush-web
rsync -a --delete --exclude .git --exclude .nojekyll --exclude README.md \
  /Users/nzm/car/Builds/WebGL/ .
git add -A && git commit -m "Rebuild" && git push
```

GitHub Pages redeploys within about a minute.

## What is in here

Unity WebGL output: `index.html`, the loader/wasm/data payloads under
`Build/`, and the template assets under `TemplateData/`. The `.nojekyll`
file disables GitHub Pages' Jekyll processing so the payloads are served
byte-for-byte.
