# Build the Intro Screen

## Let's Set the Scene! @showdialog

In this tutorial you will build the **intro screen** — the first thing the player sees when the game starts.

You will add:
- 🌙 A dark background
- 🏮 A "Ramadan Kareem" greeting banner
- 🚪 A start gate banner to walk into

## Step 1: Set the background color

Set the background to **dark blue (color 13)** to look like a night sky.

Drag this block into the ``||loops:on start||`` block:

```blocks
scene.setBackgroundColor(13)
```

## Step 2: Add the Ramadan Kareem banner

Create a sprite for the greeting. Set its kind to **Decoration** and move it up on the screen.

```blocks
let RamdhanKareem = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    `, SpriteKind.Decoration)
RamdhanKareem.y += -24
```

~hint How do I find the image? 💡
Click the grey image box in the block to open the sprite editor. Draw your banner or paste your asset there!
hint~

## Step 3: Add the Start Gate banner

This is the sprite the player will walk into to start the game. Scale it down and place it in the center of the screen.

```blocks
let StartText = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    `, SpriteKind.Player)
StartText.setScale(0.14, ScaleAnchor.Middle)
StartText.setPosition(128, 100)
```

~hint Why Player kind for the gate? 💡
We will change this to the custom **StartGate** kind in the full project. For now, use Player so the block is easy to find!
hint~

## Step 4: Add an overlap event

When the player sprite touches the Start Gate, the Sahur scene begins!

Go to ``||sprites:Sprites||`` and drag out an **on sprite overlaps** block. Set both kinds.

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    game.splash("Sahur time!")
})
```

## Finished! @showdialog

Your intro screen is ready! 🌙

The greeting and start gate are in place. Next up — adding your animated player character!
