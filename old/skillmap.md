# ramadan-game

* name: Ramadan Game - MakeCode Arcade Skillmap
* description: Build a Ramadan-themed arcade game step by step! Learn to create a walking character, animated scenes, collectible items, and game flow — all inspired by the spirit of Ramadan.
* infoUrl: https://github.com/md2158/makecode-skillmap

## path-setup

* name: Path 1 — Setting Up the Game World
* description: Build the foundation: custom sprite kinds, the intro screen, and your animated player character.
* completionUrl: https://github.com/md2158/makecode-skillmap

### activity-spritekinds

* name: Create Custom Sprite Kinds
* type: tutorial
* description: Learn how to extend MakeCode Arcade with your own sprite categories. We'll define all the custom SpriteKind types used throughout the Ramadan game.
* tags: sprites, setup, intermediate
* url: github:md2158/makecode-skillmap/01-spritekinds
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-intro

* name: Build the Intro Screen
* type: tutorial
* description: Create the opening scene with a Ramadan Kareem greeting banner, a start gate, and set the background color.
* tags: sprites, scenes, decoration
* url: github:md2158/makecode-skillmap/02-intro
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-player

* name: Animate Your Player Character
* type: tutorial
* description: Bring your boy sprite to life with a walking animation, controller movement, and screen boundary limits.
* tags: animation, player, controller
* url: github:md2158/makecode-skillmap/03-player
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-directional

* name: Add Directional Animations
* type: tutorial
* description: Make your character look like they're really walking by swapping animations when moving left or right using controller button events.
* tags: animation, controller, events
* url: github:md2158/makecode-skillmap/04-directional
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

## path-gameplay

* name: Path 2 — Game Phases and Collectibles
* description: Build the Sahur food phase, Pahala coin phase, scoring, sound effects, and the Next button unlock mechanic.
* completionUrl: https://github.com/md2158/makecode-skillmap

### activity-sahur-scene

* name: Build the Sahur Scene
* type: tutorial
* description: Set the Sahur background, destroy the intro sprites, and place decorative trees to create an outdoor pre-dawn atmosphere.
* tags: scenes, sprites, environment
* url: github:md2158/makecode-skillmap/05-sahur-scene
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-food-collect

* name: Spawn and Collect Sahur Foods
* type: tutorial
* description: Randomly spawn Sahur food sprites and handle overlap events to collect them, update the score, and play a sound.
* tags: collectibles, overlap, score, sound
* url: github:md2158/makecode-skillmap/06-food-collect
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-pahala-coins

* name: Spawn Pahala Coins
* type: tutorial
* description: Spawn 10 collectible Pahala coins at random positions with a delay between each. Learn about loops and pause timing.
* tags: coins, loop, collectibles, timing
* url: github:md2158/makecode-skillmap/07-pahala-coins
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png

### activity-next-button

* name: Unlock the Next Button and Game Flow
* type: tutorial
* description: Trigger an animated Next button when the player reaches the score target and wire all game phases into a complete loop.
* tags: animation, score, game-flow, events
* url: github:md2158/makecode-skillmap/08-next-button
* imageUrl: https://raw.githubusercontent.com/microsoft/pxt-skillmap-sample/main/img/space.png
