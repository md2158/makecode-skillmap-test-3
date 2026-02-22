# Collect Sahur Foods

## Time to eat! @showdialog

The player needs to collect **15 Sahur food items** before Sahur time ends! 🍱

In this tutorial you will spawn food sprites, handle collection with overlap events, and play a sound effect.

## Step 1: Spawn 15 food sprites with a loop

Still inside the **on Player overlaps StartGate** block (after the trees), add a **repeat 15** loop from ``||loops:Loops||``.

Inside the loop, create a food sprite at a **random position** and pause half a second between each spawn:

```blocks
    for (let index = 0; index < 15; index++) {
        let SahurFood = sprites.create(img`
            . . 2 2 b b b b b . . . . . . . 
            . 2 b 4 4 4 4 4 4 b . . . . . . 
            2 2 4 4 4 4 d d 4 4 b . . . . . 
            2 b 4 4 4 4 4 4 d 4 b . . . . . 
            2 b 4 4 4 4 4 4 4 d 4 b . . . . 
            2 b 4 4 4 4 4 4 4 4 4 b . . . . 
            2 2 b 4 4 4 4 4 4 4 b e . . . . 
            . 2 b b b 4 4 4 b b b e . . . . 
            . . e b b b b b b b e e . . . . 
            . . . e e b 4 4 b e e e . . . . 
            `, SpriteKind.Food)
        SahurFood.setPosition(randint(0, 100), randint(0, 100))
        SahurFood.setStayInScreen(true)
        pause(500)
    }
```

~hint Why pause(500)? 💡
Without the pause all 15 foods appear at once. With **500ms** delay, they drip in one by one — giving the player time to see and chase each one!
hint~

## Step 2: Handle food collection and sound

Add a new **on Player overlaps Food** block from ``||sprites:Sprites||``.

Inside it, increase the score, destroy the food, and play a beep sound for the first 5 collects:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
    if (info.score() < 5) {
        music.play(
            music.createSoundEffect(
                WaveShape.Square,
                400,
                600,
                255,
                0,
                100,
                SoundExpressionEffect.None,
                InterpolationCurve.Linear
            ),
            music.PlaybackMode.UntilDone
        )
    }
})
```

## Step 3: Unlock the Next button at score 15

Inside the same overlap block, add an **if score = 15** check. When it triggers, create the animated Next button sprite:

```blocks
    if (info.score() == 15) {
        NextButton = sprites.create(img`
            . . f f f f f f f f f f . .
            . f f 1 1 1 1 1 1 1 1 f f .
            . f 1 1 1 1 1 1 1 1 1 1 f .
            . f 1 1 f f 1 1 f f 1 1 f .
            . f f 1 1 1 1 1 1 1 1 f f .
            . . f f f f f f f f f f . .
            `, SpriteKind.FinishSahur)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(142, 101)
    }
```

~hint Score == 15 not >= 15 💡
Using **exactly 15** means the button only spawns once — the moment the 15th food is collected. Using >= 15 would try to create it on every collect after that!
hint~

## Done! @showdialog

Food collection is working! 🍱✅

Next up — **Pahala coins** and completing the full game loop!
