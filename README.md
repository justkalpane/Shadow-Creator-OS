# ⚔ SHADOW AI EMPIRE — ACTIVE JOB OUTPUT FOLDER

All skills write their outputs to this folder.
Claude reads from and writes to `current-job.md` as the live Content Dossier.

---

## FOLDER STRUCTURE

```
_outputs/
  current-job.md          ← LIVE DOSSIER: all pipeline state (auto-managed by ARUNA)
  audio_master_final.mp3  ← You save here after ElevenLabs
  audio_calm_final.mp3
  audio_energetic_final.mp3
  audio_serious_final.mp3
  avatar_video_raw.mp4    ← You save here after HeyGen download
  thumbnail.jpg           ← You save here after image generation
  backgrounds/            ← TVASHTAR reference photos
    scene_01.jpg
    scene_02.jpg
    scene_03.jpg
  bg_videos/              ← VARUNA background video clips
    scene_01.mp4
    scene_02.mp4
  final/
    final_1080p.mp4        ← RENDER-FORGE output
    shorts_1080x1920.mp4   ← RENDER-FORGE output
    master_edited.mp4      ← AGNI output
    captions.srt           ← AGNI output
```

---

## CURRENT-JOB.MD IS THE CONTENT DOSSIER

ARUNA creates and manages `current-job.md` automatically.
All 16 skills read from it and write their outputs to it.
When a pipeline completes, ARUNA saves the final report here.

**Never delete current-job.md mid-pipeline** — it contains all pipeline state.
To start a new video: ARUNA creates a new job_id and resets the dossier.
