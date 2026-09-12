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

- **Audio** — uses the app's audio player.
- **Midi** — responds to notes from a connected MIDI keyboard or controller. 
- **Line-In** — *Requires a Virtual Cable / Input Device*
### Audio player

- **LOAD** — opens an audio file: uncompressed PCM WAV, OGG, or MP3.
- **PLAY / PAUSE** — starts or pauses playback. The label tells you what clicking will do.
- **STOP** — stops playback and returns to the beginning.
- **Playback position** — drag along the song to jump to another moment.
- **Volume** — changes listening loudness. In Audio mode it also changes the sound being measured, so the picture can react differently. Use Input Gain or Visual Gain to adjust the visual response without changing listening volume.

### Media loading

Use **IMPORT MEDIA** for photo / video files. Videos play and repeat automatically.

## AUDIO tab

### Processor

- **Input Gain** (0.1–8) — overall sensitivity.
- **Attack Rate** (1–60)
- **Release Rate** (0.5–30)
- **Norm. Adapt Time** (2–30 seconds) — Poll rate for average energy.

### Capture — Audio mode

- **Capture Gain** (0.1–8)

### Line-In — Line-In mode

- **Floor Gate** (0–1) — sensitivity to input activity. Raising decreases bands triggered by overtones & background noise.

### MIDI — Midi mode

- **MIDI Gain** (0.1–4) — overall strength of the response to played notes.
- **Harmonics** (1–32) — number of harmonics simulated.
- **Harm. Rolloff** (0.2–2) — Decay rate for **simulated tones.**
- **Band Spread** (0.1–6 semitones) — how widely each note spreads across nearby pitches.
- **Note Attack** (1–60)
- **Note Release** (0.5–30)
- **Velocity Floor** (0–1)
## WAVE tab

### Shape

- **Active Bands** (32–512) — number of sound-responsive lines.
- **Top Padding / Bottom Padding** (0–128 each)

### Response

- **Dynamic Baseline** — **Generally, good to have on.** Subtracts average normalized energy to let new notes and their transients pop!
- **Baseline Subtract** (0–1) — amount of steady activity removed.
- **Dynamic Boost** (0.5–6) — strengthens the remaining movement.
- **Response Gamma** (0.25–2)
- **Noise Floor Lift** (0–0.2)
- **Edge Falloff** (0–64 bands) — gradually reduces movement near the top and bottom of the active area.

### Ambient Motion

These add movement independent of music.

- **Ambient Wobble** (0–0.15) — amount of gentle waviness
- **Wobble Speed** (0–3) 
- **Drift Speed** (0–3)

## VISUAL tab

### Band Envelope

- **Band Attack** (1–60)
- **Band Release** (0.5–30)

These are speeds: **a larger Attack or Release value means a faster response**
Note: **The band envelope is independent of the audio processor envelope**
### Band Coupling

- **Bump Bleed (bands)** (0–32) — lets each main bump lift neighboring lines above and below it. At 0, lines respond independently. Higher values join isolated peaks into broad hills across the stack.
- **Ripple Spread (bands)** (0–16) — number of neighboring lines sharing each traveling ripple. At 0, it stays on its original line; higher values create a wider wave across the stack. Requires **Transient Ripples** to see the effect.

### Geometry

- **X Resolution** (64–512) — detail along each line. Lower values can look angular; higher values follow curves and image details more smoothly.
- **Packet Width** (0.05–2) — width of bumps and traveling ripples from left to right. Narrow settings make spikes; wide settings create rolling swells. Bump Bleed and Ripple Spread widen them across several lines instead.

### Ripples

- **Transient Ripples** — creates outward-traveling waves when a line receives a sudden burst of sound.
- **Ripple Threshold** (0.01–1) — strength needed to create a ripple. Lower values produce more ripples; higher values reserve them for strong accents.
- **Ripple Speed** (0.1–6) — how quickly ripples travel left and right from their starting points.
- **Ripple Travel** (0–20) — maximum distance before a ripple disappears. Higher values let it cross more of the picture. **0 removes the distance limit**; it does not stop ripples.
- **Ripple Decay** (0–4) — how quickly ripples shrink over time. Higher values fade them sooner; 0 keeps their strength until another limit removes them.
- **Ripple Lifetime** (0.2–10 seconds) — longest time a ripple remains. It may disappear sooner because of its travel limit or fading.

