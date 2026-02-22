# Animate Your Player Character

## Bring Your Character to Life! @showdialog

Time to add the **player** — a boy sprite who walks around collecting food and coins!

You will learn how to:
- Create a player sprite
- Move it with the controller
- Run a walking animation

## Step 1: Create the player sprite

Inside ``||loops:on start||``, add a block to create your player sprite and set it as **Player** kind.

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
```

## Step 2: Move with the controller

Add the **move mySprite with buttons** block from ``||controller:Controller||``. This lets the player walk with arrow keys or D-pad!

```blocks
controller.moveSprite(mySprite)
```

## Step 3: Set starting position and size

Place the player on the left side of the screen. Scale it up so it looks bigger and clearer.

```blocks
mySprite.setPosition(20, 101)
mySprite.setScale(2, ScaleAnchor.Middle)
```

## Step 4: Keep the player on screen

Add the **stay in screen** block so the player cannot walk off the edge!

```blocks
mySprite.setStayInScreen(true)
```

## Step 5: Add a walking animation

Go to ``||animation:Animation||`` in the toolbox. Drag out the **animate** block.

Click the animation frames box to add your walking frames one by one.

```blocks
animation.runImageAnimation(
    mySprite,
    [img`
    . . . . f f f f . . . . 
    . . f f e e e e f f . . 
    . f f e e e e e e f f . 
    f f f f 4 e e e f f f f 
    f f f 4 4 4 e e f f f f 
    f 4 e 4 4 4 4 4 4 e 4 f 
    f 4 4 f f 4 4 f f 4 4 f 
    4 4 f 6 6 6 6 6 6 f 4 4 
    . . . f f f f f f . . . 
    `],
    500,
    true
)
```

~hint What does 500 mean? 💡
**500** is the time in milliseconds between each animation frame. Try **200** for a faster walk, or **800** for a slow shuffle!
hint~

## Done! @showdialog

Your player is walking! 🚶

Next tutorial — making the character face left when moving left!
