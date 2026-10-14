# bestfrend builder — handoff to Claude Code

## What this is
A single-file 3D t-shirt builder for the Bestfrend brand (bestfrend.xyz). `index.html` is the entire app — no build step.
- Real baked t-shirt GLB (MIT, from pmndrs/examples) embedded as base64 inside the file; loads via three@0.160 ES modules from jsdelivr (importmap).
- Four blanks: white / grey / tan / black.
- Designs tab: tap to place on chest, tap another to swap; drag on the 3D shirt to move; pinch or sliders for size/turn/opacity; 10 inks.
- Patterns tab (first tab): checker, swirls, lightning, tie dye, camo, stripes, dots, leopard, flames, stars. Each tap = new layer; "regenerate" re-rolls it. Patterns paint onto the model's real UV panels (front/back/sleeves/collar).
- "+ your image" button uploads a photo as a full-colour design.
- RND shuffles a random one-of-one; NEW clears; PNG saves a snapshot.
- Brand voice: "one of one", "no i in frend", handmade / never repeated / all sales final. Aesthetic = bestfrend.net: white, near-black, zero border-radius, grain overlay, wide-tracked mono labels.

## Immediate task
1. `git init` here, create **public** repo `tonydynamite/bestfrend-builder`, push.
2. Enable GitHub Pages on `main` (root). Live at tonydynamite.github.io/bestfrend-builder.

## Known todos (in priority order)
1. Dog mark is the 64px favicon → soft at chest size. Replace the `DOG` data-URI constant with a clean PNG of the mark (or add it as `dog.png` and point `DOG` at it).
2. Back-print zone: a "front / back" toggle that sets the design's default UV to the back panel (front panel ≈ u 0.02–0.47, back ≈ u 0.52–0.97, v 0.02–0.72 in the GLB's UV layout; chest centre ≈ u .245, v .27).
3. Save/share a build (encode layers in URL hash) so people can send their shirt around.
4. Hook "reserve" into the real bestfrend Supabase/Stripe checkout.

## Testing note
Headless Chromium with `--use-gl=swiftshader` renders the WebGL fine; intercept the jsdelivr three@0.160 URLs to local `node_modules/three` if the sandbox has no network.