### Tone

These controls reshape wave height rather than choosing colors.

- **Visual Gamma** (0.3–2.5) — balance between small details and large peaks in the finished shape, including wobble and image effects. Below 1 usually brings up small details; above 1 emphasizes stronger peaks. Strong image Height Influence reduces this control's effect.
- **Visual Gain** (0.1–4) — overall height of the finished waves. Raise it for a dramatic landscape or lower it for a flatter drawing.
- **Max Wave Height** (0.2–12) — limits peak height, gently rounding off growth near the limit. Low values keep a tidy stack; high values allow towering peaks and more overlap.

### Framing

- **Fit Width / Fit Height** (0.3–1.5 each) — how much of the view the plot occupies horizontally and vertically. Lower values leave more margin; higher values fill more of the screen and can push parts out of view.
- **Depth Offset** (0–0.1) — places successive rows farther behind one another. The visible effect depends on the view and may be subtle from straight ahead. Use Fit Height to change the stack's height on screen.
- **Horizontal Slope** (−0.05–0.05) — shifts each successive row farther left or right, giving the stack a slant. At 0 there is no added sideways lean.

### Line Color

- **Line Color** — opens a color editor. Changes preview immediately; **APPLY** keeps them, while **CANCEL** or closing the editor restores the previous color. **Line Red / Line Green / Line Blue** (0–1 each) remain separate MODS and MAPS targets.

With Palette Dither off, this is the lines' color. With it on, final colors come from the palette: changing Line Color mainly changes how bright the lines are considered and therefore which palette colors they receive.

## POST-FX tab

These style the drawn picture: line weight, shading beneath lines, colors, and print textures.

### Line Style

- **Line Thickness** (0–0.95) — stroke weight. Higher values give heavier lines. At 0 a fine line remains rather than disappearing entirely.
- **Peak Glow** (0–5) — brightens raised parts more than flat parts. It adds brightness, not a separate soft halo. With Palette Dither on, peaks may shift toward brighter palette colors.
- **Height Gradient** (0–1) — darkens low, flat parts while leaving tall peaks brighter. Higher values make crests stand out more strongly.
- **Peak Thickness** (0–4) — widens the line where a wave is tall. Use with some Line Thickness to give peaks heavier strokes while quieter parts stay thin.
- **Depth Fade** (0–1) — darkens rows toward the back/top of the stack. Higher values separate foreground and distance more strongly.
- **Aggregate Glow** (0–4) — brightens the whole plot as the overall sound level rises. Higher values give stronger whole-picture pulses.

### Fill

Fill is the area beneath each line.

- **Fill Mode** — **Solid** gives a plain dark area; **Gradient** fades shading downward; **Scanlines** uses horizontal stripes; **Dither** uses a fine repeating speckled pattern. Solid does not use Fill Ink or Fill Falloff, but Fill Depth Lift can still brighten it.
- **Fill Ink** (0–1) — strength of shading in Gradient, Scanlines, or Dither mode. At 0 that shading disappears; higher values make it denser and more visible.
- **Fill Falloff** (0.05–1) — how far shading reaches below a line. **Higher values spread it farther downward**; lower values keep it near the stroke.
- **Fill Depth Lift** (0–0.5) — adds brightness beneath rows toward the back/top. Raise it to make those layers more visible; it also works in Solid mode.
- **Scanline Pitch** (2–16) — stripe spacing in Scanlines mode. Higher values make broader stripes and gaps. It does not resize the Fill Mode's Dither pattern.

### Palette Dither

“Dither” creates shading with patterns of small marks or neighboring colors, like a printed picture. The pattern stays aligned with the screen while the picture beneath it moves.

