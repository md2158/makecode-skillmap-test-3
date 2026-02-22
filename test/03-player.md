# Animate Your Player Character

## Bring Your Character to Life! @showdialog

Now that the intro screen is set up, it's time to add the **player character** — a boy sprite with a walking animation. You'll learn how to create a player sprite, enable movement with the controller, and run a multi-frame animation.

## Step 1: Create the player sprite

Inside your `intro()` function, after the start gate, create the player sprite and assign it to `mySprite`:

```typescript
    mySprite = sprites.create(assets.image`Boy-standing`, SpriteKind.Player)
```

This creates the sprite using the standing image from your assets.

## Step 2: Enable controller movement

Allow the player to move with the arrow keys or D-pad:

```typescript
    controller.player1.moveSprite(mySprite)
```

## Step 3: Set starting position and scale

Position the player on the left side of the screen and scale it up so it's clearly visible:

```typescript
    mySprite.setPosition(20, 101)
    mySprite.setScale(2, ScaleAnchor.Middle)
```

## Step 4: Add the walking animation

Now for the fun part! Use `animation.runImageAnimation()` to cycle through 3 frames of the walking animation. The frames are pixel art images drawn directly in the code.

The key parameters are:
- **sprite** — which sprite to animate (`mySprite`)
- **frames** — an array of images `[img\`...\`, img\`...\`, img\`...\`]`
- **interval** — how many milliseconds between frames (`500`)
- **loop** — whether to keep looping (`true`)

```typescript
    animation.runImageAnimation(
        mySprite,
        [img`... frame1 ...`, img`... frame2 ...`, img`... frame3 ...`],
        500,
        true
    )
```

> **Tip:** Copy the full pixel art frames from your working project or the game's source code. Each frame is a 12x16 grid of color codes.

## Step 5: Keep the player on screen

Make sure the player can't walk off the edge:

```typescript
    mySprite.setStayInScreen(true)
```

## Your complete player setup inside intro()

```typescript
function intro() {
    scene.setBackgroundColor(13)
    RamdhanKareem = sprites.create(assets.image`Ramadan Greeting Text`, SpriteKind.Decoration)
    RamdhanKareem.y += -24
    StartText = sprites.create(assets.image`Start Banner`, SpriteKind.StartGate)
    StartText.setScale(0.14, ScaleAnchor.Middle)
    StartText.setPosition(128, 100)
    mySprite = sprites.create(assets.image`Boy-standing`, SpriteKind.Player)
    controller.player1.moveSprite(mySprite)
    mySprite.setPosition(20, 101)
    mySprite.setScale(2, ScaleAnchor.Middle)
    animation.runImageAnimation(mySprite, [ /* your 3 frames here */ ], 500, true)
    mySprite.setStayInScreen(true)
}
```

## Understanding multi-frame animation

Each frame in the animation array is defined using the `img` template literal. The letters and numbers represent colors in MakeCode's palette — for example `f` is black, `e` is white, `4` is skin tone. A period `.` means transparent.

Try changing the interval from `500` to `200` to make the character walk faster!

## Done! @showdialog

Your player is walking on screen! 🚶 In the next tutorial, you'll add directional animations so the character faces the right way when moving left or right.
