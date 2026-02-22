# Unlock the Next Button and Game Flow

## Bring It All Together! @showdialog

This is the final tutorial! 🎉

You will wire up the animated **Next button** and connect all the game phases into one complete Ramadan game loop!

## The full game flow @showdialog

Here is how the game works from start to finish:

```
🌙 Intro screen
   ↓ walk into Start Gate
🍱 Sahur phase — collect 15 foods
   ↓ score reaches 15 → Next button appears
   ↓ walk into Next button
🌅 Puasa phase begins!
```

## Step 1: Understand the Next button sprite

The Next button is a **FinishSahur** kind sprite. When it appears, it plays a looping animation to attract the player's attention.

In your overlap event where score equals 15 (or 10 for coins), you already created it:

```blocks
let NextButton = sprites.create(img`
    . . f f f f f f f f f f . .
    . f 1 1 1 1 1 1 1 1 1 1 f .
    . f 1 1 1 1 1 1 1 1 1 1 f .
    . . f f f f f f f f f f . .
    `, SpriteKind.Player)
NextButton.setScale(0.15, ScaleAnchor.Middle)
NextButton.setPosition(144, 102)
```

## Step 2: Add the FinishSahur overlap event

Now add a new **on sprite overlaps** block. Set it to **Player** overlaps **FinishSahur** (or Player for now):

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    game.splash("Selamat Berpuasa!")
})
```

This fires when the player walks into the Next button and starts the Puasa phase.

~hint What is Puasa? 💡
**Puasa** means fasting in Indonesian. This is where your next game phase goes — maybe a daytime scene where the player must avoid food! You can build it out however you like.
hint~

## Step 3: Check all your overlap events

Make sure you have all **4** overlap events in your game:

```blocks
// 1 — Start Gate → begins Sahur
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    game.splash("Sahur begins!")
})

// 2 — Collect food
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})

// 3 — Collect coins
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})

// 4 — Next button → begins Puasa
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    game.splash("Selamat Berpuasa!")
})
```

## Step 4: Add a win splash

When the player reaches the Puasa phase, show a congratulations message:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    game.splash("Selamat Berpuasa! 🌙")
    game.splash("Ramadan Kareem! ✨")
})
```

Find ``||game:splash||`` in ``||game:Game||``.

## Step 5: Ideas to extend your game! @showdialog

Now that you have the full loop working, here are some ideas to make it even better:

🌅 **Puasa phase** — a daytime scene where you must avoid food sprites for 30 seconds

⏱️ **Countdown timer** — use ``||info:start countdown||`` in the Puasa phase

🎵 **Background music** — add ``||music:play music||`` at the start of each scene

⭐ **High score** — show the final score at the end with ``||game:game over||``

🕌 **More collectibles** — add prayer mats, lanterns, and crescent moons as bonus items!

## Congratulations! @showdialog

You have completed the full **Ramadan Game Skillmap**! 🎉🌙

You learned how to:
- ✅ Create custom Sprite Kinds
- ✅ Build multi-scene animated games
- ✅ Use overlap events to drive game flow
- ✅ Spawn collectibles with loops and timing
- ✅ Chain game phases together with functions

**Ramadan Kareem! 🌙✨**
