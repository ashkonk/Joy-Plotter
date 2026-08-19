# JOY-PLOTTER

A real-time, highly customizable audio visualizer inspired by the CP-1919 radio pulses.
Joy-plotter generates stacked ridgelines that breathe data from audio files, live MIDI, or hardware line-in. 
Built in Unity (URP) with a GPU-driven plot, configurable graphics, post processing, and image overlay feature.

## Quick start

1. Launch the app. The settings menu opens on the **INPUT** tab.
2. Press **LOAD**, pick an audio file (WAV, OGG, or MP3), and it plays
   immediately.
3. Press **Tab** to hide the menu and let the plot fill the screen.

### Controls

| **Tab** | Toggle the settings menu | \
| **Escape** | Close the menu (or cancel a key capture) | \
| **Ctrl+Z / Ctrl+Y** | Undo / redo parameter changes (menu open) | \

Quit via the **QUIT** button (click twice).


### Supported files

- **Audio**: WAV (uncompressed PCM), OGG Vorbis, MP3.
- **Images** (for the image mask): PNG, JPG.

---

## Demos
- <img width="426" height="240" alt="Image Overlay" src="https://github.com/user-attachments/assets/cac4373c-f857-4d93-a71a-7fa02f76c48c" />
- <img width="426" height="240" alt="Logo Fade-in" src="https://github.com/user-attachments/assets/5824c569-4708-4135-bc64-528b019a235e" />
- <img width="2559" height="1439" alt="Depth Offsetting / Height Gradient" src="https://github.com/user-attachments/assets/ce8bf651-89d2-4228-af28-b826bc759f53" />

---

# SETTINGS

## Input modes

**Audio** — visualizes the app's own output mix, fed by the built-in file
player. **Midi** — visualizes live MIDI notes (each note excites the bands
around its pitch, with synthesized harmonics). **Line-In** — a hardware
input device via LASP (desktop builds only). Controls that only apply to an
inactive mode appear dimmed; hover them to see why.

---

## Parameter reference

Every slider below is also available for key mapping, and everything is
clamped to a safe range — feel free to experiment. Ranges in parentheses are
the UI limits.

### AUDIO tab

**Processor** — shapes the spectrum before it becomes geometry.

- **Input Gain** (0.1–8) — master sensitivity. Raises the whole plot's
  response to the source; too high flattens everything against the height
  cap, too low leaves the plot sleepy.
- **Attack Rate** (1–60) — how fast the spectrum *rises* toward new energy.
  High = snappy, percussive response; low = swells that lag the music.
- **Release Rate** (0.5–30) — how fast it *falls* when energy stops. Low
  values leave long, smoky decays; high values make the plot twitchy and
  literal.

**Capture** *(Audio mode)*

- **Capture Gain** (0.1–8) — level of the captured output mix feeding the
  visualizer. Use it to balance quiet files without touching playback
  volume.

**MIDI** *(Midi mode)*

- **MIDI Gain** (0.1–4) — overall strength of note excitation.
- **Harmonics** (1–32) — overtones synthesized per note. Few = clean single
  bumps at the fundamental; many = bright, harmonically rich ridges that
  climb the plot.
- **Harm. Rolloff** (0.2–2) — how quickly those overtones fade with order.
  Low keeps upper harmonics strong (buzzy); high concentrates energy at the
  fundamental (round).
- **Band Spread** (0.1–6 semitones) — width of the region each note
  excites. Narrow = needle spikes; wide = hills that merge between
  neighboring notes.
- **Note Attack / Note Release** (1–60 / 0.5–30) — per-note envelope: how
  fast a keypress blooms and how long it lingers after release.
- **Velocity Floor** (0–1) — minimum response for the softest notes, so
  gentle playing still registers.

### WAVE tab

**Shape** — the plot's skeleton. These rebuild the plot when changed.

- **Active Bands** (32–512) — how many ridgelines are drawn. Fewer = bold,
  poster-like lines; more = a dense woven field.
- **Top / Bottom Padding** (0–128) — flat, silent rows framing the active
  region above and below, for composition breathing room.

**Response** — how band energy becomes line height.

- **Dynamic Baseline** — adaptively tracks and removes the noise floor so
  quiet hiss doesn't haze the plot. Usually on.
- **Baseline Subtract** (0–1) — how much of that floor is removed. Higher =
  cleaner silence, but can swallow quiet detail.
- **Dynamic Boost** (0.5–6) — amplification applied after subtraction.
  Restores contrast; the "make it punchy" knob.
- **Response Gamma** (0.25–2) — response curve. Below 1 lifts quiet detail
  (busier plot); above 1 suppresses it so only peaks speak.
- **Noise Floor Lift** (0–0.2) — a faint constant ripple so lines never go
  dead flat during silence. A little keeps the plot feeling alive.
- **Edge Falloff** (0–64 bands) — tapers the outermost ridgelines toward
  silence so the active region fades out instead of ending abruptly.

**Ambient Motion** — idle life, independent of audio.

