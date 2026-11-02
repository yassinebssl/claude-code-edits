# Camera-move edits

Follow HOUSE_STYLE.md. 90 frames at 30 fps unless noted.

## Billboard

The camera pulls back from the clip to reveal it playing on a giant LED billboard on a tower in a city at night. 84 frames.

INPUTS: the city style (or a landmark near the user), optional accent.

- Use 84 frames from a stretch with no jump cuts where the person faces the camera.
- Bake every frame in Python (numpy, OpenCV) in linear light, then play the image sequence in Remotion. JPEG q95, folder under 40 MB.
- Scene in metres: 9:16 LED screen 8.1 x 14.4 m, bottom edge 72 m up, 16 cm black bezel, 55 cm proud of the facade, steel catwalk with railing 1.95 m below. Host tower ~12 x 95 m with dark graphite fins and floor bands 42 cm proud of the glass, interior-mapped rooms behind the glass (mostly dark), quiet cladding variation (≈10% panel tone shifts, mottle, faint vertical streaks, glossier fins).
- Surroundings: towers on a street grid with setback crowns; lit windows grouped by floor and tenant in runs of 2-4 sharing a light, mixing 2700 K, 3500 K and 5000 K, dark floors, a few blue TV rooms, nothing repeating. Blue-grey sky with faint warm-lit cloud; haze thin high, dense low; warm street glow at the bottom when looking down.
- Camera: pinhole, 66° vertical FOV, starts 11.1 m from the screen so it fills the frame. Frames 1-3 raw clip; 3-8 smoothstep cross-fade into the render.
- Pull back 4-42: dolly to 26.6 m interpolating log distance; velocity profile t^1.45·(1-t)^2.7 normalised; arc 16° right and 12° down so the end looks slightly up at the screen; consistent converging verticals; 180° shutter motion blur with 4-14 jittered samples chosen from pixel speed.
- Reveal order: LED emitters (270 x 480 rounded dots on black, visible while each is over 2.7 px, gone by 1.45 px, mip-mapped to avoid moire), then bezel and catwalk, facade, neighbours and sky. Must read as a billboard by frames 25-33 even at 0.65 scale.
- Hold 42-84: keep drifting ~4.5% further back and 2.6° further round. Last frame: screen ~41% of frame height (~790 px), centred near x=530, inside x=120..960, face recognisable.
- Screen lights the world: grazing falloff z/d³ on its facade plus soft haze bounce, tinted by the frame's own colours (pulses with the clip), catching fins, frames and catwalk, faint glow in the air.
- LED character: lifted blacks (+0.0075 linear), slight gain, ~2.4% per-cabinet mismatch on 0.9 m cabinets with hairline seams, off-axis dimming, 2-6 px bloom over the bezel.
- Lens: bloom only above ~0.16 linear, 0.6% veiling glare, 0.4 px softness, gentle vignette, soft highlight shoulder, grain ~2.3/255 stronger in darks.
- No flares, streaks, neon, other text, logos or ads. At most one dim red aviation light blinking once.

## Zoom through

A huge two-line word fills the screen over a frosted clip; the O's counter is a clear window onto the face; the camera flies through it.

INPUTS: two words, one containing an O.

- Heavy bold white sans as wide as x=120..960. Behind: the clip blurred ~30 px at ~45% brightness. Inside the O's hole: the clip clear and sharp, placed over the face.
- 0-10 hold with a 1.0 to 1.03 push. 10-46 fly into the O: scale the word layer about the O's centre exponentially (for example 1.03·60^t, t eased in) so speed feels constant; zoom blur growing with speed; blur the O's edges as they near camera; fade the frosting so the clip is fully clear when the O leaves frame. 46-90 clear clip with a 1.0 to 1.05 eased push.

## Zoom grid

The camera pulls back until the clip is one tile in a wall of the user's own moments, glides one tile across, and dives into it.

- 0-12 full screen. 12-40 eased pull back until the clip is one tile of a 5x5 wall of 9:16 tiles, 16 px gaps, near-black ground; every tile plays a different moment of the clip (start times spread across it); corners round to 28 px; ~3.3 tiles across at the end.
- 40-60 the wall glides sideways exactly one tile on a gentle arc with a slight 3D turn (up to 8°, perspective) that straightens as it lands.
- 60-80 push into that tile until it fills the screen; it keeps playing.
- Motion blur on every move. Use pre-shrunk copies of the clip for tiles to avoid shimmer.

## Pull back

The camera pulls back until the shot is the program monitor of an editing suite, with a real timeline building underneath.

INPUTS: music in `public/music.mp3`, the names of up to five effects for the FX track.

- Dolly back (exponential scale, eased, motion blur) until the clip is the monitor at ~72% size near the top, still playing; corners round in.
- Charcoal ground with chalk grain; glass timeline panel x=56..1024, 40 px radius, containing: timecode and a playhead synced to the monitor frame; an FX track where the named effects drop in and snap one after another (accent colour only here); a V1 filmstrip of real frames split at the clip's real jump cuts; an A1 track with the music's real waveform; a render bar that fills then becomes a small "Rendered" pill.
- Everything rises and snaps with fast ease-outs. Every number shown is real.
