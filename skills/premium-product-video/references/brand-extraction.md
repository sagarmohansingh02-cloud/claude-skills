# Brand extraction — find the source of truth

A premium film looks like *this* product and no other. That only happens when the brand comes from where the brand actually lives, never from a guess.

## Where to look, in order

1. **A brand kit or guidelines** the user or client provides (logo files, a palette sheet, fonts, a lockup). On a client job, look on disk in the client's folder first, since folder names are often inconsistent (`ls` before guessing).
2. **The product's own code**, when it's software. This is often better than any website:
   - theme or token files (e.g. `Theme.swift`, `tokens.css`, `tailwind.config`, `globals.css`) for exact colors, radii and type
   - animation constants (spring response/damping, durations, easing curves), so the film can move like the product
   - shape definitions (custom paths, masks) for silhouettes worth morphing
   - the shipped app icon: sample its gradient stops directly
3. **The live website's CSS**, via custom properties (`:root` variables) in the browser. Pull them live; never from memory.
4. **Real product screenshots**, for UI that has to appear on screen.

If none of these is available, **stop and ask**. Don't invent a palette.

## The 3-color worksheet

Fill this in before any storyboard, then treat it as law for the whole video type.

| Slot | Value | Source |
|---|---|---|
| Stage (background 1) | | |
| Surface (background 2, optional) | | |
| Accent (the one color that means "look here") | | |
| Type family + weights | | |
| Music lane (BPM band + genre) | | |

The product UI brings its own colors when it appears on screen. The worksheet governs everything the *film* adds around it.

## Porting product motion

When the product has motion constants (for example SwiftUI springs `response 0.42 / dampingFraction 0.80`):
- Convert each spring into an easing function or keyframed curve in the video framework, and name them by role (open, close, peek, select).
- Use the product's own curves for UI moves and a calmer camera ease for the film's camera, so the two don't fight.
- Morph real silhouettes (a notch, a card, a button) with seek-safe path or clip-path tweens, not approximations.

## Real UI, not invented UI

- Best: rebuild UI from the product's own code and tokens.
- Next best: real screenshots, cleaned and cropped.
- For generic UI around the product (a browser chrome, a settings card), use real design-system components (e.g. a shadcn/21st.dev component ported to static HTML with the same utility classes), mapped to the brand's tokens.
- Never: placeholder boxes, lorem ipsum, fake buttons.
