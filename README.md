# Heaps 2D Tutorial

Explaining a little bit of all the basics needed to create a 2D game with the Heaps.io game engine/framework.

## Features introduced or yet to introduce

code|documented|feature|note
-|-|-
_|_|(some Heaps basics should be learnt from wiki)
ok|_|sprites, sprite from strip
ok|_|basic collisions one-to-many (player to coins)
ok|_|map editor by reading strings/text files
ok|_|detecting walls
ok|_|bullets, many-to-many collision
ok|_|using a "game object" class|OOP
_|_|camera on player
_|_|UI / HUD (user interface, head-up display)
_|_|portal between two scenes (portal with filter)


## Overview: What's added each chapter

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
- 07
  - shrinked the bounding boxes inside player-enemy collision for smoother collision