# ramadan-game

* name: Ramadan Game - MakeCode Arcade Skillmap
* description: Build a Ramadan-themed arcade game step by step! Learn to create a walking character, animated scenes, collectible items, and a full game flow — all inspired by the spirit of Ramadan.
* infoUrl: https://github.com/md2158/makecode-skillmap

## path-setup

* name: Path 1 — Setting Up the Game World
* description: Build the game foundation — custom sprite kinds, the intro screen, your animated player character, and directional movement.
* completionUrl: https://github.com/md2158/makecode-skillmap

### activity-spritekinds

* name: Custom Sprite Kinds
* type: tutorial
* description: Add 5 custom Sprite Kinds so the game can tell different objects apart — coins, food, trees, gates, and decorations.
* tags: sprites, setup, intermediate
* url: github:md2158/makecode-skillmap/01-spritekinds
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-intro

* name: Build the Intro Screen
* type: tutorial
* description: Set the night sky background, add the Ramadan Kareem greeting banner, place the Start Gate, and wire up the overlap event.
* tags: sprites, scenes, decoration
* url: github:md2158/makecode-skillmap/02-intro
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-player

* name: Animate the Player Character
* type: tutorial
* description: Create the boy sprite, enable controller movement, scale it up, and add a 3-frame walking animation.
* tags: animation, player, controller
* url: github:md2158/makecode-skillmap/03-player
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-directional

* name: Directional Animations
* type: tutorial
* description: Use controller button events to swap animations when moving left and restore the default when stopping.
* tags: animation, controller, events
* url: github:md2158/makecode-skillmap/04-directional
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

## path-gameplay

* name: Path 2 — Game Phases and Collectibles
* description: Build the Sahur food phase, Pahala coin phase, score system, sound effects, and the full game loop.
* completionUrl: https://github.com/md2158/makecode-skillmap

### activity-sahur

* name: Build the Sahur Scene
* type: tutorial
* description: Swap in the outdoor background, destroy the intro sprites, reset the score, and place 4 decorative trees.
* tags: scenes, sprites, environment
* url: github:md2158/makecode-skillmap/05-sahur
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-food

* name: Collect Sahur Foods
* type: tutorial
* description: Spawn 15 food sprites with a timed loop, handle collection with overlap events, play sound effects, and unlock the Next button at score 15.
* tags: collectibles, overlap, score, sound
* url: github:md2158/makecode-skillmap/06-food
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-coins

* name: Pahala Coins
* type: tutorial
* description: Spawn 10 golden Pahala coins with a timed loop, handle coin collection, and unlock a second Next button at score 10.
* tags: coins, loop, collectibles, timing
* url: github:md2158/makecode-skillmap/07-coins
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-finish

* name: Next Button and Game Flow
* type: tutorial
* description: Wire up the FinishSahur overlap event, connect all 4 overlap events, test the complete game loop, and add the win screen.
* tags: game-flow, events, finish
* url: github:md2158/makecode-skillmap/08-finish
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png
