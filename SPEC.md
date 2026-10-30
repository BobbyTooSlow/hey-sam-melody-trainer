# Hey Sam — Functional specification v0.1

## Product goal
Hands-free melody imitation and relative-pitch practice on real acoustic/electric guitar, mandolin, and mandola. User configures a session before playing, then interacts through spoken commands without putting down the instrument. Intermediate player is the initial target.

## Session configuration
- Instrument: guitar (acoustic/electric), mandolin (acoustic/electric), mandola (acoustic/electric). Standard tuning defaults; support alternate tunings later.
- Key: all 12 major tonics initially; minor modes can be added later.
- Phrase length: configurable number of sounded notes, initially 2–16.
- Meter: 4/4 or 3/4.
- Tempo: adjustable; default 80 BPM.
- Metronome: continuous woody clicks, with higher-pitched beat 1. Independent volume relative to melody. Count-in: 0, 1, or 2 measures.
- Note durations: quarter only; quarter + half; eighth + quarter + half. Rests disabled initially.
- Pitch range: one or two octaves, inclusive of upper tonic. Major scale has seven unique degrees and eight ascending pitches with octave; pentatonic five degrees and six ascending pitches; triad three degrees and four ascending pitches.
- Pitch sets: major scale, major pentatonic, tonic major triad; extensible.
- Starting pitch: tonic, any tonic-triad tone, or any allowed pitch.
- Cadence: tonic, tonic-triad tone, open-ended, or unrestricted.
- Melodic difficulty: easy (mostly steps), medium, hard, unrestricted; optionally cap maximum leap.
- Playback: loop continuously; once with continuing clicks; alternate one phrase-length playback slot and one equally long metronome-only slot.
- Advancement: user-controlled or automatic upon accurate performance (requires grading).
- Feedback: spoken, simple sound, or self-assessment; no mandatory on-screen interaction.
- Relative pitch: after hearing the phrase, offer starting pitch and optionally announce scale degree, note name, both, or neither. Later: starting-note-only challenges.
- Optional chord-progression accompaniment: future release.

## Transport and voice behavior
- A shared beat timeline governs melody and clicks. The metronome continues through playback gaps, phrase repeats, and STOP MELODY.
- Mode changes requested during playback are applied at the next phrase boundary; changes must not cut off a sounding phrase.
- Count-in occurs at session start and when explicitly requested, with count-in behavior for AGAIN/NEXT to be configurable after testing.
- Commands: HEY SAM AGAIN, SLOWER, FASTER, NEXT, PLAY, HINT, ANSWER, STOP MELODY, STOP ALL, CONTINUE, REPEAT, LOOP, ONCE, ALTERNATE, SAME SPEED, COUNT IN.
- STOP MELODY: silence melody while clicks continue. STOP ALL: stop both. CONTINUE behavior should be defined by usability tests (resume on next downbeat recommended).
- “Hey Sam” is an app-local wake phrase while a practice session is active, not a replacement for system Siri. Offline recognition preferred; test guitar interference and iOS microphone/audio routing constraints.
- Tempo changes should take effect at musically meaningful boundaries.

## Melody generation
- Generate musical rather than unconstrained random phrases; prefer stepwise movement with difficulty-dependent leaps, occasional direction changes, and selected cadence.
- Respect selected scale degrees, octave span, start pitch, note count, rhythmic durations, and cadence constraints. Resolve impossible combinations explicitly.
- Schedule phrase duration in beats; round up to full measures when necessary so repeat/alternate slots align with the metronome. Pad with silent time, not necessarily explicit rests in the generated melody.
- Keep pitch identity distinct from fingerings; grade sounding notes, not fret positions.

## Evaluation (later phase)
- Microphone-based monophonic pitch and onset detection; tolerate doubled courses, strong harmonics, acoustic room noise, amplified guitar, and variable sustain.
- Compare pitch order, onset timing, duration, and optionally octave equivalence; calibrate latency and allow timing tolerance.
- Automatic advancement only when grading is reliable and a configured threshold is reached.

## Implementation strategy
- Native iOS target: SwiftUI, AVAudioEngine/Core Audio, local speech/wake-word components where feasible.
- Start with browser proof-of-concept to validate melody and transport behavior without requiring a Mac.
- Keep source, documentation, tests, and issue history in GitHub; repository private initially.

## Explicitly deferred or undecided
- Exact wake-word implementation and availability under background/locked-screen conditions.
- Whether metronome should continue while app is backgrounded, under interruption, or while the phone is locked.
- Precise automatic grading tolerances, calibration, and microphone/headphone recommendations.
- How count-in and phrase resets behave after NEXT, AGAIN, and STOP MELODY.
- Chord progressions, alternate tunings, minor scales, and cloud sync.
