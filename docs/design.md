# Turbo Lane — Design Doc

## Concept
A top-down arcade car race. The player's car races up a track against a
pack of rival cars, weaving between lanes to reach the finish line first.
One-thumb steering, short races (~60-90 seconds), bright cartoony look.

## Core Loop
1. Race starts — player and 3 rival cars line up at the bottom of the track.
2. All cars move forward (up the screen) automatically. The player steers
   left/right by dragging a finger anywhere on screen — the car eases
   toward the finger's horizontal position.
3. Stay on the road and dodge rivals/obstacles — clipping the road edge
   or a rival slows the player down.
4. A live position readout (1st/2nd/3rd/4th) shows how the player is
   doing against the pack as the race progresses.
5. First car to cross the finish line at the top wins the race. Game
   shows a result screen (win/lose + finish time) with a restart option.

## Design Pillars
- **One-thumb control** — steering is the only input; forward motion is
  automatic. Always playable on a phone with one hand.
- **Readable at a glance** — distinct car colors/silhouettes, clear lane
  markings, an obvious "who's winning" signal at all times.
- **Short & replayable** — races are quick, so losing (or winning) makes
  the player want to immediately go again.

## Systems

### Controls
- Touch drag (anywhere on screen) — sets a target X; the player's car
  eases toward it every frame, clamped to the road width.
- Keyboard arrow keys / A-D also nudge the target X, as a bonus for
  desktop testing.

### Track & Movement
- Vertical road, player car auto-scrolls forward at a base speed.
- Camera follows the player car up the track (world taller than one
  screen; finish line sits at the top).
- Road edges are solid — drifting into them scrubs speed.
- Rival cars run simple lane-weaving AI at a speed close to the
  player's, occasionally drifting between lanes.

### Race & Scoring
- Race distance is a tunable value (track length to the finish line).
- Position (1st-4th) is computed from progress along the track and
  shown live in the HUD.
- On finish: show placement + finish time. Best (fastest winning) time
  is saved so the player can beat their own record.

### Feel
- Speed lines / dust particles behind cars, engine-rev tween on start,
  screen flash + tween pop on finish, brief tint flash when clipping a
  rival or the road edge.

## Art & Audio Direction
- Bright cartoony arcade palette — saturated road, high-contrast car
  colors so the player's car is always instantly identifiable.
- Cars, road, and rivals are all drawn with simple shape-based art in a
  consistent toy-like style.
