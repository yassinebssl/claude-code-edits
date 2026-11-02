# Setup: project, house style, mask and head track

Run once per project.

## 1. Project

- Create a Remotion project (ask the user where; default a `claude-edits` folder). Install its dependencies.
- Every composition: 1080x1920, 30 fps.
- Copy the user's clip into `public/talking.mp4`. Never touch the original.
- If the user has music, copy it to `public/music.mp3`.

## 2. HOUSE_STYLE.md

Write this file into the project and follow it for every edit:

1. **Easing:** no linear motion. Camera moves ease in and out (cubic or sine). Things that appear use a fast ease-out (expo or quint). Springs only with under 4% overshoot.
2. **Motion blur** on anything fast: sub-frame averaging over about half a frame, or a directional blur along the movement.
3. **Safe area:** never cover the face. Readable text stays inside x=120..960 and y=260..1700 so platform buttons and captions do not hide it.
4. **Type:** at most two fonts per edit. A bold modern sans for headlines with slightly tight tracking. Nothing readable under 34 px.
5. **Colour:** white and off-white plus one accent colour. Ask the user for their brand accent; default orange.
6. **In the scene, not pasted on:** soft shadows, the person in front where it makes sense, light film grain on added graphics.
7. **Smooth:** smooth all tracking over time, no jitter or flicker.
8. **Banned:** neon, glowing outlines, colour blobs or orbs, stickers, emoji, glitch effects.

Per edit: own composition named after the edit, open Studio, render to `out/`, report the path, show 4 stills.

## 3. Person mask

A black and white clip where the person is white, same size and frame rate, frame for frame, saved as `public/mask/NNNN.png`.

- macOS: Apple Vision person segmentation (accurate quality) through a small Swift script.
- Linux or Windows: rembg or MediaPipe selfie segmentation (free).
- Feather the edge 1 to 2 px and smooth over 3 frames so hair and shoulders do not flicker.

## 4. Head track

From the mask, per frame: top of head, left and right edges of the head, head centre. Smooth each over about 7 frames. Save as `public/head-track.json`.

## 5. Components

- `BehindMe`: draws a graphic behind the person and in front of the background, using the mask.
- `InFrontOfMe`: draws a graphic on top of everything.

## 6. Check

Overlay the mask on the video at 5 frames spread across the clip and show them, so the user can confirm the edge is clean.
