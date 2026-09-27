# Worked example — Cache 2.0 launch film

A 48-second, music-driven launch film for **Cache**, an open-source macOS app (clipboard + screenshot history that lives in the notch). Built in HyperFrames, 1920×1080, 30 fps, then re-laid out for 9:16 and 1:1. Use it as a model for how the rules turn into concrete decisions.

## Message
One sentence, and every claim traced to the app's README and privacy page:

> *Give your notch a memory.*

The proposition is the combination: clipboard **and** screenshot history, **in the notch**, with **on-device text search inside screenshots**, and **nothing leaving the Mac**.

## Brand from the source of truth
- Palette, type and shape came from the **app's code**, not a website: the theme file for the blacks and greys, and the shape file for the notch silhouette.
- The app's **SwiftUI springs** (open, close, peek, select) were ported to easing functions, so the film's notch moves exactly like the real one.
- The icon gradient was sampled from the shipped app icon.

## Taste rules → decisions
| Rule | Decision |
|---|---|
| 3 colors, fixed backgrounds | Three colors, two backgrounds. The black stage doubles as the MacBook bezel. |
| Key object centered | The notch hangs centered from the black bezel in every scene. |
| Flowing transitions | Every scene hands off in-world: the swatch becomes the first peek, the notch grows into the panel, the notch's black floods the frame for the privacy beat. |
| Music tempo | 120 BPM, inside the 115–123 "elite, kinetic" band. Original score synthesized locally. |
| Subtractive SFX | Only keypresses, clicks, the copy peek and the camera shutter. |

## Structure (9 beats)
| # | Time | Beat |
|---|---|---|
| 1 | 0–6 | The problem: copying replaces the clipboard, twice. |
| 2 | 6–10 | The screen rises under the bezel; the copied swatch becomes the first peek. "Now every copy is kept." |
| 3 | 10–16 | Drop: the notch grows into the full panel. "It lives in the notch." |
| 4 | 16–21 | Category chips slide: Links → Colors → Code. |
| 5 | 21–25 | A screenshot is taken and filed. |
| 6 | 25–30 | A search finds text *inside* a screenshot; the camera dives and the recognized text lights up. |
| 7 | 30–34 | Enter copies it and the panel closes. "Never leave the keyboard." |
| 8 | 34–40 | A password copy doesn't register; the black floods the frame. "Nothing leaves your Mac." |
| 9 | 40–48 | Icon, name, tagline, "free & open source", repo URL. |

Note the rhythm: a slow problem open, a drop at 10 s, a feature run that drives, a held privacy beat, then a calm end card.

## Build lessons
- **Generate frames from a small UI kit** (one module for UI pieces, one for per-scene choreography). Edits happen in the kit and rebuild everything, so there's no hand-editing of output HTML.
- **Seek-safe morphs:** the notch shape is a `clip-path: path()` string tween, and springs are expressed as deterministic ease functions.
- **Contrast checks vs fidelity:** one real UI grey fails a strict contrast check. It was kept on purpose because it's the product's real color, and it's documented as an intentional exception.
- **Mix:** −14.2 LUFS, −1.7 dBTP.

## Multi-format re-layout (9:16, 1:1)
- Same nine beats, timings, score and SFX. Every scene is **re-laid out**, not cropped.
- 9:16: the bezel band sits at the top under the platform header, headlines break onto two lines, and content stays clear of the right-hand action buttons and bottom captions.
- 1:1: a shorter bezel band, and content inside a ~60 px margin.
- A per-scene camera scale for each format (e.g. zoom in on small UI for vertical, pull back to show the whole panel).
- One shared choreography module with a layout object per format keeps the formats in sync.