- **Palette Dither** — turns this final color-and-texture treatment on/off. When off, the remaining controls in this group are inactive.
- **Palette** — named collection of colors, with a 12-swatch preview. Use its gear to edit it, or choose **+ New Palette** to create a separate palette from the current colors.
- **Palette Size** (2–12) — number of swatches used, starting with the first swatch in the strip. Smaller values simplify the picture; larger values allow more color steps. Swatches beyond this count do not affect the output yet.
- **Dither Style** — **Pattern** gives a regular texture of small color blocks; **Halftone Cells** builds the picture from larger dots or symbols.
- **Pixel Size** (1–16; Pattern only) — size of color blocks. Higher values give a chunky, pixelated print; lower values preserve fine details.
- **Dither Spread** (0–1; Pattern only) — how much neighboring palette colors mingle. At 0 they meet in hard steps; higher values soften those steps with more visible texture.

Colors follow brightness: darker parts use darker active swatches and lighter parts use lighter ones. The active colors are sorted by brightness for this purpose. The darkest active swatch supplies the dark background; it need not be first in the strip.

#### Editing a palette

Click a swatch, then choose its color. The picture previews edits immediately. Repeat for other swatches, enter a name, and press **SAVE** to keep the palette in the library on this computer. **CANCEL** or closing the editor discards the preview changes. Editing an existing palette updates that library entry; **+ New Palette** makes a separate entry.

The picker offers hue (color family), saturation (muted to vivid), and brightness (dark to light). Its color-code field lets you enter an exact color if you have one. Presets also save individual palette colors as part of the look.

### Halftone Cells

These work with Dither Style set to Halftone Cells.

- **Cell Size** (4–48) — size of spaces containing individual dots or symbols. Small cells preserve detail; large cells make the print marks easier to see.
- **Coverage Floor** (0–0.5) — minimum extra fullness of marks in already-visible areas. Raise it to keep faint marks from becoming too tiny. Background areas remain empty.
- **Coverage Gain** (0.5–3) — how strongly brightness makes marks fill their cells. Higher values produce heavier, denser printing; lower values leave more space around marks.
- **Mark Style** — **Dots** gives a newspaper-like dot texture. **Glyphs** uses small symbols and geometric marks instead.
- **Glyph Variety** (0–1; Glyphs only) — variety of symbol families. At 0 the marks share one family; higher values mix more families. Marks within a family can still change with brightness.
- **Glyph Region Scale** (0.02–0.6; Glyphs only) — how frequently symbol families change across the image. Lower values create larger areas of similar marks; higher values make smaller patches. Most noticeable with Glyph Variety raised.
- **Glyph Fill** (0.6–1.4; Glyphs only) — size of each symbol inside its cell. Lower values leave breathing room; higher values make symbols broader and more crowded without changing cell spacing.

### Tone Ramp

These spread the picture's brightness across palette colors in both dither styles.

- **Ramp Black Point** (0–0.5) — brightness below which the picture becomes the darkest palette color. Raise it to remove faint trails and low-level detail, leaving cleaner dark areas.
- **Ramp White Point** (0.5–1) — brightness needed to reach the lightest palette color. Lower it to bring lighter colors into more of the picture; raise it to reserve them for strong highlights.
- **Ramp Contrast** (0.5–4) — separation between dark and light. Higher values favor the dark and light ends of the palette; lower values keep more of the picture around middle tones.

The old **Palette Mapping**, **Background Swatch**, **Ink Shading**, and **Shade Amount** controls are no longer in the menu. Color assignment follows brightness automatically; use Palette, Palette Size, and Tone Ramp to shape the result.

## CANVAS tab

Canvas can leave echoes of earlier pictures and move them around. **Trails must be above 0 for trail-motion controls to have anything to move.** The Lens controls also work without trails.

### Trails

- **Trails** (0–1) — amount of the previous picture kept. At 0 there are no echoes. Values close to 1 leave increasingly long trails; lower values clear the picture sooner.
- **Trail Fade** (0–4) — extra fading over time. Higher values shorten trails. At 0, Trails and movement off-screen can still remove the old picture.
- **Fade Pattern** — where fading varies. Radial varies it between the center and edges; Noise gives patchy fading.
- **Fade Pattern Amount** (−4–4) — strength of that difference. At 0, fading is even. Negative values reverse which areas fade faster. If the amount exceeds Trail Fade, some areas can stop receiving this extra fading.

