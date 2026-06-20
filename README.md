# apache-kafka-reels

Content for the **Apache Kafka** topic in [graphl-mobile](../graphl-mobile) — the
technical reels PWA. The app fetches this content at runtime; it is not bundled
into the app.

## Structure

```
scenes/   # <stem>.ts (or .json) — SceneSpec data: nodes/edges/grid for one reel
tts/      # <stem>.tts — plain spoken prose (no markdown/code) for ChatterboxTTS
audio/    # <stem>.wav — generated narration, committed and served via raw GitHub
```

One reel = one `<stem>` shared across the three folders (e.g. `kafka-topics.ts`,
`kafka-topics.tts`, `kafka-topics.wav`). A scene's `audio` field defaults to its `id`.

`.wav` files are generated from `.tts` via local ChatterboxTTS (see
`graphl-mobile/CLAUDE.md`), then committed here so the app can load them.
Target up to ~5 min (~650–780 words) per scene — cover a concept and its parts in depth.
