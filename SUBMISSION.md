# SUBMISSION

## Environment setup

- **APIs configured:**
  - Google Gemini (GEMINI_API_KEY): **[add status]**
  - AIMLAPI (AIMLAPI_KEY): **[add status]**
- **CLI verification:**
  - `uv run ai-content --help`
  - `uv run ai-content list-providers`
  - `uv run ai-content list-presets`

## Codebase exploration

- **Architecture:** See [ARCHITECTURE.md](ARCHITECTURE.md).
- **Providers:**
  - Music: Lyria (instrumental, realtime), MiniMax (vocals/lyrics, reference audio)
  - Video: Veo (fast, image-to-video), Kling (high quality, image-to-video)
- **Presets:**
  - Music: jazz, blues, ethiopian-jazz, cinematic, electronic, ambient, lofi, rnb, salsa, bachata, kizomba
  - Video: nature, urban, space, abstract, ocean, fantasy, portrait

## Generation log

> Add your exact commands, prompts, and outputs below.

### Audio (instrumental)

- **Command:**
  - `uv run ai-content music --style jazz --provider lyria --duration 30`
- **Prompt:** preset: `jazz`
- **Output file:** **[path]**
- **Result:** **[success/failure]**

### Audio (vocals) — optional (MiniMax)

- **Command:**
  - `uv run ai-content music --prompt "..." --provider minimax --lyrics path/to/lyrics.txt`
- **Prompt:** **[text]**
- **Lyrics file:** **[path]**
- **Output file:** **[path]**
- **Result:** **[success/failure]**

### Video

- **Command:**
  - `uv run ai-content video --style space --provider veo --duration 5`
- **Prompt:** preset: `space`
- **Output file:** **[path]**
- **Result:** **[success/failure]**

### (Bonus) Music video merge

- **Command:**
  - `ffmpeg -i video.mp4 -i music.wav -c:v copy -c:a aac -shortest output.mp4`
- **Output file:** **[path]**
- **Result:** **[success/failure]**

## Challenges and solutions

- **Veo SDK mismatch:**
  - **Issue:** `GenerateVideoConfig` and `generate_video` not found in `google-genai`.
  - **Fix:** Updated to `GenerateVideosConfig` and `generate_videos` in [src/ai_content/providers/google/veo.py](src/ai_content/providers/google/veo.py).
- **Veo personGeneration invalid:**
  - **Issue:** `allow_adult` not supported.
  - **Fix:** Set default to `dont_allow` in [src/ai_content/providers/google/veo.py](src/ai_content/providers/google/veo.py).

## Insights and learnings

- Provider SDKs can change quickly; pinning or adapting to API changes is essential.
- Presets are an efficient way to get quality outputs quickly.
- The pipeline layer provides reusable workflows above raw providers.

## YouTube links

- **Video 1:** **[link]**
- **Video 2:** **[link]**

## Optional: screenshots

- **Screenshot 1:** **[path or link]**
- **Screenshot 2:** **[path or link]**
