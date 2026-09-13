# JOY-PLOTTER

JOY-PLOTTER is a stylized, highly configurable audio visualizer.

This guide follows the settings menu.
Jump to: [INPUT](#input-tab) · [AUDIO](#audio-tab) · [WAVE](#wave-tab) · [VISUAL](#visual-tab) · [POST-FX](#post-fx-tab) · [CANVAS](#canvas-tab) · [MEDIA](#media-tab) · [MAPS](#maps-tab) · [MODS](#mods-tab) · [PRESETS](#presets-tab)

## Quick start

1. On **INPUT**, choose **Audio**, press **LOAD**, and select a WAV, OGG, or MP3 file. Playback starts automatically.
2. On **PRESETS**, select a look and press **LOAD**, or adjust the settings below.
3. Switch to **MODE: EDIT** to work on a look without the playlist changing it.
4. Press **Tab** to hide the menu. Press it again to bring it back.

## Demos

- <img width="426" height="240" alt="Image Overlay" src="https://github.com/user-attachments/assets/cac4373c-f857-4d93-a71a-7fa02f76c48c" />
- <img width="426" height="240" alt="Logo Fade-in" src="https://github.com/user-attachments/assets/5824c569-4708-4135-bc64-528b019a235e" />
- <img width="2559" height="1439" alt="Depth Offsetting / Height Gradient" src="https://github.com/user-attachments/assets/ce8bf651-89d2-4228-af28-b826bc759f53" />

## INPUT tab

- **Audio** - uses the app's audio player.
- **Midi** - responds to notes from a connected MIDI keyboard or controller. 
- **Line-In** - *Requires a Virtual Cable / Input Device*

### Media loading

Use **IMPORT MEDIA** for photo / video files. Videos play and repeat automatically.

## AUDIO tab

### Processor

- **Input Gain** (0.1–8) - overall sensitivity.
- **Attack Rate** (1–60)
- **Release Rate** (0.5–30)
- **Norm. Adapt Time** (2–30 seconds) - Poll rate for average energy.

### Capture - Audio mode

- **Capture Gain** (0.1–8)

### Line-In - Line-In mode

- **Floor Gate** (0–1) - sensitivity to input activity. Raising decreases bands triggered by overtones & background noise.

### MIDI - Midi mode

- **MIDI Gain** (0.1–4) - overall strength of the response to played notes.
- **Harmonics** (1–32) - number of harmonics simulated.
- **Harm. Rolloff** (0.2–2) - Decay rate for **simulated tones.**
- **Band Spread** (0.1–6 semitones) - how widely each note spreads across nearby pitches.
- **Note Attack** (1–60)
- **Note Release** (0.5–30)
- **Velocity Floor** (0–1)
## WAVE tab

### Shape

- **Active Bands** (32–512) - number of sound-responsive lines.
- **Top Padding / Bottom Padding** (0–128 each)

### Response

- **Dynamic Baseline** - **Generally, good to have on.** Subtracts average normalized energy to let new notes and their transients pop!
- **Baseline Subtract** (0–1) - amount of steady activity removed.
- **Dynamic Boost** (0.5–6) - strengthens the remaining movement.
- **Response Gamma** (0.25–2)
- **Noise Floor Lift** (0–0.2)
- **Edge Falloff** (0–64 bands) - gradually reduces movement near the top and bottom of the active area.

### Ambient Motion

These add movement independent of music.

- **Ambient Wobble** (0–0.15) - amount of gentle waviness
- **Wobble Speed** (0–3) 
- **Drift Speed** (0–3)

## VISUAL tab

### Band Envelope

- **Band Attack** (1–60)
- **Band Release** (0.5–30)

These are speeds: **a larger Attack or Release value means a faster response**
Note: **The band envelope is independent of the audio processor envelope**
### Band Coupling
### Coupling groups adjacent bands to smoothen the overall spectrum visualization. *No audial influence*

- **Bump Bleed (bands)** (0–32)
- **Ripple Spread (bands)** (0–16)

### Geometry

- **X Resolution** (64–512) 
- **Packet Width** (0.05–2)

### Ripples

- **Transient Ripples** - **Toggle Band's visual ADSR envelope.** - **Generally encouraged to keep enabled**
- **Ripple Threshold** (0.01–1) - Play with the parameter!
- **Ripple Speed** (0.1–6) -  Slide it and see what happens.
- **Ripple Travel** (0–20) - Hey, just play with it.
- **Ripple Decay** (0–4)  - ...
- **Ripple Lifetime** (0.2–10 seconds) - ...

### Tone

These controls define the height, gain, and gamma of the rendered output prior to canvas pass - *independent of any audio input.*

- **Visual Gamma** (0.3–2.5) 
- **Visual Gain** (0.1–4)
- **Max Wave Height** (0.2–12)

### Line Color

- **Line Color** - opens a color editor.


## POST-FX tab

These controls style the final pre-canvas pass.

### Line Style

- **Line Thickness** (0–0.95) 
- **Peak Glow** (0–5)
- **Height Gradient** (0–1) 
- **Peak Thickness** (0–4)
- **Depth Fade** (0–1) 
- **Aggregate Glow** (0–4)

### Fill

Fill is the area beneath each line.

- **Fill Mode** - **Solid** - **Gradient** - **Scanlines** - **Dither** 
- **Fill Ink** (0–1) 
- **Fill Falloff** (0.05–1)
- **Scanline Pitch** (2–16)
### Palette Dither

12-swatch color quantized dithering.

- **Palette Dither**
- **Palette** - named collection of colors, with a 12-swatch preview. Use its gear to edit it, or choose **+ New Palette** to create a separate palette from the current colors.
- **Palette Size** (2–12) - number of swatches used, starting with the first swatch in the strip. Smaller values simplify the picture; larger values allow more color steps. Swatches beyond this count do not affect the output yet.
- **Dither Style** - **Pattern** gives a regular texture of small color blocks; **Halftone Cells** builds the picture from larger dots or symbols.
- **Pixel Size** (1–16; Pattern only) - size of color blocks. Higher values give a chunky, pixelated print.
- **Dither Spread** (0–1; Pattern only) - how much neighboring palette colors mingle.

Colors follow brightness: darker parts use darker active swatches and lighter parts use lighter ones. The active colors are sorted by brightness for this purpose. The darkest active swatch supplies the dark background; it need not be first in the strip.

### Halftone Cells

These work with Dither Style set to Halftone Cells.

- **Cell Size** (4–48) - size of spaces containing individual dots or symbols. Small cells preserve detail; large cells make the print marks easier to see.
- **Coverage Floor** (0–0.5) - minimum extra fullness of marks in already-visible areas. Raise it to keep faint marks from becoming too tiny. Background areas remain empty.
- **Coverage Gain** (0.5–3) - how strongly brightness makes marks fill their cells. Higher values produce heavier, denser printing; lower values leave more space around marks.
- **Mark Style** - **Dots** gives a newspaper-like dot texture. **Glyphs** uses small symbols and geometric marks instead.
- **Glyph Variety** (0–1; Glyphs only)
- **Glyph Region Scale** (0.02–0.6; Glyphs only)
- **Glyph Fill** (0.6–1.4; Glyphs only) - size of each symbol inside its cell.

### Tone Ramp

These spread the picture's brightness across palette colors in both dither styles.

- **Ramp Black Point** (0–0.5) - brightness below which the picture becomes the darkest palette color.
- **Ramp White Point** (0.5–1) - brightness needed to reach the lightest palette color. Lower it to bring lighter colors into more of the picture; raise it to reserve them for strong highlights.
- **Ramp Contrast** (0.5–4) - separation between dark and light. Higher values favor the dark and light ends of the palette; lower values keep more of the picture around middle tones.

## CANVAS tab

Canvas can leave echoes of earlier pictures and move them around. **Trails must be above 0 for trail-motion controls to have anything to move.** The Lens controls also work without trails.

### Trails

- **Trails** (0–1) - amount of the previous picture kept.
- **Trail Fade** (0–4) - extra fading over time. Higher values shorten trails. At 0, Trails and movement off-screen can still remove the old picture.
- **Fade Pattern** - where fading varies. Radial varies it between the center and edges; Noise gives patchy fading.
- **Fade Pattern Amount** (−4–4) - strength of that difference. At 0, fading is even. Negative values reverse which areas fade faster. If the amount exceeds Trail Fade, some areas can stop receiving this extra fading.

### Zoom

- **Zoom Flow** (0.5–2) - ongoing size change of echoes.
- **Zoom Pattern** - lets different parts zoom at different speeds, creating bulges and tunnel-like shapes.
- **Zoom Pattern Amount** (−0.5–0.5) - strength of uneven zoom.

### Spin

- **Spin** (−180–180 degrees per second) - continuous rotation of echoes around the Focal Point
- **Spin Pattern** - varies rotation across the picture, allowing twists instead of one even turn.
- **Spin Pattern Amount** (−180–180)

### Slide

- **Slide** (X/Y pad, −0.5–0.5 per direction) - ongoing sideways and vertical drift of echoes. The center stops this drift; farther from the center moves faster.
- **Slide X Pattern / Slide Y Pattern** - varies horizontal or vertical drift across the picture. Each direction can use a different pattern.
- **Slide X Pattern Amount / Slide Y Pattern Amount** (−0.5–0.5 each) - strength of uneven drift. At 0 the pattern has no effect; negative values reverse it.

### Stretch & Focus

- **Stretch** (X/Y pad, 0.5–2 each) - continuously widens/narrows echoes horizontally and lengthens/squeezes them vertically. **1 on both axes is neutral**.
- **Focal Point** (X/Y pad, 0–1 each) - center for zooming, stretching, and rotation, including the Lens. **0.5 / 0.5** is the middle. Move it toward an edge for off-center motion.

In MODS and MAPS, the vertical halves of these pads are named **Stretch Y** and **Focal Point Y**; **Slide Y** and **Lens Slide Y** work the same way for their pads.

### Pattern choices and Pattern Shape

These choices appear in Fade, Zoom, Spin, Slide, and Lens. Patterns need a nonzero Pattern Amount to be visible.

| Pattern | Where the effect varies |
| --- | --- |
| **None** | No variation; only the main setting applies. |
| **Radial** | Between the focal point and outer edges. |
| **Angular** | In alternating wedges around the focal point, like a pinwheel. |
| **Horizontal** | From left to right. |
| **Vertical** | From bottom to top. |
| **Noise** | In irregular patches that can change over time. |

- **Pinwheel Sectors** (1–8) - number of "spokes"
- **Turbulence Scale** (0.5–16) - patch size in Noise patterns. 
- **Turbulence Speed** (0–2)

These three controls are shared by trail patterns and the Lens pattern.

### Lens

The Lens changes the whole visible picture without needing echoes. **Zoom, Angle, and Slide set a size or position; Spin is an ongoing movement.**

- **Lens Zoom** (0.5–2) - enlarges or shrinks the picture around the Focal Point.
- **Lens Angle** (−180–180 degrees) - turns the picture to a chosen angle. **If Lens Spin is running, this angle is added to its ongoing rotation.**
- **Lens Spin** (−180–180 degrees per second) - continuously rotates the picture.
- **Lens Slide** (X/Y pad, −0.5–0.5 each) - offsets the picture horizontally and vertically.
- **Lens Pattern** - bends the picture inward and outward.
- **Lens Pattern Amount** (−0.5–0.5) - strength and direction of the bending.

## MEDIA tab

An imported photo or each frame of a video becomes heights and brightness across the lines.

- **Height Influence** (0–2) - Strength of the image influence on band height (independent of audio.)
- **Audio Gate** (0–1) - uses the image as a stencil for music-driven bumps and ripples.
- **Gate Floor** (0–1) - musical movement allowed through the darkest image areas when Audio Gate is used.
- **Black Level** (0–0.5)
- **Contrast** (0.25–4) 
- **Active Region Only** - Fit the image within active bands (exclude padding.)
- **Flip Vertically**

## MAPS tab

Mappings let keys or a MIDI controller change settings while you perform. **MIDI Maps still work in Audio/Line-in mode**

- **Keyboard** - captures a key or macro.
- **MIDI notes** - use a played note or pad like a keyboard trigger. Holding a note continuously fires.
- **MIDI CC** - connects a controller knob or slider directly to a setting. Its position selects a value across the setting's range. NOTE: **These changes are not added to undo history.**
- **Step / direction** - Value to add/subtract per activation.

Mappings work with the menu open or closed, but pause while typing or using a file browser. 

Mappings save separately from visual presets, so changing looks keeps your controller setup. **Session Mode**, playlist timing, and **Mod Route 1–8 On/Off** are also targets. Route switches refer to list positions: deleting an earlier route shifts which route a later switch controls.

### Additional targets in MAPS and MODS

These source controls appear in target lists even though there is no separate SOURCES tab. A “source” is a layer of the picture: the ridge layer supplies stacked lines; the optional spectrum wave supplies a single sound-responsive line.

- **Ridge Enabled / Wave Enabled** - shows/hides that layer. Existing trails can remain until they fade.
- **Ridge Gain / Wave Gain** (0–4 each) - brightness contributed by the layer. At 0 it adds no visible color; higher values strengthen it.
- **Ridge Blend / Wave Blend** - **Additive** brightens overlaps, **Over** places the layer over what is already there, and **Max** keeps brighter overlapping parts. Over can cover existing trails or layers.
- **Wave Spectrum** - **Raw** follows sound immediately; **Smoothed** softens changes using AUDIO's Attack Rate and Release Rate.
- **Wave Thickness** (0.001–0.05) - stroke weight of the single wave.
- **Wave Position** (0–1) - vertical position of its resting line.
- **Wave Height** (0–1) - height of its sound-driven movement.
- **Wave Ink** (0–1) - brightness of its stroke before Wave Gain is applied.

Wave shape controls have a visible effect only when the wave layer is enabled.

## MODS tab

MODS moves settings automatically. Each *route* connects a source of movement to a target. For example, **Overall → Visual Gain** makes loud accents raise the waves; **LFO → Lens Zoom** makes the picture grow and shrink.

**+** adds a route. Each row has an activity indicator, target picker, settings gear, and remove control. An **M** button elsewhere starts a route for that setting.

Routes move a setting relative to your chosen starting value. Several routes aimed at the same setting add their movements together. Values stop at the setting's limits, so leave room on the slider for movement in both directions.

### Route settings

- **Target** - setting to move. Modulation's own settings and individual palette swatches are not offered as targets.
- **Source** - what drives movement; see below.
- **Slot** - which LFO or accumulator to use.
- **Curve** - changes how source strength becomes movement
- **Threshold** (0–3; Threshold curve only)
- **Depth** (−1–1)
- **Attack / Release** (0.5–60 / 0.5–30) - **Unique Per Route**
- **Enable**
- **Route Phase** (0–1; LFO only)

### Sources

| Source | How it triggers |
| --- | --- |
| **Low** | |
| **Mid** | |
| **High** | |
| **Overall** | Stronger-than-usual sound across the whole mix. |
| **Centroid** | Whether sound is weighted toward low or high pitches. Brighter, higher-pitched sound raises the signal; **NOT loudness.** |
| **Onset** | A brief trigger when overall level crosses the hit threshold. Useful for a flash or kick followed by a fade. |
| **LFO** | Automatic repeating movement, including without music. Useful for swaying or pulsing. |
| **Accumulator** | Builds movement over time as sound or hits feed it, then drains away. Useful for gradual changes. |

Low, Mid, High, and Overall normally rest at zero until sound exceeds its recent usual level. AUDIO's Norm. Adapt Time changes how quickly that reference adjusts. Inverse and Threshold curves alter this resting behavior.

### Curves

- **Linear**
- **Exponential** 
- **Threshold** - Trigger when source exceeds set value.
- **Smoothstep** - eases gently near the low and high ends.
- **Inverse** - reverses the response.

### Onset detector

- **Onset Threshold** (1.05–3) - how far above usual loudness a hit must rise to trigger Onset.

### Shared LFO settings

Four LFOs Available **Changing a slot changes every route using it**, including changes from a route popup. **Phase, however is unique to each mod**

- **Rate (Hz)** (0.02–8) - repetitions per second (1 = 1 cycle/second)
- **Shape** - **Sine**, **Triangle**, **Saw**, **Square**, **Noise** - picks a random level each cycle and holds it until the next.
- **Phase** (0–1) - shifts the timing of the entire slot. Use Route Phase to shift only one route.

The moving graph previews the selected motion. Route Attack and Release can soften its sharp corners in the final result.

For an orbit, use two routes from the same Sine LFO slot to **Lens Slide** and **Lens Slide Y**. Give them equal small depths, matching Attack/Release, and Route Phase values of 0 and 0.25. One direction leads the other instead of both moving diagonally together. Screen proportions can make the orbit look oval.

### Shared accumulator settings

Think of an accumulator as a container that sound fills and time empties. There are four shared slots.

- **Source** - Low, Mid, High, Overall, or Onset: which sounds fill it.
- **Fill Rate** (0–4) - how quickly it builds while its source is active. Higher values reach full strength sooner; 0 stops filling.
- **Decay** (0–4) - how quickly it drains toward rest. Higher values settle sooner; 0 holds the accumulated level instead of draining.

Onset, LFO, and accumulator settings save with presets and can be adjusted through MAPS, but cannot themselves be moved by a modulation route.

## PRESETS tab

### Saving and sharing

- **SAVE** - saves the current look under the entered name on this computer.
- **LOAD** - replaces the current look with the selected preset, including routes. A preset without routes clears existing routes.
- **DELETE** - removes a user-saved preset. Shipped presets cannot be deleted; deleting your saved version of a shipped name reveals the original again.
- **IMPORT** - adds presets from `.json` or `.joypresets`. Existing names are kept; imported duplicates receive new names. Select an imported preset and press LOAD to see it.
- **EXPORT SELECTED** - writes the selected saved preset to a shareable file. Save your latest edits first to include them.
- **EXPORT MY PRESETS** - writes your user-saved presets into a collection for sharing or backup.
- **OPEN FOLDER** - opens the local preset folder.

### Play and Edit

- **MODE: PLAY** - lets the playlist run, including automatic advances when enabled.
- **MODE: EDIT** - pauses playlist playback so you can work on a look. Music, waves, and modulation continue. Switching during a transition applies the incoming look completely.
- **PLAYLIST: PLAYING / PAUSED** - another control for the same Play/Edit state, in the playlist area.

### Playlist

- **ADD** - add preset to playlist at 
- **REMOVE / UP / DOWN** - removes or reorders the selected playlist entry.
- **PREV / NEXT** - moves between playlist looks. Space/Backspace do the same with the menu hidden in Play mode.
- **Transition Time** (0–30 seconds) - time for settings to change between looks. Smooth values glide, including saved custom colors. Switches, modes, whole-number settings, and the route list change halfway through. At 0 the next look appears immediately. This blends settings, so it can pass through unexpected shapes rather than simply fading one picture over another.
- **Hold Time** (1–300 seconds) - time to stay on a look before the next automatic advance, after its transition finishes.
- **Auto Advance** - moves through the playlist automatically in Play mode. Manual advances restart the wait.

The playlist is kept between launches. Its timing stays separate from presets, so loading a look does not change the pace of your set. Changing Transition Time during a transition affects the next one.

## Known Issues

- **Canvas motion seems inactive:** raise Trails, or use Lens controls for motion without echoes. Patterns also need a nonzero Pattern Amount.
- **A WAV will not load:** use uncompressed PCM WAV. Re-exporting as 16-bit PCM WAV, or using OGG/MP3, avoids compressed WAV formats the player cannot read.

Found something else? Open an issue!

## License / credits

Built by Ashkon Khalkhali using Unity (URP).
LASP and Minis packages by [Keijiro Takahashi](https://github.com/keijiro) for audio and MIDI input.
