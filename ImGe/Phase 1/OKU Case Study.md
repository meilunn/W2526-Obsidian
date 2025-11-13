- Reference games: Flower, The Pathless
- game design influenced by current market "demand"

- input mapping (controller) angepasst auf Gebrauch im Spiel 
	- sehr viel Sprinten -> sprinten auf R2 statt Left stick

## Development Process
1. Early Development
	- core mechanics in early playground scene
	- scene with ONLY terrain to see how char moves -> tweak n fine tune
		- how steep do the slopes need to be
	- new mechanics occasionally tested in isolated scenes 
		- e.g. deep water, boost rings
		- test first then put into larger scene
2. Advanced Development
	- new iteration of playground scene offers clearer frame for character controller to work in
		- during which visual dev happened
	- test all mechanics

## Technical Details Char Controller
- Char is RigidBody-based
	- direct control of linear velocity
	- not force-based
- Coyote time
- Jump input buffer time
	- jump input is saved for a short time so that player can press jump button slightly before touching ground
- support for external forces by summing them up and applying them to internal velocity

- Slope support (up and down) 
	- uses forward an right vectors of plane defined by the gorund normal
- Momentum sys
	- applied in input direction so turning doesn't suffer
- Tracking 
	- landing and reset positions
	- respawn sys
	- reset zones
- Lock sys
	- lock entire controller (only jumping)
	- char controller only unlocks if no blockers on objare left

## Pizza Playtest
- keep in mind that as a dev you are *good* at the game 
	- need to adjust expectations
	- -> any stuff that new players need to know?
- fine tune challenges based on player observation
	- can player recognise problem/goal?
	- difficulty for players
- open map leads to non-linear challenge sequence 
	- control mechanics can be unclear as player may skip challenges or do them in diff order
- Some players have a very hard time to acclimatise to third person controls as game is targeted to very casual audience
- game is slow paced and relies heavily on atmosphere and immersion
	- not good fit for most playtesting environments (e.g. Demo day, pizza playtest, conventions)
	- heavy use of audio cues make headset necessity, but still hard to hear in public playtesting spaces -> player more likely to get confused due to missing cues
		- visual elems to support audio cues or other way around 
	- favours longer sessions than usual playtests

## Camera
### Mechanics
- Dialogue sys with per-line cam support
	- frame cam for each line
- Dynamic "zoom-zones"
	- cam distance to player curated by location 
- In-Game messages, poems etc. support unique cam angles
	- saves what other players looked at as they wrote poem
- Show-cams
	- for diverting player's attention
	- e.g. highlighting obj

### Technical Details
- Cinemachine with custom cam controller script
- follows player with linear interpolation
- when jumping, cam vertically focuses landing position and doesn't follow player
	- reverts to foloing player directly if landing pos and player p
- move towards player when cam would physically bump into obstacle
- Guidance sys
	- gently turns cam towards player's movement dir if no cam input was detected for a while

## Level Prototyping
- First prototype
	- Terrain based scene containing what char controller would have to support in final game -> test n develop accordingly
	- (see early development)

- Second prototype
	- test more advances version of gameplay loop
		- establish map with according terrain, landmarks
	- adjust params for char controller
		- make char controller flexible with **exposed params** to allow efficient fine tuning at later dev stages
	- experiment with sightlines

- Third prototype
	- final prototype / vertical slice
	- still new mechanics
	- pacing and gating concepts 
		- "locking" certain regions
		- e.g. need certain amount of stamina
		- blocking things with sightlines


## Puzzle Prototyping
- Mechanic and metrics oriented
	- able to see landmark (which is puzzle) from far away
- architecturally cohesive with rest of the world

- Final version
	- final placement into open map, according teasing, sightlines, landmark function
	- work more with concept of "oku"

## Unity Terrain
- hard to work with
- base terrain -> pro builder onto terrain for testing -> adjust terrain to pro builder


## Depth n Distance
- ==completely unlit== to capture visual qualities of Ukiyo-e
- -> communication of depth only with colour
	- distance fog -> blue tint
		- + custom fog bc unity default fog cannot be customised during runtime
	- vertical gradient of mountains