### Zoom

- **Zoom Flow** (0.5–2) — ongoing size change of echoes. **1 is still**; above 1 sends trails outward, below 1 draws them inward.
- **Zoom Pattern** — lets different parts zoom at different speeds, creating bulges and tunnel-like shapes.
- **Zoom Pattern Amount** (−0.5–0.5) — strength of uneven zoom. At 0, all parts follow Zoom Flow equally; negative values reverse the variation.

### Spin

- **Spin** (−180–180 degrees per second) — continuous rotation of echoes around the Focal Point. Farther from 0 spins faster; changing the sign reverses direction.
- **Spin Pattern** — varies rotation across the picture, allowing twists instead of one even turn.
- **Spin Pattern Amount** (−180–180) — strength of the difference in rotation speed. At 0 rotation is even; negative values reverse the variation.

### Slide

- **Slide** (X/Y pad, −0.5–0.5 per direction) — ongoing sideways and vertical drift of echoes. The center stops this drift; farther from the center moves faster.
- **Slide X Pattern / Slide Y Pattern** — varies horizontal or vertical drift across the picture. Each direction can use a different pattern.
- **Slide X Pattern Amount / Slide Y Pattern Amount** (−0.5–0.5 each) — strength of uneven drift. At 0 the pattern has no effect; negative values reverse it.

### Stretch & Focus

- **Stretch** (X/Y pad, 0.5–2 each) — continuously widens/narrows echoes horizontally and lengthens/squeezes them vertically. **1 on both axes is neutral**. Above 1 expands that direction; below 1 contracts it.
- **Focal Point** (X/Y pad, 0–1 each) — center for zooming, stretching, and rotation, including the Lens. **0.5 / 0.5** is the middle. Move it toward an edge for off-center motion.

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

- **Pinwheel Sectors** (1–8) — number of repeating variations around Angular patterns. Higher values create a more finely divided pinwheel. Previously called Pinwheel Spokes in this guide.
- **Turbulence Scale** (0.5–16) — patch size in Noise patterns. Higher values make smaller, closely packed patches; lower values give broad, flowing areas.
- **Turbulence Speed** (0–2) — how quickly Noise patterns change. At 0 the pattern is fixed, though the main motion can continue through it.

These three controls are shared by trail patterns and the Lens pattern.

### Lens

The Lens changes the whole visible picture without needing echoes. **Zoom, Angle, and Slide set a size or position; Spin is an ongoing movement.**

- **Lens Zoom** (0.5–2) — enlarges or shrinks the picture around the Focal Point. At 1 its size is unchanged; above 1 zooms in, below 1 zooms out.
- **Lens Angle** (−180–180 degrees) — turns the picture to a chosen angle. At 0 there is no added turn. If Lens Spin is running, this angle is added to its ongoing rotation.
- **Lens Spin** (−180–180 degrees per second) — continuously rotates the picture. Larger positive or negative values turn faster in opposite directions. At 0 it stops further rotation at the current orientation.
- **Lens Slide** (X/Y pad, −0.5–0.5 each) — offsets the picture horizontally and vertically. A fixed value holds that position rather than continuing to drift.
- **Lens Pattern** — bends the picture inward and outward. Radial gives a bulging or pinched view; Angular gives pinwheel-like distortion; Noise gives uneven warping.
- **Lens Pattern Amount** (−0.5–0.5) — strength and direction of the bending. At 0 the pattern does nothing; changing the sign reverses distortion.

## MEDIA tab

An imported photo or each frame of a video becomes heights and brightness across the lines. Bright parts have more influence than dark parts; the media's original colors are not reproduced. Import or remove it on INPUT. Videos use the same Height Influence, Audio Gate, Contrast, active-region mapping, and flip controls as photos. Media playlists and separate video transport controls are not included yet.

