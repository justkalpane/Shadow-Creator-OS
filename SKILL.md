---
name: varuna-cinematic-video-generator-v3
description: >
  NEW SKILL §13. Takes BRAHMA prompts + TVASHTAR reference photos and generates
  cinematic background videos using RunwayML, Pika, Kling, Sora, or ComfyUI.
  Full camera movement specs, motion types, duration targets, compositing readiness.
  Trigger: generate background video, animate background, B-roll video, cinematic video.
---

# 🌊 VARUNA — Cinematic Background Video Generator
> *God of cosmic order, the celestial oceans, and the night sky.*
> *"BRAHMA envisioned the world. TVASHTAR photographed it. VARUNA breathes life into it."*

---

## VARUNA'S MISSION

Static background photos are good. **Moving cinematic backgrounds are extraordinary.**

VARUNA takes TVASHTAR's reference photos and BRAHMA's environment briefs, then generates:
1. **Looping background video clips** for each scene section
2. **B-roll transition videos** between sections
3. **Animated atmospheric elements** (particle systems, data flows, subtle camera drift)

These videos feed into AGNI (Skill-16) for final compositing with the avatar.

---

## KEY PRINCIPLE: BACKGROUND MOTION HIERARCHY

```
The avatar is ALWAYS primary. Background motion is ALWAYS secondary.

FORBIDDEN:
  × Fast camera cuts in background (distracts from avatar)
  × Bright flashing elements (causes visual fatigue)
  × Text/logos in background (fights with content)
  × People in background (attention splits)

REQUIRED:
  ✓ Slow, elegant motion that supports the emotional tone
  ✓ Motion speed inversely proportional to content complexity
  ✓ Loopable clips (for duration flexibility)
  ✓ Consistent exposure throughout clip
```

---

## MOTION TYPE LIBRARY

| Motion Type | Speed | Best For | Prompt Keyword |
|---|---|---|---|
| **Ambient Breathe** | Ultra-slow | Any content, universal | `subtle ambient motion, barely perceptible drift` |
| **Parallax Drift** | Very slow | Professional/neutral | `slow parallax camera drift, 3D depth layers moving` |
| **Slow Dolly** | Slow | Establishing scenes | `slow dolly push through environment, 0.1 m/s` |
| **Orbit** | Slow-medium | Tech/data visualizations | `slow orbital camera rotation around subject` |
| **Data Flow** | Medium | AI/tech explanations | `flowing data streams, particle systems in motion` |
| **Atmosphere** | Very slow | Dramatic moments | `volumetric fog drift, light shaft movement` |
| **Time Lapse** | Fast background | Impact/scale moments | `time-lapse city movement in background` |

---

## STEP 1 — LOAD INPUTS

From `_outputs/current-job.md`:
- `background_prompts` (from BRAHMA) — environment descriptions per scene
- `reference_photos` (from TVASHTAR) — reference photos per scene
- `script` (from BRIHASPATI) — to determine motion energy per section
- `emotion_curve` (from NATARAJA) — emotion intensity → motion speed guide

**Motion Speed Rule:**
```
Emotion intensity 0.0–0.40: Ultra-slow ambient (ambient breathe)
Emotion intensity 0.40–0.65: Slow drift (parallax / slow dolly)
Emotion intensity 0.65–0.85: Medium flow (data streams / orbit)
Emotion intensity 0.85–1.0:  Dynamic atmosphere (NOT fast cuts — dramatic slow)
```

---

## STEP 2 — BUILD VIDEO GENERATION PROMPTS

For each scene, generate prompts for the target tool:

### RUNWAY ML GEN-3 ALPHA (Best Quality, Industry Standard)

```
RUNWAY PROMPT FORMAT:
[Reference photo description]
[Camera movement instruction]
[Motion type]
[Duration]
[Atmosphere]
[Lighting consistency instruction]

EXAMPLE:
"Ultra-modern AI research laboratory, subtle blue ambient lighting.
Extremely slow parallax drift, camera moving at 0.05 m/s left to right.
Holographic data displays gently pulsing with soft cyan glow.
Atmospheric particles drifting upward in foreground.
Consistent exposure throughout, no flicker.
Duration: 5 seconds, seamlessly loopable."

RUNWAY SETTINGS:
  Duration: 5s (standard) or 10s (loop)
  Reference image: Upload TVASHTAR photo for this scene
  Camera motion: "slow", "very slow", "none (environment only)"
```

### PIKA LABS (Fast, Free Tier Available)

```
PIKA PROMPT FORMAT:
[Scene description] animated, [motion description], 
[atmosphere], [lighting], no humans, loopable background video,
cinematic quality, [duration]s

PIKA PARAMETERS:
  -camera [still/slow-dolly/orbital]
  -motion [0-4, use 1-2 for backgrounds]
  -fps 24
  -ar 16:9
```

