# Packaging: /edit command, chat intro, full reel, fixes

## The /edit command

Once a few edits work, turn them into one project slash command:

1. Save each edit's filled spec as its own file in `edits/` named with dashes (`edits/reel-wall.md`, `edits/glass-widgets.md`), with the user's values replaced by clear placeholders.
2. Create `/edit` (a project skill or `.claude/commands/edit.md`) with a description the user chooses. Usage: `/edit <name> <the user's own words>`.
3. On run: read the matching file, fill in the user's words, ask for anything still missing (real numbers above all), follow HOUSE_STYLE.md, build, render to `out/`, show 4 stills.
4. `/edit` alone lists every edit with a one-line description. Test it once after creating it.

## Chat-style intro and ending

Optional reusable compositions, designed from scratch in a dark mobile chat style (never copy a real app's screenshots). Make the command, description and following edit into props.

- **ChatRender (~1.2 s):** dark phone chat with a message box (plus button, mic, round accent send button) over a dark keyboard; a thumbnail of the clip already attached. A slash is typed, a command list pops up and narrows to `/edit` then autocompletes; the edit name is typed and a suggestion card with a one-line description autocompletes it; keys light up as pressed. Send: the thumbnail moves top right as a sent message with an accent pill showing the command and an "Editing with <name>..." line with a small spinning star. A card of tiny dots lights up and resolves into the edit, then after ~1 s grows to full screen (corners squaring, chat sinking back) and the edit plays until a hard cut.
- **ChatEnding (~6 s):** a home screen with a greeting in italic serif and the accent star; a keyword is typed and sent; the reply streams in word by word inviting viewers to comment the keyword; a card renders the end board and grows to full screen.

## FullReel

1. For five chosen edits in order: ChatRender with that edit's command and description, then the edit.
2. Hard cuts between sections, no fades.
3. Music from `public/music.mp3` at normal speed, clip audio muted, music fades out over the last 0.5 s.
4. End with ChatEnding. End board: charcoal ground, the call to action in big bold type with the keyword in the accent, a short italic line, and a 3x2 grid of large rounded tiles: the five edits (finished state, small name label) plus a sixth "+N more" tile over a darkened mosaic.
5. Render `out/full-reel.mp4` at 1080x1920, 30 fps; check key elements stay inside x=120..960.

## When something looks off

| Problem | Fix to apply |
|---|---|
| Cut-out flickers or haloes around hair | Smooth the mask more over time and erode it 1 px before feathering |
| Feels too fast | Lengthen to 4 s and stretch every move to match |
| Text hard to read on a phone | Scale all text up 20% and check at phone size |
| A graphic touches the face | Move it lower and keep it out of the face area |
| Motion feels robotic | Re-apply HOUSE_STYLE.md: ease in and out, add motion blur |
| Slow computer | Render a half-size preview first, full quality once approved |

Unfilled inputs make Claude guess: ask for every missing value before building.