- **Height Influence** (0–2) — how strongly bright image areas raise lines, even without music. Higher values make the image more prominent and also shade lines according to the image, darkening its dark areas. At 0 this added height and shading are off; Audio Gate can still shape musical movement.
- **Audio Gate** (0–1) — uses the image as a stencil for music-driven bumps and ripples. At 0 sound moves freely across the picture. At 1 movement is strongest in bright image areas and reduced in dark areas. It does **not** simply hide the image whenever music is quiet.
- **Gate Floor** (0–1) — musical movement allowed through the darkest image areas when Audio Gate is used. At 0 those areas can be still; higher values let more through. At 1 the image no longer reduces that movement.
- **Black Level** (0–0.5) — treats dim image details as black. Raise it to remove a murky background or isolate a bright silhouette.
- **Contrast** (0.25–4) — above 1 suppresses dim and middle-brightness details, leaving brighter shapes; below 1 brings out faint details. At 1 this extra adjustment is neutral.
- **Active Region Only** — fits the image into sound-responsive rows, leaving padding outside it. Turn it off to spread the image across all rows, including padding.
- **Flip Vertically** — turns the image upside down to correct its orientation or change the composition.

For an image that stays visible, raise Height Influence. For a shape revealed mainly by moving sound, try Height Influence at 0, Audio Gate near 1, and a low Gate Floor. Ambient Wobble can still move lines outside that shape.

## MAPS tab

Mappings let keys or a MIDI controller change settings while you perform. Choose a trigger and a target, then set the step/direction where applicable.

- **Keyboard** — captures a key or combination. Number settings move one step per press and repeat while held; switches toggle, and dropdown choices move forward/backward.
- **MIDI notes** — use a played note or pad like a keyboard trigger. Holding a note can repeat changes to number settings.
- **MIDI CC** — connects a controller knob or slider directly to a setting. Its position selects a value across the setting's range. These changes are not added to undo history.
- **Step / direction** — for keys and MIDI notes, a larger step changes the target more per press; direction selects increase/decrease or next/previous.

Mappings work with the menu open or closed, but pause while typing or using a file browser. Dimmed targets keep their usual prerequisites. Mapping a MIDI note is separate from choosing Midi as the visual input.

Mappings save separately from visual presets, so changing looks keeps your controller setup. **Session Mode**, playlist timing, and **Mod Route 1–8 On/Off** are also targets. Route switches refer to list positions: deleting an earlier route shifts which route a later switch controls.

### Additional targets in MAPS and MODS

These source controls appear in target lists even though there is no separate SOURCES tab. A “source” is a layer of the picture: the ridge layer supplies stacked lines; the optional spectrum wave supplies a single sound-responsive line.

- **Ridge Enabled / Wave Enabled** — shows/hides that layer. Existing trails can remain until they fade.
- **Ridge Gain / Wave Gain** (0–4 each) — brightness contributed by the layer. At 0 it adds no visible color; higher values strengthen it.
- **Ridge Blend / Wave Blend** — **Additive** brightens overlaps, **Over** places the layer over what is already there, and **Max** keeps brighter overlapping parts. Over can cover existing trails or layers.
- **Wave Spectrum** — **Raw** follows sound immediately; **Smoothed** softens changes using AUDIO's Attack Rate and Release Rate.
- **Wave Thickness** (0.001–0.05) — stroke weight of the single wave.
- **Wave Position** (0–1) — vertical position of its resting line.
- **Wave Height** (0–1) — height of its sound-driven movement.
- **Wave Ink** (0–1) — brightness of its stroke before Wave Gain is applied.

Wave shape controls have a visible effect only when the wave layer is enabled.

## MODS tab

MODS moves settings automatically. Each *route* connects a source of movement to a target. For example, **Overall → Visual Gain** makes loud accents raise the waves; **LFO → Lens Zoom** makes the picture grow and shrink.

**+** adds a route. Each row has an activity indicator, target picker, settings gear, and remove control. An **M** button elsewhere starts a route for that setting.

Routes move a setting relative to your chosen starting value. Several routes aimed at the same setting add their movements together. Values stop at the setting's limits, so leave room on the slider for movement in both directions.

### Route settings

