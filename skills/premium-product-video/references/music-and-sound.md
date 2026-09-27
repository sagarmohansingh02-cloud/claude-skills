# Music and sound

## Tempo first

The soundtrack sets the energy, including the "premium" feeling. Choose the BPM band before the genre.

| BPM | Feel | Typical fit |
|---|---|---|
| 60–80 | regal, cinematic, heritage | brand films, luxury, manifesto launches, fund/firm announcements |
| 90–110 | smooth, cool, effortless | product walkthroughs, calm SaaS and fintech, onboarding |
| 115–123 | elite, kinetic, sophisticated | feature-cascade launches, "everything it does" montages |
| 124+ | drive, hype | only when hype *is* the brand; it overwhelms most premium work |

These bands are a practitioner heuristic, not measured research. Use them as the starting point, then trust the reference.

Then pick the genre for the audience: a developer tool, a luxury brand and a consumer fintech app can share a BPM and still need very different sounds.

## Getting a track at a BPM

- **Licensed or catalog music:** filter by BPM, then audition against the stills.
- **Generated music (HyperFrames `/media-use`):** the BGM generator accepts `--bpm`, `--scale`, `--brightness` and `--density` on its Lyria recipe. Bake the mood into the prompt too, because some backends ignore the flags.
- **Fully local:** synthesize a simple score in code (pads, a pulse, a few hits). This avoids licensing and network use entirely, and it works well for minimal product films.

## Cutting to the music

- Get the beat grid first (HyperFrames: `npx hyperframes beats <project> --json`) and place the key moments on it: the reveal, the drop, the logo.
- Adaptive rhythm lives here: let the music hold while the picture breathes, and let both drive together at the peak.

## Sound design pass (subtractive)

1. Add SFX **only for physical, meaningful moments**: a keypress, a click, a capture shutter, the product's own notification sound.
2. Balance them under the music; nothing should jump out.
3. **Remove pass:** listen end to end and cut any sound that is too loud, out of place, or not helping the viewer understand or stay. If you're unsure, cut it.

Exception: retention-driven short-form clips use denser, punchier SFX on purpose. This pass is for premium product films.

## Delivery targets

- Social/web mix: about **−14 LUFS integrated**, true peak ≤ **−1 dBTP**.
- Check the mix on laptop speakers *and* headphones before delivery.
