# Spawn Pahala Coins

## Earn Your Rewards! @showdialog

**Pahala** means spiritual reward in Arabic. 🪙

In this tutorial you will spawn **10 golden coins** that appear one by one for the player to collect!

## Step 1: Add a loop for 10 coins

Go to ``||loops:Loops||`` and drag a **repeat** block. Set it to **10**.

Inside, create a coin sprite at a random position, then pause before the next one:

```blocks
for (let index = 0; index < 10; index++) {
    let GetPahala = sprites.create(img`
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

Find ``||sprites:create sprite of kind||`` in ``||sprites:Sprites||`` and ``||loops:pause||`` in ``||loops:Loops||``.

~hint Why pause between coins? 💡
Without the pause, all 10 coins appear at the same instant. With **pause(500)**, one coin appears every half second — so the player can see and chase each one!
hint~

## Step 2: Handle coin collection

Add an **on sprite overlaps** block for **Player** overlaps **Coin**:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})
```

## Step 3: Add the score sound

Play a sound when score is under 5, just like the food tutorial:

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

## Step 4: Unlock the Next button at score 10

The Pahala phase unlocks the Next button at **10 coins** (different from the food phase at 15):

```blocks
    if (info.score() == 10) {
        let NextButton = sprites.create(img`
            . . f f f f f f f f f f . .
            . f f 1 1 1 1 1 1 1 1 f f .
            . f 1 1 1 1 1 1 1 1 1 1 f .
            . f f 1 1 1 1 1 1 1 1 f f .
            . . f f f f f f f f f f . .
            `, SpriteKind.Player)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(144, 102)
    }
```

~hint Challenge! 🌟
Try changing ``||loops:randint(0, 100)||`` to ``||loops:randint(20, 130)||`` to spread the coins more evenly around a bigger area of the screen!
hint~

## Done! @showdialog

Pahala coins are raining down! 🪙✨

Last tutorial — wiring up the Next button to complete the full game loop!
