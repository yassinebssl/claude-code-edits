# Edits that place graphics behind the person

All use `talking.mp4`, the mask and `BehindMe`; 90 frames at 30 fps unless noted. Follow HOUSE_STYLE.md.

## Reel wall

The flat wall behind the person becomes a grid of vertical screens playing their real top reels.

INPUTS: number of reels (about 8) in `public/reels/1.mp4..` (1 = best), real view count per reel, 3 or 4 columns.

- Pre-cut a ~4 s lively excerpt of each reel, downscaled to on-screen size, as frames, so many play smoothly.
- Find the wall's perspective (its corners) so screens lie flat on the wall; stay under the ceiling line.
- 9:16 screens in columns with small gaps showing the real wall; thin dark bezel, tiny radius, a dark pill with play icon and views. Only the best reel gets the accent (pill and hairline edge).
- Person and foreground furniture stay in front via the mask; no hair halo.
- Screens light the room: soft spill on gaps, ceiling, furniture, faint rim on hair and shoulders. Match black level, slight bloom on highlights, same grain.
- Timing: 0-6 dark glass; 6-18 switch on in a wave from behind the head with a short bloom; from 6 columns scroll like a feed, alternating directions at slightly different speeds; whole time a slow push (wall 1.0 to 1.03, person 1.0 to 1.05 for parallax) with slight drift, still moving at the end; 44-60 best reel comes forward and brightens.
- Hide any view pill partly covered by the person.

## Glass widgets

The room becomes a home screen: three big smoked-glass widgets at different depths, a live clock, the playing song, and a notification in front of the person.

INPUTS: time (match any phone status bar), day, song title and artist, audio file, app logo, app name, notification text, accent colour.

- Glass in linear light: blur the room inside the shape only, magnified ~3%, slight outward bend in a thin rim band; smoked tint passing 35-45%; radius ~60 px large, ~46 px small; hairline border tinted by the room, brighter top-left; shadow down-right; top sheen and darker inner edge; text full white over a soft dark copy of itself.
- Two fonts, two weights. Accent only on the app logo. Leave one side of the frame empty.
- Clock (wide, top, furthest back): huge digits, small seconds on the same baseline, day under. Real ticking: seconds start at 58, tick at frame 16, minute rolls at 46. Digits slide up out and in from below, right to left, with vertical motion blur; slot width eases.
- Now playing (tall, right, middle depth, where the hand rises so it passes in front): label, title, artist, pause icon, real-speed progress, scrolling waveform from the real audio (~10 bars/s, played bars white, upcoming dimmed, edges fade).
- Notification (wide pill across the chest, nearest, IN FRONT): logo in real colours, app name bold, "now" dimmed, message.
- Depth: three planes; slow push 1.0 to 1.03 with nearer widgets growing and drifting more; person between back widgets and notification; soft person shadow on widget glass behind.
- Timing: clock arrives 1-19, now playing 6-24 (rise ~40 px, scale from 94%, frost forms as it fades in, text sharpens); tick at 16; notification springs up 20-32 from ~100 px lower and 92% (≈0.4 s spring, slight settle, motion blur); minute rolls 46-58; one light sweep across all glass 58-77; match footage grain.
- Only real things: no weather, calendar, fake messages or numbers.

## Orbit

Five thick glass app tiles (like, comment, share, save, follow) orbit the head in real 3D; the heart gets liked as it passes in front of the chest.

INPUTS: the five symbols or logos, which tile gets liked, accent colour, the room's accent light.

- Tiles: square glass blocks with app-icon rounded corners (~30% radius), depth ~22% of width, rounded rim ~10%. Symbols drawn as clean white shapes, ~half the tile, stroke ~7%. No numbers or words.
- Glass by ray tracing: refract into the front face (index 1.5), through the block, sample the video where the ray exits; strong bending at the rim, little in the middle; ~2 px frost on the face, sharp rim; smoke passing ~60%, darker at the rim; slight chromatic split at the rim (±1.5%); Fresnel reflections.
- Light matched to the room: key highlight top-left rim, ceiling streak along the top edge, the room's accent light on right edges; bright line where face meets rim, faint inner bottom shadow, soft top sheen. Symbols raised, frosted, lit by the same key with a small glint.
- Orbit: 3D ellipse at eye-line perspective, tilted down at the front; follows ~half the head-track motion, smoothed; back half wider and lifted so back tiles pass beside and above the head. Sizes ~232 px front, ~153 px sides, ~129 px back. Tiles face camera but swing up to 17° and lean up to 7° into the turn.
- Layers: room without person, back half, person, front half. Switch layers only beside the head.
- In the room: person shadow on tiles just behind; front tiles shadow down-right onto the person only; back tiles defocus up to 2.6 px and dim to ~64%; motion blur 0.4 of per-frame travel; grain matched to the clip.
- Timing: tiles appear 1-20 about 2 frames apart (86% to 100%, focus pull); ring spins up 1-30, overshoots to ~2x cruise around frame 13, settles to one turn per 6 s; around frame 44 the chosen tile crosses the chest and fills with the accent over 5 frames with one small damped pop (≤6%); camera push 1.0 to 1.035. Still moving at the end.
- Never cross the face; tiles inside x=120..960. Accent only on the liked tile.

