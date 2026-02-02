## AI Content Architecture Diagrams

### 1) src/ai_content/ Package Structure

```mermaid
graph TD
	A[src/ai_content] --> B[core]
	A --> C[config]
	A --> D[providers]
	A --> E[pipelines]
	A --> F[presets]
	A --> G[integrations]
	A --> H[utils]
	A --> I[cli]

	B --> B1[registry.py]
	B --> B2[result.py]
	B --> B3[exceptions.py]
	B --> B4[job_tracker.py]

	C --> C1[settings.py]
	C --> C2[loader.py]

	D --> D1[google]
	D --> D2[aimlapi]
	D --> D3[kling]

	E --> E1[base.py]
	E --> E2[music.py]
	E --> E3[video.py]
	E --> E4[full.py]

	F --> F1[music.py]
	F --> F2[video.py]

	G --> G1[archive.py]
	G --> G2[media.py]
	G --> G3[youtube.py]

	I --> I1[main.py]
```

### 2) Providers Overview

```mermaid
graph TD
	P[ProviderRegistry] --> M[Music Providers]
	P --> V[Video Providers]
	P --> I[Image Providers]

	M --> L[Lyria (Google)]
	M --> MM[MiniMax (AIMLAPI)]

	V --> VE[Veo (Google)]
	V --> KL[Kling (KlingAI)]

	I --> IM[Imagen (Google)]
```

### 3) Pipelines

#### 3.1 Music Pipeline Workflows
```mermaid
flowchart TD
	M0[MusicPipeline] --> M1[Performance-First]
	M0 --> M2[Lyrics-First]
	M0 --> M3[Reference-Based]
	M0 --> M4[Provider Comparison]

	M1 --> M1a[Select preset]
	M1a --> M1b[Generate instrumental]

	M2 --> M2a[Parse/structure lyrics]
	M2a --> M2b[Generate vocals]

	M3 --> M3a[Reference audio URL]
	M3a --> M3b[Style transfer]

	M4 --> M4a[Run multiple providers]
	M4a --> M4b[Compare outputs]
```

#### 3.2 Video Pipeline Workflows
```mermaid
flowchart TD
	V0[VideoPipeline] --> V1[Text-to-Video]
	V0 --> V2[Image-to-Video]
	V0 --> V3[Provider Comparison]

	V1 --> V1a[Select preset]
	V1a --> V1b[Generate video]

	V2 --> V2a[Use image/keyframe]
	V2a --> V2b[Animate image]

	V3 --> V3a[Run multiple providers]
	V3a --> V3b[Compare outputs]
```

#### 3.3 Full Content Pipeline (Music Video)
```mermaid
flowchart TD
	F0[FullContentPipeline] --> F1[Generate music]
	F0 --> F2[Generate keyframe image]
	F1 --> F3[Generate video]
	F2 --> F3
	F3 --> F4[Merge audio + video]
	F4 --> F5[Local export]
	F5 --> F6[Optional upload]
```
