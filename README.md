# AI Reels Starter Kit — Clean Explainer Lane

Make animated Instagram Reels end-to-end with an AI agent — from a one-line chat message to a finished 9:16 video.

This is the exact *method* behind @stlpercy's animated explainer reels, packaged as a starter kit any capable AI agent can run (Hermes, Claude, or any agent with an image-gen + video-gen integration and ffmpeg).

**The pipeline:** script → keyframes (AI image gen) → animate (image-to-video) → voiceover (yours, or an AI clone) → assemble with ffmpeg → deliver.

## What's in the kit
| Path | What it is |
|------|-----------|
| `SKILL.md` | The master workflow + the locked rules (start here) |
| `styles/clean-explainer.md` | The style lane: calm, premium single-concept explainers |
| `docs/agent-setup.md` | Wiring it up: repo, API keys, and your first test run |

## How it works
1. You message your agent: `Explainer reel: what is an AI agent`
2. It writes a ~10-line script and waits for your OK.
3. It generates one clean keyframe per line and waits for your OK.
4. It animates each keyframe, gets the voiceover (you record it — or fully hands-off with `auto reel:` + an ElevenLabs voice clone), and assembles everything with ffmpeg.
5. A finished 9:16 reel lands back in your chat.

## The rules that make it look good (short version)
- All on-screen text is generated **into** the artwork — never overlaid in post.
- One idea per frame. Generous negative space. Fewer, longer holds.
- The voiceover is the master clock — the edit cuts to the voice, not the other way around.
- Approval gates before anything costs money: script first, then keyframes, then animate.
- Pick 3–4 colors and lock them. Consistency is the style.

## Credit
Method by Percy (@stlpercy). Steal it, make it yours — and make the style your own: change the palette, change the pacing, keep the system.

