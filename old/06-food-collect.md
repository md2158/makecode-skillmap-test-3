# Spawn and Collect Sahur Foods

## Time to Eat! @showdialog

In this tutorial you will spawn **15 Sahur food sprites** across the scene and handle collecting them — updating the score and playing a sound effect! 🍱

## Step 1: Create a food sprite with a loop

Go to ``||loops:Loops||`` and drag out a **repeat** block. Set it to **15**.

Inside the loop, create a food sprite at a random position:

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
        . . . e e b 4 4 b e e e b . . . 
        `, SpriteKind.Food)
    SahurFood.setPosition(randint(0, 100), randint(0, 100))
    SahurFood.setStayInScreen(true)
    pause(500)
}
```

~hint What does pause(500) do? 💡
It makes the game wait **half a second** before spawning the next food item. This means food appears one by one, giving the player time to see each one!
hint~

## Step 2: Handle food collection

Go to ``||sprites:Sprites||`` and drag out an **on sprite overlaps** block. Set it to **Player** overlaps **Food**.

Inside it, increase the score and destroy the food sprite:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})
```

## Step 3: Add a sound effect

Play a beep sound when the score is still low (under 5). This gives satisfying audio feedback at the start!

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

Find **play sound** in ``||music:Music||``. Click the sound box to design your beep!

## Step 4: Unlock the Next button at score 15

When the score reaches **15**, create an animated Next button sprite:

```blocks
    if (info.score() == 15) {
        let NextButton = sprites.create(img`
            . . . . . . . . . . . . . . . .
            . . f f f f f f f f f f f f . .
            . f f 1 1 1 1 1 1 1 1 1 1 f f .
            . f 1 1 1 1 1 1 1 1 1 1 1 1 f .
            . f 1 1 1 1 1 1 1 1 1 1 1 1 f .
            . f f 1 1 1 1 1 1 1 1 1 1 f f .
            . . f f f f f f f f f f f f . .
            `, SpriteKind.Player)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(142, 101)
    }
```

~hint Score == 15 vs >= 15 💡
Using **== 15** (exactly 15) means the Next button only appears once — the moment the 15th food is collected. This avoids it spawning multiple times!
hint~

## Done! @showdialog

Sahur food collection is working! 🍱✅

Next tutorial — spawning the Pahala coins!
