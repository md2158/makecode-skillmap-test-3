# Build the Intro Screen

## Let's set the opening scene! @showdialog

The intro screen is the first thing players see. 🌙

In this tutorial you will build it in 3 steps:
- Set the night sky background
- Add the Ramadan Kareem greeting banner
- Add the Start Gate and wire up the overlap

## Step 1: Night sky background and greeting banner

Inside ``||loops:on start||``, set the background to **dark blue (color 13)** to look like a Ramadan night sky.

Then create the greeting banner sprite, set its Kind to **Decoration**, and move it up near the top of the screen:

```blocks
scene.setBackgroundColor(13)
let RamdhanKareem = sprites.create(img`
    f f f f f f f f f f f f f f f f
    f 1 1 1 1 1 1 1 1 1 1 1 1 1 1 f
    f 1 d d d 1 1 1 d d 1 1 d 1 1 f
    f f f f f f f f f f f f f f f f
    `, SpriteKind.Decoration)
RamdhanKareem.y += -24
```

~hint How to pick the image? 💡
Click the grey image box to open the sprite editor. Switch to the **My Assets** tab to pick your saved **Ramadan Greeting Text** image!
hint~

## Step 2: Add the Start Gate banner

Create the Start Gate sprite — this is the banner the player walks into to begin the game.

Scale it down to 14% and position it on the right-center of the screen:

```blocks
let StartText = sprites.create(img`
    f f f f f f f f f f f f f f f f
    f 5 5 5 5 5 5 5 5 5 5 5 5 5 5 f
    f 5 1 1 1 1 1 1 1 1 1 1 1 1 5 f
    f f f f f f f f f f f f f f f f
    `, SpriteKind.StartGate)
StartText.setScale(0.14, ScaleAnchor.Middle)
StartText.setPosition(128, 100)
```

~hint Screen size tip 💡
MakeCode Arcade's screen is **160 × 120 pixels**. Position (128, 100) places the gate in the right-center — perfect for the player to walk toward from the left!
hint~

## Step 3: Wire up the Start Gate overlap

Add an **on sprite overlaps** block from ``||sprites:Sprites||``. Set it to **Player** overlaps **StartGate**.

For now, add a splash message as a placeholder — you will replace this with the real Sahur scene in Tutorial 5:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.StartGate, function (sprite, otherSprite) {
    game.splash("Sahur dimulai!")
})
```

Press **Play** ▶️ to check your layout — dark background, banner at top, gate on the right!

## Done! @showdialog

The intro screen is complete! 🌙🏮

Next up — creating and animating your **player character**!
