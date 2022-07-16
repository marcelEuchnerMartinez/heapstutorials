# Heaps 2D Tutorial

Explaining a little bit of all the basics needed to create a 2D game with the Heaps.io game engine/framework.

## Features to introduce

- (some Heaps basics should be learnt from wiki)
- sprites, sprite from strip
- basic collisions one-to-many (player to coins)
- map editor by reading strings/text files
- detecting walls
- bullets, many-to-many collision
- using a "game object" class
- camera on player
- UI / HUD (user interface, head-up display)
- portal between two scenes (portal with filter)

## History: What's added each chapter

- 01
  - adding some `h2d.Bitmap` sprites at random positions
  - therefore introducing `hxd.Res.initLocal` to load game assets
  - adding a basic `h2d.Text` for in-game information
- 02
  - sprites are now `h2d.Anim` based on sprite strips
  - player can move (arrow keys / W-A-S-D)
    - therefore making first time use of `hxd.App.update` and using a reference to the player (sprite)
- 03
  - setting the game's background color to a dark green
  - player movement now changes the player's sprite as well
    - a little clean-up in the update function and separating keyboard key hitting states
    - for the moment changing this sprite is very unconvenient and verbose (`changePlayerAnimation`)
      - the reference `player` switches and must save/pass all values from the old object
      - the sprite must be re-created here
- 04
  - new fields to store game objects and game information/state:
    - `coins` (an array to save all coin sprites)
    - `score_collectedCoins` (cointing collected coins)
    - `updatableInfoHUD` (adding an updatable score information)
  - everything gets cleaned up by defining/using methods
    - keyboard key checks are bundled into one method (`checkKeyboardKeys`)
    - sprite creating is bundled (into `createSprite_animated`)
      - (simplifying `changePlayerAnimation` a little bit, but still a bit clumsy)
  - `update` now contains several to-dos:
    - `player_movement`
    - `wrapPlayerScene`
    - `update_InfoHUD`
    - `checkCollision_playerAndCoins`
