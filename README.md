# JOY-PLOTTER

A real-time, highly customizable audio visualizer inspired by the CP-1919 radio pulses.
Joy-plotter generates stacked ridgelines that breathe data from audio files, live MIDI, or hardware line-in.
Built in Unity (URP) with a GPU-driven plot, a MilkDrop-style feedback canvas, a palette-quantizing dither composite, a full modulation matrix, and a preset playlist for hands-off sets.

## Quick start

1. Launch the app. The settings menu opens on the **INPUT** tab.
2. Press **LOAD**, pick an audio file (WAV, OGG, or MP3), and it plays
   immediately.
3. Press **Tab** to hide the menu and let the plot fill the screen.

### Controls

| **Tab** | Close the topmost window first (file browser, mod route popup, credits), then the settings menu | \
| **Escape** | Same close-first flow (or cancel a key capture) | \
| **Ctrl+Z / Ctrl+Y** | Undo / redo parameter changes (menu open) | \
| **Space / Backspace** | Next / previous playlist preset (menu closed) | \

Quit via the **QUIT** button (click twice). **HELP** opens this document;
**CREDITS** shows the credits popup.

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

- Note: Some settings will force the plot to reinitialize, resulting in a
  momentary burst of spectrum-wide band peaks.
- **The M button** on a row adds a modulation route targeting that
  parameter and jumps to the MODS tab with the route open — any slider,
  toggle, or dropdown can dance to the music.
- **XY pads** (Slide, Stretch, Focal Point, Lens Slide) edit two related
  parameters with one drag. Type exact values into the X / Y boxes, or
  press **RESET** to return both axes to their defaults. A coral dot rides
  the pad at the live modulated position while a route drives either axis.

## Input modes

**Audio** — visualizes the app's own output mix, fed by the built-in file
player. **Midi** — visualizes live MIDI notes (each note excites the bands
around its pitch, with synthesized harmonics). **Line-In** — a hardware
input device via LASP (desktop builds only). Controls that only apply to an
inactive mode appear dimmed; hover them to see why.

---

## Parameter reference

### AUDIO tab

**Processor** — shapes the spectrum before it becomes geometry.

- **Input Gain** (0.1–8) — master sensitivity. Raises the whole plot's
  response to the source; too high flattens everything against the height
  cap, too low leaves the plot sleepy.
- **Attack Rate** (1–60) — trigger rate of a note.
- **Release Rate** (0.5–30) — release rate of the note.
- **Norm. Adapt Time** (2–30 s) — how fast the "typical level" reference
  adapts. This calibrates every audio-reactive mod source: 1.0 means
  "as loud as usual".

**Capture** *(Audio mode)*

- **Capture Gain** (0.1–8) — level of output mix feeding the visualizer.

**Line-In** *(Line-In mode)*

- **Floor Gate** (0–1) — zeroes bands at or below the threshold and
  re-normalizes the survivors. Cleans noise-floor hiss and broadband
  splash at the source.

**MIDI** *(Midi mode)*

- **MIDI Gain** (0.1–4) — overall strength of note (considering velocity).
- **Harmonics** (1–32) — harmonic count generated per note.
- **Harm. Rolloff** (0.2–2) — how quickly those overtones fade with order.
- **Band Spread** (0.1–6 semitones) — width of the region each note triggers.
- **Note Attack / Note Release** (1–60 / 0.5–30) — per-note envelope.
- **Velocity Floor** (0–1) — minimum response for the softest notes, so
  gentle playing still registers.

### WAVE tab

**Shape** — **These rebuild the plot when changed.**

- **Active Bands** (32–512) — how many ridgelines are drawn. Fewer = bold,
  poster-like lines; more = a dense woven field.
- **Top / Bottom Padding** (0–128) — flat, silent rows framing the active
  region above and below, for composition breathing room.

**Response** — how band energy becomes line height.

- **Dynamic Baseline** — adaptively tracks and removes the noise floor. Usually on.
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
  actually see.

**Geometry**

- **X Resolution** (64–512) — points per line. Low = angular, vectorized
  lines; high = smooth curves. **Rebuilds the plot.**
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
  fills preview the composite color live. (Color is applied at the palette
  composite — sources feed the canvas as grayscale ink.)

### POST-FX tab

Material-level styling of the rendered lines, plus the palette-quantizing
composite that gives the whole image its printed identity.

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

**Palette Dither** — the final composite. Every on-screen pixel is snapped
to a fixed palette swatch; only ink *density* is dithered, never color, and
the dither grid stays screen-aligned even while the canvas rotates
underneath it. The other dither rows unlock while it's enabled.

- **Palette Dither** — the on/off. Also disables FXAA while on
  (post-dither smoothing would smear the grid).
- **Dither Style** — **Pattern** (ordered Bayer) or **Halftone Cells**
  (print-style dots).
- **Pixel Size** (1–16) — size of the virtual pixels/cells. Big = chunky
  riso poster, small = fine newsprint.
- **Dither Spread** (0–1) — how much the pattern perturbs the quantization;
  0 = hard posterization bands.
- **Palette Mapping** — **Nearest Color**, **Luminance Ramp** (brightness
  indexes the palette), or **Ink Separation** (per-channel plates).
- **Palette Size** (2–12) — how many swatches are in play. 2 = two-tone
  print.
- **Background Swatch** (0–11) — which swatch reads as "paper".
- **Ink Shading** — **Flat**, **Steps**, or **Modulate** — how ink density
  shades within a swatch.
