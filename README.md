# 🤖 Robot Voice FM-Synth

A browser-based synthesizer for non-verbal robot vocalizations — think expressive
beeps, chirps, and trills that communicate emotion without dialogue. Built entirely
with the Web Audio API: no backend, no build step, no dependencies.

**[Live demo](#)** · Open `index.html` in any modern browser — that's it.

---

## Look & feel

Dark, plugin-style UI with custom knob controls and a fixed, grid-aligned layout
(Text → Voice / Character archetype / Info up top, Emotion presets / Waveform
preview / Sequence builder in the middle, Body mechanics / Voice synth / Advanced
below) — the same underlying engine and parameters, styled to look and feel like
a real audio tool rather than a web form.

## Features

- 🎛️ **Full synthesis engine** — pitch, contour, vibrato, glide, unison/detune,
  stereo motion, and a separate "body mechanics" layer (servo, gear clicks, static)
- 🎭 **7 emotion presets** — Surprise, Agreement, Error, Joy, Sadness, Curious, Companion
- 🤖 **5 character archetype presets** — War Machine, Broken/Glitchy, Swarm/Hive,
  Friendly Companion, Sentry/Guardian. Unlike the emotion presets, picking an
  archetype doesn't just set sliders once — it stays selected as a persistent
  "who is this robot" layer. Every emotion preset you pick, and every phrase you
  generate from text afterward, gets reshaped to match that archetype's register,
  timbre, and body-mechanics signature, while the emotion/phrase still drives the
  expressive side (contour, energy, chirp count). Switching the archetype while an
  emotion is already selected instantly re-applies that emotion with the new
  archetype's character.
- 🗣️ **Text → Voice** — type a phrase and the synth analyzes tone (punctuation,
  word choice, syllable count) and generates a matching vocalization automatically,
  entirely with local heuristics — no API calls, no ML model
- 🧬 **Syllable archetypes** — every syllable is independently one of three pitch
  characters (blip / whistle / trill) combined with one of six amplitude gestures
  (rising / falling / arc / swell / pulse / stutter), so a phrase has real variety
  instead of one repeated tone
- ✂️ **Trim markers** — drag two handles on the waveform to select exactly which
  region plays and exports. The full sequence gets its own independent waveform
  and trim markers too, so you can play/export just part of an assembled sequence
- 🔗 **Sequence builder** — chain multiple sounds together with configurable gaps,
  reorder them, and export the whole sequence as one file
- 💾 **WAV export** — real 16-bit/44.1kHz `.wav` files, rendered client-side via
  `OfflineAudioContext`. Every exported file embeds a standard `LIST/INFO`
  metadata chunk (Software / Artist / Date / Comment describing the archetype,
  waveform, pitch, and contour used) — readable in Audacity, most DAWs, `ffprobe`,
  `exiftool`, etc.

## Quick start

No installation, no build tools, no server:

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPO.git
cd YOUR-REPO
open index.html   # or just double-click it
```

Or enable **GitHub Pages** for this repo (Settings → Pages → Deploy from branch →
`main` / root) and it's live at `https://YOUR-USERNAME.github.io/YOUR-REPO/`.

## How it works

Everything runs client-side with the [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API):

- **Synthesis**: oscillators with automated frequency/gain curves, no samples or
  audio files involved — every sound is generated mathematically at play time
- **Text analysis**: a lightweight heuristic engine (punctuation, capitalization,
  a small positive/negative word list, real syllable counting via vowel-group
  detection) maps text to synthesis parameters — no network requests, no ML
- **Export**: `OfflineAudioContext` renders the exact same audio graph offline,
  then a hand-written WAV encoder packages it as a downloadable file, with an
  optional `LIST/INFO` metadata chunk describing how the sound was generated

## Project structure

```
.
├── index.html   # everything — UI, styles, and the full synthesis engine
└── README.md
```

Single file by design — easy to fork, easy to read, easy to deploy anywhere.

## Browser support

Any modern browser with Web Audio API support: Chrome, Firefox, Safari, Edge.

## License

[PolyForm Noncommercial 1.0.0](https://polyformproject.org/licenses/noncommercial/1.0.0) —
free to use, run, and modify for non-commercial purposes. For commercial use
(including using the tool or its output in a commercial product), contact K.K.Sound.
See [`LICENSE`](./LICENSE) for the full text.

---

<p align="center"><sub>K.K.Sound</sub></p>
