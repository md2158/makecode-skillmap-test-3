# Build the Intro Screen

## Let's Set the Scene! @showdialog

In this tutorial, you'll build the **intro screen** for the Ramadan game. This is the first thing the player sees — a beautiful opening with a "Ramadan Kareem" greeting and a start banner to walk into.

## Step 1: Create the intro function

We wrap the intro setup in a **function** called `intro()`. This keeps our code organised and easy to call later.

```typescript
function intro() {
    // We'll fill this in step by step
}
```

At the very bottom of your project, call the function so it runs when the game starts:

```typescript
intro()
```

## Step 2: Set the background color

Inside `intro()`, set the background to a dark blue — color `13` — to give the night sky feel of Ramadan.

```typescript
function intro() {
    scene.setBackgroundColor(13)
}
```

## Step 3: Add the Ramadan Kareem banner

Create a sprite using your greeting image asset and assign it the `Decoration` kind. Nudge it upward so it sits at the top of the screen.

```typescript
    RamdhanKareem = sprites.create(assets.image`Ramadan Greeting Text`, SpriteKind.Decoration)
    RamdhanKareem.y += -24
```

## Step 4: Add the Start Gate banner

Create the start banner the player walks into to begin playing. Scale it down and position it center-right.

```typescript
    StartText = sprites.create(assets.image`Start Banner`, SpriteKind.StartGate)
    StartText.setScale(0.14, ScaleAnchor.Middle)
    StartText.setPosition(128, 100)
```

## Step 5: Declare your variables

Outside all functions at the bottom of your project, declare these variables:

```typescript
let RamdhanKareem: Sprite = null
let StartText: Sprite = null
let mySprite: Sprite = null
let NextButton: Sprite = null
```

## Step 6: Wire up the Start Gate overlap

When the player touches the `StartGate`, call `Sahur()` to move to the next phase. Add this outside the `intro()` function:

```typescript
sprites.onOverlap(SpriteKind.Player, SpriteKind.StartGate, function (sprite, otherSprite) {
    Sahur()
})
```

> **Note:** You'll build `Sahur()` in a later tutorial. For now add a placeholder: `function Sahur() {}`

## Your full intro() so far

```typescript
function intro() {
    scene.setBackgroundColor(13)
    RamdhanKareem = sprites.create(assets.image`Ramadan Greeting Text`, SpriteKind.Decoration)
    RamdhanKareem.y += -24
    StartText = sprites.create(assets.image`Start Banner`, SpriteKind.StartGate)
    StartText.setScale(0.14, ScaleAnchor.Middle)
    StartText.setPosition(128, 100)
}

intro()
```

## Done! @showdialog

Your intro screen is ready! 🌙 The greeting banner and start gate are in place. Next, you'll add your animated player character.
