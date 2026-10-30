# Hey Sam — Melody Trainer

An iPhone-first, hands-free ear-training application for acoustic/electric guitar, mandolin, and mandola.

## Prototype v0.1

Open `index.html` in a browser and tap **Start session**. No installation or server is required. The prototype uses Web Audio for a synthesized melody and a short, woody-style click with a higher-pitched downbeat. It includes key, note count, scale, octave span, rhythm, meter, tempo, count-in, independent volume controls, melodic difficulty, cadence, and playback modes.

**Limitations:** This is an exploratory browser prototype, not a finished timing engine. Browser scheduling and audio output vary, especially on iPhone. Voice commands, microphone grading, real-instrument pitch detection, automatic advancement, preset persistence, and relative-pitch prompts are not yet implemented. `STOP MELODY` prevents future scheduled phrases but does not cancel notes already scheduled. Tempo changes may cause a transient timing discontinuity. Changes to key, meter, and other generation settings should be made before starting a new session. The visual note display is for debugging and will be hidden by default in the final app.

## Repository setup

Create a GitHub repository named `hey-sam-melody-trainer`, upload the files in this folder, and commit them. Keep the repository private initially. Use GitHub's file browser on iPhone for review; use Windows for longer edits. A Mac with a current compatible Xcode version will be needed for native iOS builds, unless using a cloud Mac/build service.

## Next engineering milestones

1. Build a deterministic musical transport with sample-accurate beat scheduling, phrase boundary transitions, and cancellable notes.
2. Move phrase generation into a testable pure module with reproducible random seeds and musical constraints.
3. Implement a native SwiftUI front end and AVAudioEngine playback.
4. Add offline small-vocabulary voice commands and investigate custom wake phrase “Hey Sam.”
5. Add monophonic pitch tracking, onset detection, grading, and automatic advancement.
6. Add relative-pitch prompts, saved presets, adaptive practice, and optional chord progressions.

See `SPEC.md` for the full agreed product requirements.
