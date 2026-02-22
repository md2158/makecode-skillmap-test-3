# Directional Animations

## Make movement feel real! @showdialog

Right now your character walks — but always faces the same direction even when moving left!

In this tutorial you will use **controller button events** to swap animations based on direction.

## Step 1: Understand button events

Go to ``||controller:Controller||`` — you will see event blocks for each button direction.

There are two types:
- **Pressed** → fires the instant you push the button
- **Released** → fires the instant you let go

The plan: **Left Pressed** → swap to left-facing animation. **Left Released** → restore default.

Try it with a test splash first:

```blocks
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    game.splash("Going left!")
})
```

Press **Play** ▶️ and tap the left arrow. You will see the splash the instant you press! Delete it when done.

## Step 2: Add the left-facing animation

Replace the test splash with a real **animate sprite** block using your left-facing frames.

Then add an **on left released** block that restores the default right-facing animation:

```blocks
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    animation.runImageAnimation(
        mySprite,
        [img`
        . . . f f f f f . . . . 
        . . f e e e e e f f . . 
        f e e 4 e e e f f f f f 
        f f e 4 4 4 4 4 f f f f 
        f f e 4 4 f f 4 e 4 f f 
        . . f 1 1 1 e d d 4 . . 
        . . f 6 6 6 f e e f . . 
        . . . f f f f f f . . . 
        `],
        500,
        true
    )
})
controller.left.onEvent(ControllerButtonEvent.Released, function () {
    animation.runImageAnimation(
        mySprite,
        [img`
        . . . . f f f f . . . . 
        f 4 e 4 4 4 4 4 4 e 4 f 
        f 4 4 f f 4 4 f f 4 4 f 
        4 4 f 6 6 6 6 6 6 f 4 4 
        . . . f f f f f f . . . 
        `],
        500,
        true
    )
})
```

~hint Where are the left-facing frames? 💡
Open the sprite editor and flip your walking frames **horizontally** — or look in My Assets for the left-walk frames!
hint~

## Step 3: Restore default on right release too

Add one more block — **on right released** — that also restores the default animation. This makes sure the character always snaps back to right-facing when not moving left:

```blocks
controller.right.onEvent(ControllerButtonEvent.Released, function () {
    animation.runImageAnimation(
        mySprite,
        [img`
        . . . . f f f f . . . . 
        f 4 e 4 4 4 4 4 4 e 4 f 
        f 4 4 f f 4 4 f f 4 4 f 
        4 4 f 6 6 6 6 6 6 f 4 4 
        . . . f f f f f f . . . 
        `],
        500,
        true
    )
})
```

Test all directions — left faces left ⬅️, right faces right ➡️, releasing snaps back correctly!

## Done! @showdialog

Your character now moves and faces the right way every time! 🎮

**Path 1 — Setting Up the Game World is COMPLETE!** 🎉

Head to **Path 2** to build the Sahur food-collecting scene! 🌙🍱
