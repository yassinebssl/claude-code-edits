# Layout and data edits

90 frames at 30 fps unless noted. Follow HOUSE_STYLE.md.

## Kallaway

The shot drops into a rounded bottom panel, the head rises out of it, and a logo plus two-line headline build above. 84 frames.

INPUTS: official logo SVG in its exact brand colour, a true two-line headline, the 2-3 words to set in the accent italic.

- Layout: charcoal #121213 with fine chalk grain drawn once full size (never tiled). Panel x=71..1009, top y=1410, running 5 px past the bottom, radius 40. Scale the clip uniformly by 938/1080; set its top so the median head-top (from the mask) lands at y=1310.
- Head break-out: mask used only above the panel top, overlapping it by 16 px. Clean the mask (fill pinholes, drop specks), then temporally smooth with optical-flow warping of ±2 neighbours (weights 1,2,4,2,1); remove room colour from the hair edge; whisper shadow (blurred, 9 px lower, 40% black).
- Graphic area x=120..960, y=200..1172; nothing on the face, no captions.
- Shot: 0-3 full frame; 3-22 one camera-like move (cubic-bezier 0.6,0,0.3,1) into the panel, corners 0 to 40, heavy sub-frame motion blur (up to 64 samples, 150° shutter); the head cut-out only appears once the panel edge passes behind the head; then a 1.0 to 1.02 push centred on the face.
- Logo: 480 px wide; logo, 104 px gap, two lines as one group centred at x=540, y≈664. Split into parts (one per ray for a star logo, plus a core covering the joins). Frames 10-31 build piece by piece: each part grows from the centre along its direction (expo-out, 15 frames, staggered ~0.55 frames, order stepping ~150° round), 6-sample motion blur; focus rack 11 px to 0 and scale 0.84 to 1; thin physical object from 10 stacked copies 1.7 px apart (lighter chamfer first), tilt rotateX 12°/rotateY -26° easing to 0 by frame 50. Turns from -58° to upright over 10-47 while a two-crest pulse wave (parts up to 7.5% longer) runs 22-48; lands upright with the last word and one breath under 2%.
- Headline: line tops y=847 and y=953. Bold sans white ~96 px, tracking -3; key words in an italic serif at 1.1x in the logo colour. Streams word by word like a chat reply (fade 11 frames, 11 px blur to sharp, rise 20 px, 3.5-4 frames apart) from 17 to 47.
- 46-68 one soft warm diagonal light sweep clipped to the logo (screen, ~44%). Moving grain matched to the footage (overlay 10% on the graphic, a whisper of soft-light grain on the charcoal; measure it against the footage). Slow 1.0 to 1.03 push on the graphic group.
- No extra words, logos or UI; no reflection, glow, outlines or sparkles.

## Face cam

One move puts the person in a creator layout: rounded bottom panel, head breaking out over its top edge, a headline above.

INPUTS: headline line 1 with one accent word, headline line 2.

- 0-24 one eased move with motion blur: full clip shrinks into a panel x=72..1008, top y=1190, 40 px radius, 15% white edge line, soft shadow; frame the person so hands stay in shot.
- Head cut out with the mask, drawn over the panel edge, top of head ~40 px above it; smoothed.
- Above: charcoal #121213 with fine grain. Headline centred between y=520 and 800: line 1 bold sans (~98 px, tracking -3) white with one word in the accent; line 2 italic serif (~110 px) white. Each word rises out of an invisible mask from frame 14, fast ease-out, 4-frame stagger, slight motion blur.
- Hold: slow 1.8% push on the panel anchored on the head top so the break-out stays constant.
- Fonts used in the original: Bricolage Grotesque and Newsreader Italic (both on Google Fonts); download them into the project.

## Reach split

The top half becomes a chalk board with the user's real reach chart; the shot eases into the bottom half and fades into it.

INPUTS: daily "accounts reached" for ~4 weeks and new followers for the same days, from the platform dashboard. Only these numbers.

- Charcoal #121213 with chalk grain. Clip eases down 1-15 into the bottom half: top edge ~y=960 fading into charcoal over ~250 px (no visible line), 84 px side radius, head near y=1060.
- Graphic in the top half: solid down to y=770, gone by y=940.
- Title in bold sans, "last 4 weeks" in accent italic serif; a small glass chip "+N followers | 4 weeks".
- Daily line chart full width, thin gridlines, round-number labels, no dates. Warm white 6 px line turning accent as it climbs the last big days; soft light under the curve. Peak: accent marker, big peak number with the K in accent, "in one day" in italic.
- Timing: 4-27 title word by word and gridlines from the left; 9-31 line across quiet days; 31-41 line whips to the peak while a counter lands on the real value and the marker pops with one ring; 41-60 caption then chip drops and counts; 52-80 light sweep along the line; marker breathes and slow push to the end.
- Round every number down.

## Tier list

A tier list builds below the face; items drop into S-D one at a time; a status pill flips from Ranking to Ranked. This edit may use five tier colours.

INPUTS: topic, items per tier (or ask Claude to rank them first and save the ranking verbatim to a file), optional logos in `public/logos/` named after the items.

- Dark rounded panel below the face inside x=120..960. Rows S red, A orange, B yellow, C green, D blue (coloured label squares, dark grey rows).
- Top pill "Ranking <topic>..." with a small spinner, crossfading to "Ranked" with a tick when the last item lands; never both at once.
- Items drop one at a time every ~4 frames with a small bounce: logo tiles if the file exists, else a clean text chip. Never draw logos.
- Panel slides up and fades in 0-8, items from frame 10, hold, fade out over the last 10 frames.

## Glass graph

A frosted card at chest height: the number counts up and a line graph draws itself.

INPUTS: metric title and period, start and end number (real), optional data series.

- Card ~760x520, centred inside x=120..960, below the face: ~10% white, strong blur behind, 36 px radius, thin light border, soft shadow, top highlight.
- Inside: small grey title; big bold white number counting with ease-out and tabular figures; line graph drawing left to right (rising overall with small dips, from real data if given) in the accent with a fading gradient fill; a dot rides the tip and pulses once at the end.
- Timing: 0-8 card slides up ~60 px and fades in; 8-60 count and draw together; 60-80 hold, dot pulses; 80-90 fade out with a slight drop.

## 3D text

A solid 3D word stands on an invisible desk in front of the person, seen slightly from above.

INPUTS: the word.

- At chest height below the face, inside x=120..960. Prefer `@remotion/three` with extruded text; fallback: ~56 stacked copies receding toward a vanishing point above the frame.
- Camera looks slightly down so letter tops show and sides converge.
- Front faces matte warm off-white (#F2EEE6), no gradients, bevels, outlines or shine. Sides the same hue, 30-60% darker toward the back. Must read as an object, never WordArt.
- Soft contact shadow ~35%, footage-matched grain.
- 0-30 letters rise one at a time, 3 frames apart, ~2.5% overshoot; 30-90 hold with a 1.0 to 1.04 dolly where the word moves slightly more than the background.
