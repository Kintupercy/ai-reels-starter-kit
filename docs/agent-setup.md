# Agent setup — wiring the kit to a real agent

This kit is plain markdown: any agent that can (a) generate images, (b) animate them image-to-video, (c) run ffmpeg, and (d) call the ElevenLabs API can run it. The reference setup below uses a Hermes agent on a VPS, driven from Telegram.

## 1. Give the agent the kit
```bash
git clone https://github.com/<your-username>/<this-repo>.git
```
Tell the agent: "Read SKILL.md in this repo and follow it for every reel request. `git pull` before each run."

## 2. Generation tools
- **Images + video:** any image-gen + image-to-video integration (the reference build uses Higgsfield MCP: `gpt_image_2` for keyframes, `seedance_2_0` for animation). Whatever you use, keep SKILL.md rule 5: aspect ratio explicit, generated audio off, typography held static.
- **Assembly:** `ffmpeg` installed on the agent's machine (`apt-get install -y ffmpeg`).

## 3. ElevenLabs (for `auto reel:` mode)
1. Create an ElevenLabs account and add your API key to the agent's environment: `ELEVENLABS_API_KEY=...`
2. Clone YOUR voice (Voice Lab → Instant/Professional clone). You need a few minutes of clean solo speech — existing YouTube VO works great. Note the `voice_id`.
3. Tell the agent the voice_id and the rule: clone VO is generated **per line** — one text-to-speech call per scene — so every scene's audio duration is exact and no silence-detection is needed.
4. Keep SKILL.md rule 1: the clone only fires on `auto reel:` — your real voice stays the default.

## 4. First test run
Message your agent:
```
Explainer reel: what is an AI agent
```
Expected flow: script for approval → keyframes for approval → animation → it asks for your VO recording → finished reel delivered.

Then the fully-automated test:
```
Auto reel: what is an AI agent
```
Same flow, but after keyframe approval it generates the clone VO itself and goes straight to the finished reel. The only human steps left are the two approvals — and you can drop those too once you trust it (edit SKILL.md rule 4; it's your repo now).

## Troubleshooting
- **Text looks warped after animation** → strengthen the "typography stays completely static" line in the animation prompt; regenerate just that clip.
- **Misspelled words in a keyframe** → regenerate that frame with the exact words in quotes; never fix text in post.
- **Reel feels slow** → speed the finished file 1.07–1.10× (SKILL.md rule 7), don't rush the VO read.
- **Music fights the voice** → drop the bed to ~0.10 and keep it constant; no sidechain ducking.

