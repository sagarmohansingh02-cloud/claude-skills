---
name: product-video
description: Direct a product video, launch film, feature reveal or UI motion graphic so it looks premium ("Apple-level", expensive, pro) instead of like generic AI motion graphics. Use whenever the user wants a product/launch/promo video to look expensive, premium, cinematic, polished or Apple-style; when planning, storyboarding or art-directing one; when picking music tempo or sound effects for one; or when giving revision notes on a render ("it looks cheap", "make it feel more premium"). Supplies the taste rules (brand constraints, design before motion, eased motion, flowing transitions, BPM-first music, subtractive sound) and the direction loop (reference → context dump → 3 storyboards → stills → render → director notes). Pair it with /hyperframes or /product-launch-video, which do the build; this skill decides what good looks like and how to steer there.
---

# Product Video

The model and the tools are the same for everyone. What makes a product video look expensive is **intention**: every choice is deliberate and consistent from video to video, and most of "premium" is what you leave out.

Left alone, an AI build falls back to a default look: centered text, a stock gradient, everything fading in. This skill exists to pull it off that default.

This skill is the **director**. The build happens in a code-to-video framework (HyperFrames by default: `/hyperframes`, `/product-launch-video`). Load this skill for the decisions, and load those for the implementation.

## The direction loop

Run these in order. Don't skip to motion.

1. **Reference.** Get 1–2 real videos in the target style and *name* the style ("match this pacing and type"). Naming beats describing. Sources: the client's past films, a curated launch-video catalog such as whatships.com, or `/watch <url>` to study one frame by frame. Pull out pacing, type, transitions and camera language.
2. **Context dump.** Gather everything before designing:
   - the brand, from its **source of truth** (see [references/brand-extraction.md](references/brand-extraction.md))
   - real product UI (screenshots, the app's own code, or real components; never invented boxes)
   - the reference
   - the message, in one sentence
   - the script, if there is one
3. **Three storyboards.** Propose **three** directions that differ in structure, pacing or hero moment, not only in color. The user picks one, which beats patching the first idea.
4. **Stills first.** Build one static frame per scene and review them as a contact sheet (HyperFrames: `snapshot`, with **`--describe false` on client work**, because otherwise frames can be uploaded for AI captions). A still takes seconds to fix. A render costs a re-render.
5. **Render.** Only after the stills are approved. Expect ~80% on the first pass.
6. **Director notes.** Close the last 20% with notes that name **the move, the target and a number** (see below). Never "make it better": vague notes produce random changes.

## The taste rules

Check every storyboard and render against these five layers.

### 1. Brand intention (decide before frame 1)
- Write the constraints down and keep them: **3 colors** for this video type, **1–2 fixed backgrounds**, **one music lane**, one type family.
- Default to *fewer* effects. The most common ways to cheapen a video are stacked effects, decorative SFX and off-brand music.
- Consistency reads as intent. When the viewer senses the video was *decided*, it reads as premium.

### 2. Design before motion
- **One shot = one idea.** If a frame explains two things, split it.
- **Room to breathe.** Keep generous negative space. Crowding reads cheap.
- **Key object centered.** The key object is the real product: a UI panel, a device, the moment of use. Not a line of text.
- **The background serves the brand and never competes** with the key object.
- Product UI must be real (the app's code or screenshots, or real design-system components). Placeholder boxes and fake-looking buttons are instantly felt.

### 3. Animation
- **Ease everything that moves as an event**, and **overlap** moves: the next begins before the last settles. Linear events read cheap.
- **Flowing transitions.** Carry scene A into scene B through a shared element, match cut, push or morph, so each scene feels like it belongs there. Hard-cut only when the cut itself carries the message.
- **Adaptive rhythm.** Speed up, slow down, hold. Uniform pacing is flat, so plan where the film breathes and where it drives.
- If the product has its own motion (UI springs, easing curves), **port it** so the film moves the way the product moves.

### 4. Music: tempo first, then genre
Pick the BPM band for the feeling, then the genre for the audience. Full table, generation flags and mix targets are in [references/music-and-sound.md](references/music-and-sound.md).

| BPM | Feel |
|---|---|
| 60–80 | regal, cinematic, heritage |
| 90–110 | smooth, cool, effortless |
| 115–123 | elite, kinetic, sophisticated |
| 124+ | drive, hype (fits some brands, ruins others) |

### 5. Sound design is subtractive
- SFX only where they help the viewer understand or stay with the product: the keypress, the click, the moment the thing happens.
- Last pass: listen end to end and **remove** anything too loud, out of place or decorative.

## Director-note vocabulary

Notes that land exactly name **the move, the target and a number or frame**:

- **Speed:** "slow every zoom to 0.7x", "ease the settle on scene 3 over 12 frames"
- **Cut:** "cut on the click, not after it", "hard cut on the last word, no music tail"
- **Camera:** "push in on the button", "whip from the list to the detail view", "hold 15 frames longer on the result"
- **Timing:** "land the headline on the downbeat at 0:04", "start the next move 6 frames before this one settles"
- **Subtraction:** "remove the whoosh on scene 2", "drop the glow, keep the shadow"

When the user gives a vague note ("it feels cheap"), translate it into one of these before editing, state the translation, then edit.

## When the rules bend (genre)

These rules target **premium product and launch films**. Other genres break them on purpose:

- **Editorial trailers** (podcast cold opens, documentary teasers) often end movements on a **hard cut on a word**. That satisfies the rule's own exception, because the cut *is* the message.
- **Linear carriers are fine.** A slow constant push under eased events, or a linear wipe revealing text, is deliberate. The rule is against linear *events*.
- **Retention-driven short-form** (clips, hooks) uses denser, punchier SFX on purpose. Don't apply the subtractive rule there.
- **Centered key object ≠ the default AI look.** Centering a *real product* on an on-brand stage is premium. Centering *text* on a stock gradient is the generic look.

## Guardrails

- **Scripts are locked.** If the user supplies a script or voiceover, storyboard variants may change visuals and pacing, never the words or their order. If it runs long, flag the overflow instead of cutting.
- **Never invent a brand.** No palette, font or logo guesses. If the brand source can't be found, ask.
- **Client material stays local.** Don't send client brand files, screenshots, scripts or unreleased product details to third-party generators, component-publishing services or cloud renderers without asking. Keep search queries to external catalogs generic.
- **Claims are traced.** Every on-screen product claim must trace to the product's docs (README, privacy page, changelog). Don't invent features.

## Pre-render QC checklist

- [ ] 3-color / background / music-lane constraints written down and respected
- [ ] Every scene: one idea, key object centered, room to breathe, background not competing
- [ ] Product UI is real, never placeholder
- [ ] Every event eased; moves overlap; no accidental linear events
- [ ] Every scene change is a flowing transition, or a hard cut with a reason
- [ ] Rhythm varies: at least one hold and one drive
- [ ] BPM chosen for the feeling; key moments land on beats
- [ ] SFX pass done: nothing decorative left
- [ ] Script verbatim; on-screen claims traced to docs
- [ ] Contrast and safe areas checked for every delivery aspect ratio (16:9, 9:16, 1:1)

## References

- [references/brand-extraction.md](references/brand-extraction.md) — find the brand's source of truth, the 3-color worksheet, porting product motion
- [references/music-and-sound.md](references/music-and-sound.md) — BPM bands, generating to a BPM, beat grids, SFX pass, loudness targets
- [references/worked-example-cache.md](references/worked-example-cache.md) — a 48 s launch film built with this skill, beat by beat, including 9:16 and 1:1 re-layouts
- [references/sources.md](references/sources.md) — where these ideas come from