### KLING AI (Chinese Platform, Excellent Realism)

```
KLING PROMPT:
[TVASHTAR description], cinematic background video,
[camera movement], slow motion atmosphere,
[environment elements] subtly animated,
professional broadcast quality, no subjects, loopable,
[duration] seconds

KLING SETTINGS:
  Mode: High Quality
  Duration: 5s
  Aspect: 16:9
  Motion: Low (1–2)
```

### SORA (OpenAI — When Available)

```
SORA PROMPT:
A [duration]-second cinematic background video of [environment].
Camera movement: [ultra slow / stationary with environment motion].
[Atmosphere description]. Professional studio cinematography.
[Lighting description]. No people. Suitable for video background.
Seamlessly loopable.
```

### COMFYUI + ANIMATEDIFF (Free, Unlimited, Local)

```
COMFYUI WORKFLOW:
  1. Load TVASHTAR reference photo as init image
  2. AnimateDiff node: motion_module = "v3_sd15_mm.ckpt"
  3. Context length: 16 frames
  4. Motion scale: 0.5–1.0 (low = subtle motion)
  5. Add: LCM sampler for speed
  6. Export: mp4 24fps 5s loop

FREE INSTALL: comfyui.org → install → add AnimateDiff extension
```

---

## STEP 3 — FULL VIDEO BRIEF PER SCENE

```
🌊 VARUNA VIDEO BRIEF — SCENE [N]
══════════════════════════════════════════════════════════════════

Scene:         [Scene name from BRAHMA]
Script time:   [0:00]–[0:30]
Emotion:       [ENERGETIC / CALM / SERIOUS]
Motion level:  [Ultra-slow / Slow / Medium]

REFERENCE PHOTO: [Path from TVASHTAR output]

RUNWAY GEN-3 PROMPT:
"[Full assembled prompt — 2–4 sentences]"

PIKA PROMPT:
"[Full assembled prompt]"
-camera slow-dolly -motion 1 -fps 24 -ar 16:9

COMFYUI (Free) SETTINGS:
  Init image: [TVASHTAR photo path]
  Motion scale: [0.5 / 0.8 / 1.2]
  Frames: 96 (= 4 seconds at 24fps)
  Prompt: "[simplified version]"

COMPOSITING SPEC (for AGNI):
  Duration needed:    [X] seconds (match script section length)
  Loop seamlessly:    YES (use loop-cut technique if needed)
  Avatar position:    [left / center / right] third
  Blend mode:         Normal (avatar on top layer)
  Background opacity: 100%
  Motion blur:        Subtle — 0.3 shutter angle
```

---

## LOOP EXTENSION TECHNIQUE

```
If a scene is longer than your generated clip:
  Method 1 (FFmpeg): Loop the clip
    ffmpeg -stream_loop 3 -i background_scene1.mp4 
           -t [target_duration] -c copy background_scene1_looped.mp4

  Method 2 (Bounce): Reverse + forward = seamless loop
    ffmpeg -i clip.mp4 -filter_complex "[0:v]reverse[r];[0:v][r]concat=n=2:v=1[out]" 
           -map "[out]" bounced.mp4

  Method 3 (Fade): Cross-fade loop
    Use CapCut/DaVinci Resolve: duplicate clip, apply 1s cross dissolve at join point
```

---

## FREE TOOLS COMPARISON

| Tool | Free Tier | Quality | Ease | Best For |
|---|---|---|---|---|
| **Runway ML Gen-3** | 125 credits free | ★★★★★ | ★★★★ | Highest quality |
| **Pika Labs** | 150 videos/month | ★★★★ | ★★★★★ | Ease of use |
| **Kling AI** | 66 credits/day | ★★★★★ | ★★★ | Realism |
| **Luma Dream Machine** | 30 free/month | ★★★★ | ★★★★★ | Natural motion |
| **ComfyUI+AnimateDiff** | Unlimited (local) | ★★★★ | ★★ | Budget, unlimited |
| **HuggingFace Spaces** | Free (limited) | ★★★ | ★★★★ | Zero install |

---

## QUALITY GATE FOR BACKGROUNDS

Before passing to AGNI, verify each background video:
```
□ Motion speed: subtle enough to never distract from avatar
□ Duration: matches or exceeds scene length (can loop)
□ Exposure: consistent, no flicker
□ No people/faces: only environment
□ Format: MP4, H.264, 1920×1080, 24fps
□ Color temperature: consistent with scene lighting spec from BRAHMA
```

---

## SAVE + HAND OFF

Save to `_outputs/current-job.md` under `background_videos`.

> "✅ VARUNA: [X] cinematic background videos generated/prompted.
> Videos are compositing-ready for AGNI's master edit.
> All clips loopable. Avatar separation maintained.
> Next: AGNI for master cinema edit with full compositing."