- **Shade Amount** (0–1) — depth of that shading.
- **Ramp Black / White Point** (0–0.5 / 0.5–1) and **Ramp Contrast**
  (0.5–4) — the tone ramp feeding the mapping.

### CANVAS tab

The feedback canvas — the MilkDrop-style motion engine. Everything here
warps the **retained image**, so the Trails amount is the master: at 0 the
canvas shows only the current frame and the motion controls have nothing to
move. That's what the **Lens** section at the bottom is for — motion that
needs no trails at all.

**Trails**

- **Trails** (0–1) — how much of the previous frame survives into this one.
  0 = off (identical to no canvas); ~0.9+ = long echo trails.
- **Trail Fade** (0–4) — extra drain per second. Higher = shorter trails.
- **Fade Pattern / Amount** — shapes *where* trails dissolve (Radial,
  Angular, Horizontal, Vertical, Noise) — patchy smoke, edge burn-off, etc.

**Zoom / Spin / Slide** — per-second motion applied to the trail image.
Each has a base rate plus a **Pattern** (a spatial field) and **Pattern
Amount** that vary the rate per-pixel — the difference between a flat zoom
and a bulging tunnel.

- **Zoom Flow** (0.5–2) — multiplicative zoom per second. Above 1 expands
  (tunnel), below 1 sucks inward.
- **Spin** (−180–180 °/s) — rotation of the trail image around the focal
  point.
- **Slide** (XY pad, ±0.5/s) — directional drift.

**Stretch & Focus**

- **Stretch** (XY pad, 0.5–2) — anisotropic scaling per second.
- **Focal Point** (XY pad, 0–1) — where the zoom/spin motion centers.

**Pattern Shape**

- **Pinwheel Spokes** (1–8) 
- **Turbulence Scale / Speed** — Noise frequency

**Lens** — a second warp applied to the *final* image
every frame (Final pass.)

- **Lens Zoom** (0.5–2)
- **Lens Angle** (−180–180)
- **Lens Spin** (−180–180 °/s)
- **Lens Slide** (XY pad, ±0.5)
- **Lens Pattern / Amount** 

### IMAGE tab

Imported images affect band brightness based on image source. Controls unlock once an image is loaded, and
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

### MAPS tab

Bind keyboard keys and MIDI to parameters for live performance.

- **Keyboard** — capture a key (or chord) and attach it to any parameter
  with a step size; keys repeat while held. Notes and keys nudge values in
  steps.
- **MIDI CC** — absolute control: the knob position *is* the value (no undo
  history, by design).
- **MIDI notes** — step/direction triggers, like keyboard keys.

Mapped keys stay live while the menu is open — except while a modal file
browse is up, or while typing in a text field.

### MODS tab

The modulation matrix: **routes** that push audio (and generator) signals
into any parameter, live. A route adds its signal *on top of* the slider's
base value — sliders, presets, and undo always see the base; the coral tick
on a slider (and the coral dot on a pad) shows the live modulated value.

Each route row: an **activity dot** (glows with the route's envelope), the
**target picker**, a **gear** opening the detail popup, and **remove**. The
**+** button adds a route; row **M buttons** all over the settings are a
shortcut that pre-targets one.

**Route settings** (gear popup):

- **Target** — any parameter (mod settings themselves excluded).
- **Source** — **Low / Mid / High / Overall** (band energy vs. typical
  level — rests at zero during ordinary passages), **Centroid** (spectral
  brightness), **Onset** (drum-hit trigger), **LFO**, **Accumulator**.
- **Slot** — which LFO / accumulator (4 of each, shared by all routes).
- **Curve** — Linear, Exponential (emphasizes peaks), Threshold (on/off
  above a level), Smoothstep, Inverse.
- **Depth** (−1–1) — signed fraction of the target's range at full signal.
- **Attack / Release** — the route's own envelope.
- **Enable** — mute the route without losing its settings.

The **LFO section** (shown when the source is an LFO) edits the *shared*
slot — rate, shape (Sine / Triangle / Saw / Square / Noise), phase — with a
live scope drawing exactly the waveform the engine runs. **Accumulators**
integrate a source over time (fill rate / decay) for slow builds.

The onset detector's **Onset Threshold** and every LFO / accumulator
setting are ordinary parameters: preset-saved, undoable, and MIDI-mappable.

### PRESETS tab

Save, load, and delete complete looks — every parameter plus the full
modulation route list. Loading replaces everything, including "no
modulation" if the preset was saved that way.

**Playlist** — a MilkDrop-style set list.

- **ADD** appends the preset selected in the dropdown; **REMOVE / UP /
  DOWN** edit the list; **PREV / NEXT** move through it. The list persists
  between launches.
- **Space / Backspace** advance/rewind while the menu is closed.
- **Transition Time** (0–30 s) — presets *crossfade in parameter space*:
  smooth values glide, stepped values (band counts, modes, toggles) and the
  route list swap at the midpoint. 0 = hard cut. Active modulation keeps
  riding on top of the moving values through the whole transition.
- **Hold Time** (1–300 s) + **Auto Advance** — hands-off playback. Manual
  advances restart the hold timer.

Playlist timing is deliberately **not** saved inside presets — a preset
can't retime or stop the set that's playing it.

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
LASP and Minis Packages by [Keijiro Takahashi](https://github.com/keijiro) for Audio & Midi Signal Processing.