- **Target** — setting to move. Modulation's own settings and individual palette swatches are not offered as targets.
- **Source** — what drives movement; see below.
- **Slot** — which of four shared LFOs or four shared accumulators to use. Shown for those sources only.
- **Curve** — changes how source strength becomes movement; see below.
- **Threshold** (0–3; Threshold curve only) — level that must be exceeded to activate. For Low/Mid/High/Overall, 1 means usual loudness and 1.3 means about 30% stronger than usual. LFO ranges from −1 to 1; the remaining sources range from 0 to 1, so thresholds of 1 or more will not activate LFO, Centroid, Onset, or Accumulator.
- **Depth** (−1–1) — amount and direction. Positive values generally raise the target; negative values lower it. At 0.25 a route can move it by a quarter of its full range. LFO motion can go both above and below the starting value.
- **Attack / Release** (0.5–60 / 0.5–30) — how quickly this route moves away from rest and settles back. Higher values react faster; lower values smooth movement. These affect this route only.
- **Enable** — pauses this route's contribution without deleting it. Other routes can still move the same target.
- **Route Phase** (0–1; LFO only) — shifts this route's timing within the shared repeating motion. 0 matches the slot; 0.25 shifts by a quarter-cycle; 0.5 by half a cycle; 1 matches 0 again. Other routes using the slot keep their timing.

### Sources

| Source | How it moves the target |
| --- | --- |
| **Low** | Stronger-than-usual low sounds, such as bass and kick drums. |
| **Mid** | Stronger-than-usual middle tones, often voices and instruments. |
| **High** | Stronger-than-usual high sounds, such as cymbals and bright percussion. |
| **Overall** | Stronger-than-usual sound across the whole mix. |
| **Centroid** | Whether sound is weighted toward low or high pitches. Brighter, higher-pitched sound raises the signal; it is not simply loudness. |
| **Onset** | A brief trigger when overall level crosses the hit threshold. Useful for a flash or kick followed by a fade. |
| **LFO** | Automatic repeating movement, including without music. Useful for swaying or pulsing. |
| **Accumulator** | Builds movement over time as sound or hits feed it, then drains away. Useful for gradual changes. |

Low, Mid, High, and Overall normally rest at zero until sound exceeds its recent usual level. AUDIO's Norm. Adapt Time changes how quickly that reference adjusts. Inverse and Threshold curves alter this resting behavior.

### Curves

- **Linear** — follows the source directly.
- **Exponential** — reduces smaller movements while keeping strong accents prominent.
- **Threshold** — switches between no movement and full movement when the chosen level is crossed. Attack and Release can soften the switch.
- **Smoothstep** — eases gently near the low and high ends, with stronger change through the middle.
- **Inverse** — reverses the response. For sound sources, quiet moments can produce the strongest movement; for an LFO, up/down motion is flipped.

### Onset detector

- **Onset Threshold** (1.05–3) — how far above usual loudness a hit must rise to trigger Onset. Lower values catch more accents; higher values reserve it for stronger hits. Separate from VISUAL's **Ripple Threshold**, which controls traveling ripples on individual lines.

### Shared LFO settings

An LFO is a repeating motion generator. There are four slots. **Changing a slot changes every route using it**, including changes from a route popup.

- **Rate (Hz)** (0.02–8) — repetitions per second. 1 repeats once a second; 0.25 once every four seconds. Higher values move faster.
- **Shape** — **Sine** sways smoothly; **Triangle** rises/falls at an even pace; **Saw** rises then jumps back; **Square** jumps between two levels; **Noise** picks a random level each cycle and holds it until the next.
- **Phase** (0–1) — shifts the timing of the entire slot. Use Route Phase to shift only one route.

The moving graph previews the selected motion. Route Attack and Release can soften its sharp corners in the final result.

For an orbit, use two routes from the same Sine LFO slot to **Lens Slide** and **Lens Slide Y**. Give them equal small depths, matching Attack/Release, and Route Phase values of 0 and 0.25. One direction leads the other instead of both moving diagonally together. Screen proportions can make the orbit look oval.

### Shared accumulator settings

