# ⚔ SHADOW AI EMPIRE — USER CONFIGURATION
## Fill in ALL fields below before running any pipeline.
## KRISHNA checks this file at boot. Missing fields = pipeline blocked.

---

## YOUR CHANNEL IDENTITY

CHANNEL_NAME: ""
# Example: "AI Empire Daily" or "Shadow Intelligence"

CHANNEL_PERSONA: ""
# How Claude writes your scripts. Example:
# "Intelligent, calm explainer for curious professionals aged 25–45.
#  Never condescending. Always insightful. Like a smart friend who works in AI."

CHANNEL_NICHE: ""
# Example: "AI tools and machine learning for non-technical audiences"

CHANNEL_LANGUAGE: "English"
# Primary language. Future: Hindi, Spanish, etc.

---

## VOICE CLONE (ELEVENLABS)

ELEVENLABS_VOICE_ID: ""
# Find at: elevenlabs.io → Voices → your cloned voice → copy ID
# Example: "21m00Tcm4TlvDq8ikWAM"

ELEVENLABS_API_KEY: ""
# Find at: elevenlabs.io → Profile → API Key
# Leave blank if using website method only

ELEVENLABS_MODEL: "eleven_multilingual_v2"
# Options: eleven_multilingual_v2 (recommended), eleven_monolingual_v1

---

## AVATAR (HEYGEN)

HEYGEN_AVATAR_ID: ""
# Find at: heygen.com → Avatars → your avatar → copy ID
# Example: "Daisy-inskirt-20220818"

HEYGEN_API_KEY: ""
# Find at: heygen.com → Account → API Key
# Leave blank if using website method only

HEYGEN_FALLBACK: "D-ID"
# Options: "D-ID" | "SadTalker" | "none"

---

## YOUTUBE CHANNEL

YOUTUBE_CHANNEL_ID: ""
# Find at: youtube.com → Your channel → About → Share → Copy channel ID
# Example: "UCxxxxxxxxxxxxxxxxxxxxxxxx"

YOUTUBE_DEFAULT_CATEGORY: "28"
# 28 = Science & Technology (recommended for AI channels)
# Other options: 27=Education, 22=People & Blogs

PUBLISH_TIMEZONE: "UTC"
# Your audience timezone for optimal publish times
# Examples: "America/New_York" | "Europe/London" | "Asia/Kolkata"

PUBLISH_SCHEDULE: "Mon,Wed,Fri"
# Days of the week to publish

DEFAULT_PUBLISH_TIME: "14:00"
# UTC time to publish (adjust based on your audience location)

CHANNEL_CTA: "Subscribe for weekly AI insights you won't find anywhere else."
# The call-to-action text at the end of every video

---

## CONTENT DEFAULTS

DEFAULT_VIDEO_LENGTH: "Medium"
# Options: Short (150–200w), Medium (1100–1300w), Long (2000–2400w)

DEFAULT_HOOK_TYPE: "CURIOSITY_GAP"
# Options: CURIOSITY_GAP | SHOCK_STAT | OPEN_LOOP | CONSPIRATORIAL | IDENTITY
# Will be updated by GANESHA based on performance data

DEFAULT_EMOTION: "ENERGETIC"
# Default dominant emotion. GANESHA will update based on watch time data.

---

## CINEMATIC SETTINGS (for BRAHMA, TVASHTAR, MAYA)

DEFAULT_BACKGROUND_STYLE: "Futuristic Tech Studio"
# Options from BRAHMA: "Futuristic Tech Studio" | "Editorial Office" | 
# "Research Lab" | "Executive Boardroom" | "Abstract Data Space"

DEFAULT_COLOR_GRADE: "INNOVATION/AI"
# Options: TRUST/AUTHORITY | INNOVATION/AI | PREMIUM/DARK | NEON FUTURIST

IMAGE_GENERATION_TOOL: "Midjourney"
# What you use for images: "Midjourney" | "DALL-E 3" | "Adobe Firefly" | "Leonardo"

VIDEO_GENERATION_TOOL: "Pika"
# What you use for bg videos: "Runway" | "Pika" | "Kling" | "ComfyUI"

---

## COST TRACKING

MONTHLY_BUDGET_USD: "51"
# $22 ElevenLabs Creator + $29 HeyGen Creator = $51 base
# Adjust if on different plans

ELEVENLABS_PLAN: "Creator"
# Free | Creator ($22) | Pro ($99) | Scale ($330)

HEYGEN_PLAN: "Creator"
# Free | Creator ($29) | Team ($89)

---

## PERFORMANCE TARGETS (GANESHA gates)

TARGET_CTR: "6.0"
# Percentage. GANESHA flags if below this.

TARGET_WATCH_TIME_PCT: "50"
# Percentage of video watched. GANESHA flags if below this.

TARGET_SUBSCRIBER_GROWTH: "500"
# Net new per month after Month 3.
