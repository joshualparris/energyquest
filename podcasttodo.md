# Podcast Integration TODO

**Decision:** Add if this remains an active web game/app.
**Topic bank:** game development, systems design, the app's core theme, indie development, learning-through-games.

## TODO
- [ ] Curate about 25 Spotify episodes relevant to the active product/theme.
- [ ] Add a collapsed bottom dock: **🎧 Listen to a different game/learning podcast**.
- [ ] One tap selects/loads another episode; persist recent choices and avoid immediate repeats.
- [ ] Use Spotify embed/deep links without assuming autoplay.
- [ ] Hide/pause whenever game music, narration, TTS or important sound cues are active.
- [ ] Keep gameplay/learning interactions primary.
- [ ] Keep episode data separate from game logic and easy to update.
- [ ] Add mobile/a11y and audio-conflict/persistence tests.

## Shared direction
Use the reusable **Josh Podcast Dock** pattern rather than a bespoke media implementation.