- **Ambient Wobble** (0–0.15) — amplitude of a slow organic undulation
  across all lines.
- **Wobble Speed** (0–3) — how fast that undulation cycles.
- **Drift Speed** (0–3) — slow sideways migration of the wobble pattern, so
  the idle motion never visibly loops.

### VISUAL tab

**Envelope**

- **Band Attack / Band Release** (1–60 / 0.5–30) — the smoothing you
  actually *see*: per-ridge rise and fall speed, downstream of the audio
  envelope. This pair dominates the plot's perceived snappiness.

**Geometry**

- **X Resolution** (64–512) — points per line. Low = angular, vectorized
  lines; high = smooth curves. Rebuilds the plot.
- **Packet Width** (0.05–2) — horizontal spread of each energy bump. Narrow
  reads as spikes, wide as rolling swells.

**Ripples** — transient-triggered motion.

- **Transient Ripples** — on/off for onset-driven ripples that spawn at
  hits and travel outward along the lines.
- **Ripple Threshold** (0.01–1) — how hard a transient must hit to spawn a
  ripple. Low = every tick ripples; high = only big accents.
- **Ripple Speed** (0.1–6) — outward travel speed.
- **Ripple Travel** (0–20) — how far a ripple journeys before dying.
- **Ripple Decay** (0–4) — how quickly a ripple loses height as it travels.
- **Ripple Lifetime** (0.2–10 s) — maximum age before a ripple is retired.

**Tone**

- **Visual Gamma** (0.3–2.5) — display response curve applied to heights.
- **Visual Gain** (0.1–4) — display multiplier on heights.
- **Max Wave Height** (0.2–12) — hard ceiling on line height. Low keeps the
  classic tidy stack; high lets peaks tower and overlap dramatically.

**Framing**

- **Fit Width / Fit Height** (0.3–1.5) — scale factors on the auto-fit that
  frames the plot in the camera. Below 1 adds margin; above 1 overfills.
- **Depth Offset** (0–0.1) — spacing between successive ridgelines in
  depth. Compresses or stretches the stack.
- **Horizontal Slope** (−0.05–0.05) — skews rows sideways as they recede,
  tilting the whole formation into a parallax slant.

**Line Color**

- **Line Red / Green / Blue** (0–1) — the line color. The three slider
  fills preview the composite color live.

### POST-FX tab

Material-level styling of the rendered lines.

**Line Style**

- **Line Thickness** (0–0.95) — stroke weight of every ridgeline.
- **Peak Glow** (0–5) — brightness boost at wave crests; high values bloom.
- **Height Gradient** (0–1) — intensity ramp by height, so tall peaks read
  hotter than the baseline.
- **Peak Thickness** (0–4) — how far the peak treatment extends down from
  each crest.
- **Depth Fade** (0–1) — dims lines as they recede, adding atmosphere and
  depth separation.
- **Aggregate Glow** (0–4) — a whole-plot glow that pulses with overall
  energy. The "the drop hits and everything lights up" control.

**Fill**

- **Fill Mode** — treatment of the area under each line: **Solid**,
  **Gradient** (fades downward), **Scanlines**, or **Dither** (Bayer
  ordered dithering — screen-print texture).
- **Fill Ink** (0–1) — fill density/opacity.
- **Fill Falloff** (0.05–1) — how quickly the fill fades below the line.
- **Fill Depth Lift** (0–0.5) — brightens fills on distant rows so they
  don't vanish into the depth fade.
- **Scanline Pitch** (2–16) — spacing of the scanline / dither pattern.

### IMAGE tab

Load an image (INPUT tab) and its brightness sculpts the plot — the classic
"face in the waveform" trick. Controls unlock once an image is loaded, and
clearing the image restores all of these to defaults.

- **Height Influence** (0–2) — how strongly image brightness adds to wave
  height. The primary control.
- **Audio Gate** (0–1) — makes the image reveal itself *with the music*:
  louder audio exposes more of the image.
- **Gate Floor** (0–1) — minimum image visibility when audio is quiet.
- **Black Level** (0–0.5) — brightness treated as zero. Raise to remove
  murky backgrounds from the silhouette.
- **Contrast** (0.25–4) — steepens or flattens the image's tonal range.
- **Active Region Only** — maps the image to the active bands only,
  excluding the padding rows.
- **Flip Vertically** — for images that arrive upside down.

### PRESETS tab

Unreleased

### MAPPING tab

Unreleased

---

## Known issues

- **WAV support is limited to uncompressed PCM.** Unity's runtime loader
  can't decode WAV files written with compressed codecs. Joy-plotter will
  refuse them with the codec named in the status line. Fix: re-export as
  16-bit PCM WAV (Audacity: File → Export → WAV, "Signed 16-bit PCM"), or
  use OGG/MP3.

Found something else? Open an issue!

---

## License / credits

Built by Ashkon Khalkhali using Unity (URP).
LASP and Minis Packages by [Keijiro Takahashi](https://github.com/keijiro) Audio & Midi Signal Processing.
Visual style inspired by Harold Craft's CP-1919 pulsar plots.