## Reel orbit

Like Orbit, but the cards are the user's top reel covers with real view pills.

INPUTS: number of reels (~5), covers in `public/covers/1.jpg..` (1 = best), real view counts.

- Vertical rounded cover cards, small dark views pill. 3D ellipse following the smoothed head track; cards face camera, lean up to 7°, ~1.5x at front, smaller at back.
- Layers and layer-switch rule as Orbit; never cross the face; inside x=120..960; back cards defocus up to 2.6 px and dim to ~64%; directional motion blur; person shadow on back cards, front-card shadows on the shirt, a glint sliding across each card as it passes the front.
- Cards resolve in one after another (fast ease-out, slight scale-up, focus pull) while the ring spins up, overshoots softly and settles; slow 3.5% camera push; best reel crosses the chest mid-effect; still moving at the end.

## Text ring

A ring of text spins around the head in 3D, front half in front, back half behind.

INPUTS: the text (end with a separator so it loops).

- True 3D circle, radius ~270 px, centred on the smoothed head track at forehead height, eye level, tilted ~15° front-down.
- Letters face outward, bold sans, white, ~52 px, laid out by arc length so the phrase closes the circle exactly.
- Back half via `BehindMe`, front half in front. Far-side letters ~35% brightness, slightly blurred, smaller. Soft shadow on the hair where the front arc passes.
- Frames 0-18 ease from still to one turn per 3 s, then keep turning; motion blur along each letter's travel.

## Text path

A repeated line of text flows along the outline of the head and shoulders, behind the person.

INPUTS: the text (repeated with a bullet separator).

- Each frame trace the silhouette from the mask: left shoulder, over the head, right shoulder; offset ~65 px outward.
- Smooth in space (neighbour averaging) and time (~5 frames each side) so it moves at most 1-2 px per frame; hold steady across jump cuts.
- Medium-bold sans, white at 90%, ~46 px, each letter rotated to the curve, scrolling ~150 px/s. Write-on from the left over frames 0-20. Both ends fade over their last 80 px. Drawn behind the person.

## Text behind

A huge word rises from behind the head, holds, drops away.

INPUTS: the word.

- Heavy condensed bold sans, white, ~330 px tall, centred behind the head, the whole word inside x=120..960 (shrink if needed). The head must cover part of it.
- 0-10 rises from lower, blurred to sharp, transparent to solid; 10-75 hold with a ~20 px slow lift; 75-90 drops and fades.

## Over the shoulder

The camera pushes in over one shoulder as a BEFORE card pops, swings to the other shoulder for the AFTER card, then settles. Cards sit behind the person.

INPUTS: before number with label, after number with label (real, screenshot-able).

- Two dark glass cards just above the shoulder line, behind the person via the mask: rounded, ~20% white hairline, blur behind, soft shadow, small grey label over a big bold white number. Pop: scale 0.8 to 1 plus fade.
- Cards are attached to the footage; the camera move scales and slides the whole shot and must always fill the frame (no black edges).
- Timing: 0-5 centred; 5-20 slide left and push to 1.3x over the left shoulder, BEFORE pops at 10; 20-27 hold with tiny drift; 27-36 out to 1.12x sliding across; 36-46 push to 1.3x over the right shoulder, AFTER pops at 40; 46-55 hold; 55-70 settle to centre.
- Motion blur proportional to camera speed, none on holds. Focused card inside x=120..960.

## Stage light

The room goes dark, a theatre spotlight lands on the person, and a word is projected onto the wall as light, cut by the head's shadow.

INPUTS: the word.

- Linear light throughout. Lights down 1-15: everything outside the (cleaned) mask down ~3 stops, slightly cooler; the person keeps their light.
- Spotlight 14-20 (quick ease-out, tiny settle, warming like a lamp): soft oval pool on the wall behind head and shoulders; person shadow down-right inside it; faint beam from above through drifting haze (6-10%); top light on hair and shoulders; thin wrap from the lit wall.
- Projected word 21-37 from a lower front-left projector: keystoned flat on the wall, added to the wall's brightness (takes its texture), cut by the mask projected from the projector's direction with a blurred edge; fades up while racking into focus.
- Slow push 1.0 to 1.04, soft highlights, fine grain in the dark room. Warm white only.

## Glass panels

Four smoked-glass panels behind the person, at three depths, show what the edit is doing: the command, the cuts, the export, the mask.

INPUTS: the command text, the real number of jump cuts in the clip.

- Glass: near-black tint ~55%, strong blur behind, 28 px radius, ~14% hairline border, top highlight, soft shadow. Bold sans for numbers and labels, italic serif for one or two words.
- Panels: command bar across the top (accent star, command types out with the slash part dimmed, star turns, then tick and "Done"); cuts panel high left and nearest (counter climbs as each real cut lands, a strip of the clip with cut marks, accent playhead, real timecode); export panel lower right (9:16 outline draws, "1080 × 1920", "30 fps", tick); mask panel low left, furthest back, softer (live white silhouette from the mask, frame counter).
- Timing: 3-15 command types; 7-33 panels arrive back to front; 15-37 cuts land; 33-44 export tick then Done; 46-72 one light sweep; per-panel depth parallax and gentle push, still moving at the end.
- Only true numbers.
