## Config

Phaser.AUTO
Default. Tries WebGL first, falls back to Canvas if WebGL isn’t supported.

Phaser.WEBGL
Force WebGL only. Fast, supports advanced effects like shaders, tinting, blending.

Phaser.CANVAS
Force Canvas only. More compatible, but lacks WebGL features and may be slower.

physics:

- "arcade" Fast, simple physics (ideal for platformers & arcade games).
- "matter" Realistic, full-featured physics (supports mass, friction, rotation, etc.).
- "impact" Physics from the ImpactJS engine (requires plugin).

## Game

this.add.image(0, 0, "sky")

- The x and y position of the image. These are in world coordinates — so (0, 0) is the top-left corner of the game world

.setOrigin(0, 0)

- By default, Phaser places images based on their center (origin at 0.5, 0.5).
- setOrigin(0, 0) changes the origin to the top-left of the image.
- This means the top-left corner of the image will be placed exactly at position (0, 0).

add.staticImage(x, y, key): This method creates a static image in the physics world.

- staticImage means the image will not move or be affected by forces or collisions, but other objects can collide with it. It's typically used for platforms or ground surfaces.

this.player.setBounce(0.1);

- Bounce controls how "bouncy" an object is when it collides with something.
- A bounce value of 0 means no bounce — the player will just stop on impact.
- A bounce value of 1 means full bounce — the player will bounce back with the same velocity it hit the surface.
- 0.1 means a small bounce, so the player will slightly rebound after hitting the ground or another surface.

this.player.setCollideWorldBounds(true);

- .setCollideWorldBounds(true): This tells the physics engine that the player should collide with the boundaries of the game world (the edges of the game screen).

this.cameras.main.setBounds(0, 0, worldWidth, canvasHeight);

- this.cameras.main: Refers to the main camera in your Phaser game scene. The camera controls what part of the game world is visible on the screen.
- .setBounds(x, y, width, height): Sets the bounds or limits of the camera’s movement within the game world.
- 0, 0: The top-left corner of the camera’s allowed area (x = 0, y = 0).
- worldWidth: The width of the area the camera can move within (typically the width of your whole game world or level).
- canvasHeight: The height of the area the camera can move within (typically the height of your game screen or world).

this.physics.world.setBounds(0, 0, worldWidth, canvasHeight);

- this.physics.world: Refers to the physics simulation world in your Phaser scene. This is where all the physics-enabled objects exist and interact.
- .setBounds(x, y, width, height): Defines the edges of the physics world — essentially the area where physics calculations like collisions, gravity, and movement can occur.
- 0, 0: The top-left corner of the physics world.
- worldWidth: The total width of the physics world.
- canvasHeight: The total height of the physics world.

this.physics.add.collider(this.player, this.pyramids, handleCrash, null, this);

- this.player
  The first physics-enabled object (usually a sprite).
  In this case, your main player.

- this.pyramids
  The second object or group of objects (e.g. a group of obstacles).
  These could be static or dynamic game objects (like traps or platforms).

- handleCrash
  A callback function that gets called when the player collides with a pyramid.
  You define this function somewhere else in your code to handle what should happen — like reducing health, playing a sound, or ending the game.

- null
  This is the process callback — it's used to control whether the collision should actually trigger the handleCrash function.
  null means always process the collision.

- this
  The context in which the callback should run (usually the scene).
  Ensures this inside handleCrash refers to your scene object.

this.tweens.add({targets: this.player, angle: this.player.angle + 90, duration: 300, ease: "Linear" });

- targets: this.player
  The object to animate — in this case, your player sprite.

- angle: this.player.angle + 90
  This sets the target angle for the rotation.
  The player will rotate 90 degrees from its current angle.
  Note: This calculates the target angle at the moment the tween is created.

- duration: 300
  The animation will take 300 milliseconds to complete.

- ease: "Linear"
  The animation will have a constant speed (no acceleration or deceleration).

Quadratic, Cubic, Quartic, Quintic
These ease in/out with increasing steepness.

Linear:

ease: "Quad.easeIn"

ease: "Quad.easeOut"

ease: "Quad.easeInOut"

Also available for Cubic, Quart, and Quint.

🪜 Sine (Sinusoidal)
Smooth, wave-like easing.

ease: "Sine.easeIn"

ease: "Sine.easeOut"

ease: "Sine.easeInOut"

🕳️ Expo (Exponential)
Starts or ends very fast/slow.

ease: "Expo.easeIn"

ease: "Expo.easeOut"

ease: "Expo.easeInOut"

🏎️ Back
Goes slightly backward before moving forward — great for "recoil" effects.

ease: "Back.easeIn"

ease: "Back.easeOut"

ease: "Back.easeInOut"

📦 Bounce
Mimics a bouncing ball.

ease: "Bounce.easeOut" ← most common

ease: "Bounce.easeIn"

ease: "Bounce.easeInOut"

🪝 Elastic
Overshoots and then springs into place.

ease: "Elastic.easeOut" ← springy!

ease: "Elastic.easeIn"
