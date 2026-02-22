# Add Directional Animations

## Make Movement Feel Real! @showdialog

Right now your character walks, but they always face the same direction. In this tutorial, you'll use **controller button events** to swap animations when the player moves left — and restore the default animation when they stop.

## Step 1: Understand controller events

MakeCode Arcade has two kinds of button events:
- `ControllerButtonEvent.Pressed` — fires the moment the button is held down
- `ControllerButtonEvent.Released` — fires the moment the button is let go

We'll use `Pressed` to start the left-facing animation, and `Released` to go back to the default.

## Step 2: Add the left-press animation

When the player presses the **left** button, switch to a set of left-facing walking frames:

```typescript
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    animation.runImageAnimation(
        mySprite,
        [img`... left-frame1 ...`, img`... left-frame2 ...`, img`... left-frame3 ...`],
        500,
        true
    )
})
```

> **Tip:** The left-facing frames are a mirrored version of the right-facing ones. Copy them from the game source — they use the same color palette but the body faces left.

## Step 3: Restore the animation on right release

When the player **releases** the right button (meaning they stop moving right), go back to the neutral walking animation:

```typescript
controller.right.onEvent(ControllerButtonEvent.Released, function () {
    animation.runImageAnimation(
        mySprite,
        [img`... default-frame1 ...`, img`... default-frame2 ...`, img`... default-frame3 ...`],
        500,
        true
    )
})
```

## Why Released and not Pressed for right?

The default animation already plays when the game starts. We only need to *restore* it after the player has moved left. Using `Released` on the right button catches the moment the player stops moving right and snaps back to neutral.

## Step 4: Think about edge cases

What happens if the player presses left and right at the same time? MakeCode will just run whichever event fires last. For this game that's fine — it's a simple side-scroller and we don't need complex state management.

## Full event handlers

```typescript
controller.left.onEvent(ControllerButtonEvent.Pressed, function () {
    animation.runImageAnimation(
        mySprite,
        [ /* 3 left-facing frames */ ],
        500,
        true
    )
})

controller.right.onEvent(ControllerButtonEvent.Released, function () {
    animation.runImageAnimation(
        mySprite,
        [ /* 3 default frames */ ],
        500,
        true
    )
})
```

## Challenge!

Can you add a `controller.right.onEvent(ControllerButtonEvent.Pressed)` handler with a slightly faster animation interval (say `300ms`) to make the character look like they're rushing to the right?

## Done! @showdialog

Your character now faces the right direction when moving! 🎮 You've completed **Path 1**. Head over to **Path 2** to start building the Sahur food-collecting scene!