Think of an accumulator as a container that sound fills and time empties. There are four shared slots.

- **Source** — Low, Mid, High, Overall, or Onset: which sounds fill it.
- **Fill Rate** (0–4) — how quickly it builds while its source is active. Higher values reach full strength sooner; 0 stops filling.
- **Decay** (0–4) — how quickly it drains toward rest. Higher values settle sooner; 0 holds the accumulated level instead of draining.

Onset, LFO, and accumulator settings save with presets and can be adjusted through MAPS, but cannot themselves be moved by a modulation route.

## PRESETS tab

A preset saves a look: settings, individual palette colors, and the full modulation route list. It does not package audio or image files, keyboard/MIDI mappings, session mode, or playlist timing.

### Saving and sharing

- **SAVE** — saves the current look under the entered name on this computer.
- **LOAD** — replaces the current look with the selected preset, including routes. A preset without routes clears existing routes.
- **DELETE** — removes a user-saved preset. Shipped presets cannot be deleted; deleting your saved version of a shipped name reveals the original again.
- **IMPORT** — adds presets from `.json` or `.joypresets`. Existing names are kept; imported duplicates receive new names. Select an imported preset and press LOAD to see it.
- **EXPORT SELECTED** — writes the selected saved preset to a shareable file. Save your latest edits first to include them.
- **EXPORT MY PRESETS** — writes your user-saved presets into a collection for sharing or backup.
- **OPEN FOLDER** — opens the local preset folder.

### Play and Edit

- **MODE: PLAY** — lets the playlist run, including automatic advances when enabled.
- **MODE: EDIT** — pauses playlist playback so you can work on a look. Music, waves, and modulation continue. Switching during a transition applies the incoming look completely.
- **PLAYLIST: PLAYING / PAUSED** — another control for the same Play/Edit state, in the playlist area.

### Playlist

- **ADD** — appends the preset selected in the library dropdown.
- **REMOVE / UP / DOWN** — removes or reorders the selected playlist entry.
- **PREV / NEXT** — moves between playlist looks. Space/Backspace do the same with the menu hidden in Play mode.
- **Transition Time** (0–30 seconds) — time for settings to change between looks. Smooth values glide, including saved custom colors. Switches, modes, whole-number settings, and the route list change halfway through. At 0 the next look appears immediately. This blends settings, so it can pass through unexpected shapes rather than simply fading one picture over another.
- **Hold Time** (1–300 seconds) — time to stay on a look before the next automatic advance, after its transition finishes.
- **Auto Advance** — moves through the playlist automatically in Play mode. Manual advances restart the wait.

The playlist is kept between launches. Its timing stays separate from presets, so loading a look does not change the pace of your set. Changing Transition Time during a transition affects the next one.

## When a change is hard to see

- **Canvas motion seems inactive:** raise Trails, or use Lens controls for motion without echoes. Patterns also need a nonzero Pattern Amount.
- **Colors do not match Line Color:** Palette Dither assigns final colors from the palette. Edit that palette, or turn Palette Dither off.
- **A swatch does nothing:** make sure it falls within Palette Size. The picture also needs enough brightness variation to reach that color.
- **Fill controls do nothing:** choose Gradient, Scanlines, or Dither and raise Fill Ink. Solid does not use those shading controls.
- **The image is hard to recognize:** raise Height Influence, adjust Black Level and Contrast, and reduce competing waves or trails. Increase Active Bands and X Resolution for finer detail.
- **A setting keeps moving after adjustment:** check MODS for a route targeting it and whether the playlist is running.
- **An audio route rarely moves:** try a stronger passage, lower its Threshold if used, or try Onset for distinct accents. Low/Mid/High/Overall respond to sound above its recent usual level.
- **A WAV will not load:** use uncompressed PCM WAV. Re-exporting as 16-bit PCM WAV, or using OGG/MP3, avoids compressed WAV formats the player cannot read.

Found something else? Open an issue!

## License / credits

Built by Ashkon Khalkhali using Unity (URP).
LASP and Minis packages by [Keijiro Takahashi](https://github.com/keijiro) for audio and MIDI input.
