---
name: claude-code-edits
description: Build premium vertical video edits on a talking-head clip with Remotion inside Claude Code, from a library of 20 named effects (reel wall, glass widgets, Kallaway split, 3D orbit, billboard pull-back, zoom through, text path, zoom grid, face cam, 3D text, text ring, tier list, glass graph, over the shoulder, text behind, stage light, glass panels, reach split, reel orbit, pull back), plus project setup, a house style, a person mask and head track, an /edit slash command, a chat-style intro and a full-reel assembly. Use when the user wants to edit a reel, TikTok or Short with code, asks for one of these effects by name, wants a Remotion edits project set up, or wants a reusable /edit command.
---

# Claude Code edits

A library of vertical (1080x1920, 30 fps) edits that Claude builds in Remotion on the user's own clip and renders to MP4. Each edit is a 3 second composition (90 frames) unless its spec says otherwise.

Credit: technique catalogue adapted from the FRAME guide by Promptible ("15 video edits you can make with Claude"). The specs here are rewritten summaries, not the original prompts.

## Before building any edit

1. **Project set up?** If there is no Remotion project with `HOUSE_STYLE.md` and `public/talking.mp4`, run the setup in [references/setup.md](references/setup.md) first. Never modify the user's original clip; copy it.
2. **Mask and head track?** Most edits need `public/mask/` (one PNG per frame) and `public/head-track.json`, plus the `BehindMe` and `InFrontOfMe` components. Build them once (setup step 2).
3. **Real data only.** Ask the user for every number, name, logo file, song and view count an edit shows. Never invent figures; round numbers down. If a value is missing, ask, do not guess.
4. **Follow HOUSE_STYLE.md** for every edit, except where an edit spec states an exception.

## Building an edit

1. Read the spec for the edit in the reference files below.
2. Fill its inputs from the user (marked as INPUTS in each spec).
3. Build it as its own composition named after the edit.
4. Open Remotion Studio for preview, render to `out/<EditName>.mp4`, report the exact path.
5. Show 4 stills (start, two middle moments, end) so the user can check without playing it.
6. Check the safe area: readable text inside x=120..960, y=260..1700; nothing over the face.

## The edit library

| Edit | Composition | Look | Spec |
|---|---|---|---|
| Reel wall | ReelWall | Wall behind you becomes screens playing your top reels | [behind-you](references/edits-behind-you.md#reel-wall) |
| Glass widgets | GlassWidgets | Smoked-glass home-screen widgets at depth, live clock, song, notification | [behind-you](references/edits-behind-you.md#glass-widgets) |
| Orbit | Orbit | Thick glass social tiles orbit your head in 3D, heart gets liked | [behind-you](references/edits-behind-you.md#orbit) |
| Reel orbit | ReelOrbit | Your reel covers orbit your head with real view counts | [behind-you](references/edits-behind-you.md#reel-orbit) |
| Text ring | TextRing | Text ring spins around your head in 3D | [behind-you](references/edits-behind-you.md#text-ring) |
| Text path | TextPath | Text flows along your head and shoulder outline | [behind-you](references/edits-behind-you.md#text-path) |
| Text behind | TextBehind | Huge word rises from behind your head | [behind-you](references/edits-behind-you.md#text-behind) |
| Over the shoulder | OverTheShoulder | Camera pushes over each shoulder as BEFORE/AFTER cards pop behind you | [behind-you](references/edits-behind-you.md#over-the-shoulder) |
| Stage light | StageLight | Room goes dark, spotlight, a word projected on the wall | [behind-you](references/edits-behind-you.md#stage-light) |
| Glass panels | GlassPanels | Glass panels behind you show the prompt, cuts, mask and export | [behind-you](references/edits-behind-you.md#glass-panels) |
| Kallaway | Kallaway | Shot drops into a bottom panel, head breaks out, logo and headline build above | [layouts](references/edits-layouts.md#kallaway) |
| Face cam | FaceCam | Creator layout: rounded panel, head breaks out, headline rises | [layouts](references/edits-layouts.md#face-cam) |
| Reach split | ReachSplit | Top half becomes a chalk board with your real reach chart | [layouts](references/edits-layouts.md#reach-split) |
| Tier list | TierList | S to D tier list builds below your face | [layouts](references/edits-layouts.md#tier-list) |
| Glass graph | GlassGraph | Frosted card at chest height, number counts up, line draws | [layouts](references/edits-layouts.md#glass-graph) |
| 3D text | Text3D | A solid 3D word stands on the desk in front of you | [layouts](references/edits-layouts.md#3d-text) |
| Billboard | Billboard | Camera pulls back to reveal your clip on a city billboard at night | [camera](references/edits-camera.md#billboard) |
| Zoom through | ZoomThrough | Camera flies through the O of a giant word into your shot | [camera](references/edits-camera.md#zoom-through) |
| Zoom grid | ZoomGrid | Pull back to a wall of your moments, glide, dive into another | [camera](references/edits-camera.md#zoom-grid) |
| Pull back | PullBack | Pull back until your shot is the monitor of an editing suite with a live timeline | [camera](references/edits-camera.md#pull-back) |

Packaging (the `/edit` command, the chat-style intro and ending, the full reel) and troubleshooting: [references/packaging.md](references/packaging.md).

## Shared techniques

- **Layering behind the person:** background, graphic, then the person cut out from the mask on top (`BehindMe`). A graphic may switch from behind to in front only where it does not overlap the person.
- **Glass:** blur what is behind only inside the shape, tint it, add a hairline border, a top sheen and a soft shadow. For realistic glass, work in linear light (convert, blur and tint, convert back).
- **Camera moves:** scale exponentially (interpolate the log of the scale) so speed feels constant; ease in and out; keep moving on the last frame.
- **Motion blur:** average sub-frame samples across part of a frame, or blur along the direction of travel, sized from speed.
- **Make it sit in the scene:** soft shadows, match the clip's grain and black level, the person in front where it makes sense.
- **Heavy scenes** (billboard, 3D glass): bake frames in Python (numpy, OpenCV) and play them back as an image sequence.

## Related plugins

The `remotion` plugin (Remotion best practices, render, captions) and `hyperframes` plugin are installed. Use Remotion's best-practices skill for API details.
