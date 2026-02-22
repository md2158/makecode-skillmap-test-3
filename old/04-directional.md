# Add Directional Animations

## Make Movement Feel Real! @showdialog

Right now your character walks — but they always face the same direction!

In this tutorial you will use **controller button events** to swap animations when the player moves left, and restore the default when they stop.

## How button events work @showdialog

There are two types of button events:

- **Pressed** → fires the moment you press the button
- **Released** → fires the moment you let go

We use **Pressed** to start the left-facing walk, and **Released** to go back to normal.

## Step 1: Add the left-press event

Go to ``||controller:Controller||`` and find the **on left button pressed** block. Drag it to your workspace.

Inside it, add an **animate** block with your left-facing frames:

```blocks
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    animation.runImageAnimation(
        mySprite,
        [img`
        . . . f f f f f . . . . 
        . . f e e e e e f f . . 
        . f e e e e e e e f f . 
        f e e e e e e e f f f f 
        f e e 4 e e e f f f f f 
        f f e 4 4 4 4 4 f f f f 
        f f e 4 4 f f 4 e 4 f f 
        . f f d d d d 4 d 4 f . 
        . . f b b d d 4 f f f . 
        . . f 1 1 1 e d d 4 . . 
        . . f 6 6 6 f e e f . . 
        `],
        500,
        true
    )
})
```

~hint Where are the left-facing frames? 💡
The left-facing frames are a mirror of the right-facing ones. Open your sprite editor and flip the image horizontally, or draw new frames facing left!
hint~

## Step 2: Restore the animation on right release

When the player **releases** the right button, swap back to the default walking animation.

Find the **on right button released** block from ``||controller:Controller||``:

```blocks
controller.right.onEvent(ControllerButtonEvent.Released, function () {
    animation.runImageAnimation(
        mySprite,
        [img`
        . . . . f f f f . . . . 
        . . f f e e e e f f . . 
        . f f e e e e e e f f . 
        f f f f 4 e e e f f f f 
        f 4 e 4 4 4 4 4 4 e 4 f 
        f 4 4 f f 4 4 f f 4 4 f 
        4 4 f 6 6 6 6 6 6 f 4 4 
        `],
        500,
        true
    )
})
```

## Step 3: Test it!

Press the **Play** button and try walking left and right. Does your character face the right direction?

~hint Challenge! 🌟
Can you also add an **on up button pressed** event that makes the character jump or wave? Try adding a different animation frame set!
hint~

## Done! @showdialog

Your character now faces the right way when moving! 🎮

You have finished **Path 1 — Setting Up the Game World**!

Head over to **Path 2** to start building the Sahur food-collecting scene! 🌙
