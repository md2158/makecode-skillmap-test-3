# Ramadan Game — MakeCode Arcade Skillmap

A MakeCode Arcade skillmap that teaches students how to build a Ramadan-themed arcade game step by step, through 8 guided tutorials split across 2 learning paths.

## Preview the Skillmap

Once hosted on GitHub, you can open it in MakeCode Arcade with this URL:

```
https://arcade.makecode.com/skillmap#github:YOUR_USERNAME/YOUR_REPO/skillmap
```

Replace `YOUR_USERNAME` and `YOUR_REPO` with your actual GitHub username and repository name.

## Learning Paths

### Path 1 — Setting Up the Game World
1. **Create Custom Sprite Kinds** — Define the SpriteKind types used throughout the game
2. **Build the Intro Screen** — Set up the opening scene with the Ramadan Kareem banner
3. **Animate Your Player Character** — Add a walking boy sprite with multi-frame animation
4. **Add Directional Animations** — Swap animations based on controller direction

### Path 2 — Game Phases & Collectibles
5. **Build the Sahur Scene** — Set the outdoor background and place decorative trees
6. **Spawn & Collect Sahur Foods** — Randomly spawn food items and handle collection
7. **Spawn Pahala Coins** — Use a timed loop to drip-feed collectible coins
8. **Unlock the Next Button & Game Flow** — Wire all phases into a complete game loop

## File Structure

```
skillmap.md              ← Main skillmap definition
pxt.json                 ← MakeCode project metadata
tutorials/
  01-spritekinds.md
  02-intro.md
  03-player.md
  04-directional.md
  05-sahur-scene.md
  06-food-collect.md
  07-pahala-coins.md
  08-next-button.md
```

## Setup Instructions

1. **Fork or clone** this repository to your own GitHub account
2. **Replace** all instances of `YOUR_USERNAME/YOUR_REPO` in `skillmap.md` with your actual repo path
3. **Add your image assets** — the tutorials reference assets like `Ramadan Greeting Text`, `Start Banner`, `Sahur Background`, `Boy-standing`, `NextButtonIcon`, and `myAnim1`. These come from your MakeCode Arcade project's asset store.
4. **Push to GitHub** and open the skillmap URL in MakeCode Arcade

## Target Audience

- **Level:** Intermediate
- **Platform:** MakeCode Arcade
- **Language:** TypeScript / JavaScript
- **Theme:** Ramadan (educational, cultural)

## License

MIT
