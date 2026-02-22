# Animate the Player Character

## Bring your hero to life! @showdialog

Time to add the **player** — a boy sprite who walks around collecting food and coins! 🚶

In this tutorial you will create the sprite, enable movement, and add a walking animation.

## Step 1: Create and move the player

Inside ``||loops:on start||``, create the player sprite using your **Boy-standing** asset and set Kind to **Player**.

Then hook it up to the controller, set the starting position on the left, and lock it to the screen:

```blocks
let mySprite = sprites.create(img`
    . . . . f f f f . . . . 
    . . f f e e e e f f . . 
    . f f e e e e e e f f . 
    f f f f 4 e e e f f f f 
    f f f 4 4 4 e e f f f f 
    f f f 4 4 4 4 e e f f f 
    f 4 e 4 4 4 4 4 4 e 4 f 
    f 4 4 f f 4 4 f f 4 4 f 
    f e 4 d d d d d d 4 e f 
    . f e d d b b d d e f . 
    . f f e 4 4 4 4 e f f . 
    e 4 f b 1 1 1 1 b f 4 e 
    4 d f 1 1 1 1 1 1 f d 4 
    4 4 f 6 6 6 6 6 6 f 4 4 
    . . . f f f f f f . . . 
    . . . f f . . f f . . . 
    `, SpriteKind.Player)
controller.moveSprite(mySprite)
mySprite.setPosition(20, 101)
mySprite.setStayInScreen(true)
```

## Step 2: Scale up the player

The sprite is small by default. Scale it up to **2×** so it stands out clearly on screen:

```blocks
mySprite.setScale(2, ScaleAnchor.Middle)
```

Find **set mySprite scale** in ``||sprites:Sprites||``. Set the number to **2** and anchor to **Middle**.

~hint What does ScaleAnchor.Middle do? 💡
It scales the sprite from its **center point** outward — so it grows evenly in all directions and stays in the same screen position!
hint~

## Step 3: Add the walking animation

Go to ``||animation:Animation||`` and drag out the **animate sprite** block.

Click the **+** to add 3 walking frames from your My Assets. Set interval to **500ms** and loop to **true**:

```blocks
animation.runImageAnimation(
    mySprite,
    [img`
    . . . . f f f f . . . . 
    f 4 e 4 4 4 4 4 4 e 4 f 
    f 4 4 f f 4 4 f f 4 4 f 
    4 4 f 6 6 6 6 6 6 f 4 4 
    . . . f f f f f f . . . 
    `, img`
    . . . . f f f f . . . . 
    f 4 e 4 4 4 4 4 4 e 4 f 
    f e 4 d d d d d d 4 e f 
    4 4 f 6 6 6 6 6 6 f 4 4 
    . . . f f . . f f . . . 
    `, img`
    . . . . f f f f . . . . 
    f 4 e 4 4 4 4 4 4 e 4 f 
    f 4 4 f f 4 4 f f 4 4 f 
    4 4 f 6 6 6 6 6 6 f 4 4 
    . . . f f f f f f . . . 
    `],
    500,
    true
)
```

Press **Play** ▶️ — your character should walk with animation and stop at screen edges!

## Done! @showdialog

Your player is alive and walking! 🎉🚶

Next up — making the character **face left** when moving left!
