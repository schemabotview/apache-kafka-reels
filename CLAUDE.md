# CLAUDE.md — apache-kafka-reels

Guidance for Claude Code when working in this repo. This is the **content** for
the **Apache Kafka** topic in [graphl-mobile](../graphl-mobile), the technical
reels PWA. The app fetches this content at runtime via raw GitHub; it is **not**
bundled into the app. Repo: `github.com/schemabotview/apache-kafka-reels`.

## Structure

```
scenes/   # currently EMPTY — SceneSpec data lives in graphl-mobile/src/data/scenes/<stem>.ts
tts/      # <stem>.tts — plain spoken prose (no markdown/code) for ChatterboxTTS
audio/    # <stem>.wav — generated narration, committed and served via raw GitHub
```

One reel = one `<stem>` shared across folders (e.g. `kafka-topics.tts`,
`kafka-topics.wav`). A scene's `audio` field defaults to its `id`.

## Pipeline (who does what)

1. **Scene** — author `graphl-mobile/src/data/scenes/<stem>.ts` and register it in
   `src/data/scenes/index.ts` (feed order = teaching order). `npm run build` is
   the only gate (runs DEV `validateLayout`). See `kafka-topics.ts` for the
   worked reference (flat `columns`).
2. **TTS** — write `tts/<stem>.tts` here: ~650–780 words (≈5 min), plain spoken
   prose, no markdown/code. Blank lines become ~300 ms pauses that pace reveals.
3. **Audio** — **the user** generates + pushes the `.wav` (Claude does not run
   the conda/audio/push step):
   ```bash
   # from ~/Apps/graphl-mobile:
   conda run -n chatterbox python scripts/generate_audio.py --topic apache-kafka
   ```
   Then commit + push the `.wav` here so it serves via raw GitHub.

## Scene index

Legend: ✅ scene + tts done · 🔊 audio generated · 🔲 not started. Order = feed /
teaching order.

| # | Stem           | Title             | Scene | TTS | Audio |
|---|----------------|-------------------|-------|-----|-------|
| 1 | `kafka-topics` | Topics & Partitions | ✅  | ✅  | 🔊    |

This topic is just getting started — add reels by following the pipeline above.
