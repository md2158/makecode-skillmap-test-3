# Pahala Coins

## Earn your rewards! @showdialog

**Pahala** means spiritual reward in Arabic and Indonesian. 🪙

In this tutorial you will spawn 10 golden Pahala coins and handle their collection — including unlocking a second Next button when all 10 are collected.

## Step 1: Spawn 10 coins with a timed loop

Inside your **on Player overlaps StartGate** block (after the food loop), add a **repeat 10** loop.

Create a coin sprite at a random position and pause between each one:

```blocks
    for (let index = 0; index < 10; index++) {
        GetPahala = sprites.create(img`
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . 4 4 4 4 4 . . . . . . 
            . . . 4 4 4 5 5 5 d 4 4 4 4 . . 
            . . 4 d 5 d 5 5 5 d d d 4 4 . . 
            . . 4 5 5 1 1 1 d d 5 5 5 4 . . 
            . 4 5 5 5 1 1 1 5 1 1 5 5 4 4 . 
            . 4 d d 1 1 5 5 5 1 1 5 5 d 4 . 
            . 4 5 5 1 1 5 1 1 5 5 d d d 4 . 
            . 2 5 5 5 d 1 1 1 5 1 1 5 5 2 . 
            . 2 d 5 5 d 1 1 1 5 1 1 5 5 2 . 
            . . 2 4 d d 5 5 5 5 d d 5 4 . . 
            . . . 2 2 4 d 5 5 d d 4 4 . . . 
            . . 2 2 2 2 2 4 4 4 2 2 2 . . . 
            . . . 2 2 4 4 4 4 4 4 2 2 . . . 
            . . . . . 2 2 2 2 2 2 . . . . . 
            `, SpriteKind.Coin)
        GetPahala.setPosition(randint(0, 100), randint(0, 100))
        pause(500)
    }
```

~hint Coins vs Food spawn area 💡
Try changing **randint(0, 100)** to **randint(20, 140)** to spread the coins across a wider area — so food and coins don't stack on top of each other!
hint~

## Step 2: Handle coin collection

Add a new **on Player overlaps Coin** block from ``||sprites:Sprites||``.

Increase score, destroy the coin, and play the same beep sound for the first 5 collects:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
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

## Step 3: Unlock Next button at score 10

Inside the coin overlap block, add an **if score = 10** check that spawns the Next button:

```blocks
    if (info.score() == 10) {
        NextButton = sprites.create(img`
            . . f f f f f f f f f f . .
            . f f 1 1 1 1 1 1 1 1 f f .
            . f 1 1 1 1 1 1 1 1 1 1 f .
            . f 1 1 f f 1 1 f f 1 1 f .
            . f f 1 1 1 1 1 1 1 1 f f .
            . . f f f f f f f f f f . .
            `, SpriteKind.FinishSahur)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(144, 102)
    }
```

Press **Play** ▶️ — walk into the gate, collect food and coins, watch the Next button appear! ✅

## Done! @showdialog

Pahala coins are flowing! 🪙✨

Last tutorial — wiring up the **Next button** to complete the full game loop!
