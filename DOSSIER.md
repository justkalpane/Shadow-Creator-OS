# ⚔ SHADOW AI EMPIRE — MASTER DATA CONTRACT
## The Content Dossier Schema v3.0.0
### All skills READ from and WRITE to this shared state object.
### Save/update at: `_outputs/current-job.md`

---

```json
CONTENT_DOSSIER {

  // ═══ SYSTEM (KRISHNA sets) ═══════════════════════════════
  job_id:             "SHADOW-YYYYMMDD-XXXX"   // UUID, auto-gen
  created_at:         ISO-8601 timestamp
  pipeline_status:    0=IDLE | 1=EXECUTING | 2=SUCCESS | 3=HALTED
  current_module:     string
  retry_count:        int (0–3 max per module)

  // ═══ NARADA OUTPUT ═══════════════════════════════════════
  topic:              string     // video topic
  topic_score:        float      // virality 0–10, GATE: ≥ 6.0
  content_brief: {
    hook_type:          CURIOSITY_GAP | SHOCK_STAT | OPEN_LOOP | CONSPIRATORIAL | IDENTITY
    dominant_emotion:   ENERGETIC | CALM | SERIOUS | CONSPIRATORIAL | NEUTRAL
    target_length:      Short(150–200w) | Medium(1100–1300w) | Long(2000–2400w)
    key_points:         string[]  // 4–6 items
    target_viewer:      string
    hook_variants:      string[]  // 3 A/B hook options
  }

  // ═══ BRIHASPATI OUTPUT ═══════════════════════════════════
  script:             string     // full [EMOTION]+SSML tagged script
  word_count:         int
  flesch_score:       float      // GATE: ≥ 60
  emotion_tag_counts: { ENERGETIC, CALM, SERIOUS, IMPACTFUL, CONSPIRATORIAL, NEUTRAL }
  dominant_emotion:   string     // most frequent tag → voice variant selector
  ssml_validated:     bool       // no chunk boundary splits

  // ═══ NATARAJA OUTPUT ═════════════════════════════════════
  emotion_curve_url:  "s3://bucket/jobs/{job_id}/emotion/emotion_curve.json"
  emotion_curve: [
    { t: float, emotion: string, intensity: float }  // 100ms windows
  ]
  dominant_emotion_confirmed: string
  audio_duration_sec: float

  // ═══ SARASWATI OUTPUT ════════════════════════════════════
  audio_files: {
    master:       HTTPS presigned URL  // NEVER s3:// raw
    calm:         HTTPS presigned URL
    energetic:    HTTPS presigned URL
    serious:      HTTPS presigned URL
  }
  selected_audio_url: HTTPS presigned URL  // chosen variant
  voice_variant:      master | calm | energetic | serious
  audio_chunk_count:  int   // if script > 4800 chars

  // ═══ BRAHMA OUTPUT ═══════════════════════════════════════
  background_prompts: [
    { scene_id: int, timestamp_start: float, timestamp_end: float,
      prompt: string, environment: string, color_grade: string,
      camera_angle: string, lighting: string }
  ]
  background_count:   int

  // ═══ TVASHTAR OUTPUT ════════════════════════════════════
  reference_photos: [
    { scene_id: int, photo_path: string, midjourney_prompt: string,
      dalle_prompt: string, negative_prompt: string }
  ]
  photos_generated:   int

  // ═══ VARUNA OUTPUT ═══════════════════════════════════════
  background_videos: [
    { scene_id: int, video_path: string, video_prompt: string,
      motion_type: string, duration_sec: float, tool_used: string }
  ]
  broll_ready:        bool

  // ═══ MAYA OUTPUT ════════════════════════════════════════
  thumbnail_prompt:   string     // full 8-layer cinematic prompt
  thumbnail_file:     string     // local path after generation
  broll_prompts:      string[]   // 3 additional B-roll scenes

  // ═══ VISHWAKARMA OUTPUT ═════════════════════════════════
  avatar_video_url:   "s3://bucket/jobs/{job_id}/avatar/raw.mp4"
  heygen_task_id:     string
  heygen_video_url:   string     // HTTPS, download IMMEDIATELY (7-day TTL!)
  render_duration_sec: float

  // ═══ RENDER-FORGE OUTPUT ════════════════════════════════
  final_1080p_url:    "s3://bucket/jobs/{job_id}/final/final_1080p.mp4"
  shorts_url:         "s3://bucket/jobs/{job_id}/final/shorts_1080x1920.mp4"
  cdn_1080p_url:      "https://cdn.shadowai.com/jobs/{job_id}/final_1080p.mp4"
  cdn_shorts_url:     "https://cdn.shadowai.com/jobs/{job_id}/shorts.mp4"
  render_cost_usd:    float      // ~$0.025 per render

  // ═══ SANJAY OUTPUT ═══════════════════════════════════════
  edit_decision_log:  object     // full EDL
  final_edited_video: string
  shorts_edited_video: string
  captions_srt:       string     // path to .srt file

  // ═══ AGNI OUTPUT ════════════════════════════════════════
  master_edited_video: string    // full post-production final
  sound_design_log:   object
  zoom_cuts:          int
  broll_insertions:   int
  retention_score:    float      // 3-second rule compliance %

  // ═══ SHAKUNI OUTPUT ══════════════════════════════════════
  qa_score:           float      // GATE: ≥ 7.0 (target ≥ 0.80)
  lip_sync_score:     float      // GATE: ≥ 0.75 (Pearson correlation)
  phoneme_latency_ms: float      // GATE: ≤ 40ms
  ssim_score:         float      // GATE: ≥ 0.85
  emotion_r2:         float      // GATE: ≥ 0.80
  qa_verdict:         APPROVED | REVISE | REJECT
  rejection_codes:    string[]

  // ═══ GARUDA OUTPUT ═══════════════════════════════════════
  youtube_title:      string     // 50–60 chars, keyword-first
  description:        string     // 3-zone format
  tags:               string[]   // 20–30 tags, max 500 chars total
  chapters:           object[]
  publish_schedule:   datetime
  youtube_video_id:   string     // after upload
  quota_units_used:   int        // 1600 per upload, max 10000/day

  // ═══ GANESHA OUTPUT ══════════════════════════════════════
  performance_data: {
    ctr:                float    // TARGET: ≥ 6%
    avg_view_pct:       float    // TARGET: ≥ 50%
    avg_view_duration:  float    // seconds
    impressions:        int
    likes_ratio:        float
    comments:           int
    traffic_sources:    object
  }
  feedback_weights: {
    hook_template_update:     object
    emotion_variant_weight:   object
    pacing_profile_update:    object
    topic_category_weight:    object
  }
}
```

---

## QUALITY GATES SUMMARY (All Skills Must Enforce)

| Gate | Field | Threshold | Enforced By |
|---|---|---|---|
| Topic quality | `topic_score` | ≥ 6.0 | KRISHNA |
| Script readability | `flesch_score` | ≥ 60 | BRIHASPATI |
| Lip sync | `lip_sync_score` | ≥ 0.75 (deliver), ≥ 0.85 (target) | SHAKUNI |
| Phoneme latency | `phoneme_latency_ms` | ≤ 40ms | SHAKUNI |
| Frame realism | `ssim_score` | ≥ 0.85 | SHAKUNI |
| Emotion alignment | `emotion_r2` | ≥ 0.80 | SHAKUNI |
| Emotion accuracy | emotion classifier | ≥ 88% | NATARAJA |
| Voice similarity | MOS-SIM score | ≥ 4.2/5.0 | SARASWATI |
| Audio URL | format | HTTPS only, never s3:// | KRISHNA |
| QA gate | `qa_score` | ≥ 7.0 | ARUNA |
| Pipeline time | end-to-end | ≤ 45 minutes | ARUNA |
| Job success rate | delivery ratio | ≥ 95% (week 4+) | KRISHNA |
