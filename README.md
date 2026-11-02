# Claude Code edits

A Claude Code skill: 20 premium vertical video edits built in Remotion on your own talking-head clip, with project setup, a house style, person mask and head track, an /edit command and a full-reel assembly.

## Install

```bash
git clone https://github.com/projectgabis-dotcom/claude-code-edits.git ~/.claude/skills/claude-code-edits
```

Claude Code picks it up on the next session. Works best with the Remotion plugin (`claude plugin marketplace add remotion-dev/claude-code-plugin`, then `claude plugin install remotion@remotion`).

## Needs

Node.js, a Remotion project, a vertical talking-head clip (1080x1920 ideal), and for cut-outs a person segmentation tool (MediaPipe or rembg on Linux/Windows, Apple Vision on macOS).

## Credits

Effects catalogue adapted from the FRAME guide by Promptible: https://promptible.notion.site/FRAME-15-video-edits-you-can-make-with-Claude-copy-paste-prompts-4056a397f23b81bcb2d2e937d918d84c . The specs in this skill are rewritten summaries, not the original prompts.
