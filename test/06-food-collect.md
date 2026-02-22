# Spawn & Collect Sahur Foods

## Time to Eat! @showdialog

In this tutorial, you'll spawn 15 Sahur food sprites across the scene and handle what happens when the player collects them — updating the score, playing a sound, and unlocking the Next button when enough food is collected.

## Step 1: Set up the food image array

Inside `Sahur()`, after placing the trees, define an array of food images. This lets us randomly pick from multiple food types each time we spawn one:

```typescript
    let SahurFoods: Image[] = []
    SahurFoods = [
        img`... food image 1 ...`,
        img`... food image 2 ...`,
        img`... food image 3 ...`
    ]
```

> **Tip:** The game has 3 food images — rice with chicken, a bowl of soup, and another dish. Copy the pixel art from the source code.

Also declare `SahurFood` as a variable at the bottom of your project:

```typescript
let SahurFood: Sprite = null
```

## Step 2: Spawn 15 food sprites with a loop

Use a `for` loop to create 15 food sprites, placing each one at a random position. Add a `pause(500)` between each spawn so they appear one by one rather than all at once:

```typescript
    for (let index = 0; index < 15; index++) {
        SahurFood = sprites.create(SahurFoods[randint(0, 2)], SpriteKind.Food)
        SahurFood.setPosition(randint(0, 100), randint(0, 100))
        SahurFood.setStayInScreen(true)
        pause(500)
    }
```

`randint(0, 2)` picks a random number between 0 and 2 — matching our 3 food images (index 0, 1, 2).

## Step 3: Handle the food overlap event

Outside the `Sahur()` function, add an overlap event for when the player touches a `Food` sprite:

```typescript
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    sprites.destroy(otherSprite)
})
```

This increases the score by 1 and removes the collected food sprite.

## Step 4: Add a sound effect for early collects

Play a short square-wave beep when the score is still under 5. This gives satisfying audio feedback at the start:

```typescript
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    sprites.destroy(otherSprite)
    if (info.score() < 5) {
        music.play(
            music.createSoundEffect(WaveShape.Square, 400, 600, 255, 0, 100, SoundExpressionEffect.None, InterpolationCurve.Linear),
            music.PlaybackMode.UntilDone
        )
    }
})
```

## Step 5: Unlock the Next Button at score 15

When the player collects all 15 food items (score reaches 15), create an animated Next button sprite:

```typescript
    if (info.score() == 15) {
        NextButton = sprites.create(assets.image`NextButtonIcon`, SpriteKind.FinishSahur)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(142, 101)
        animation.runImageAnimation(
            NextButton,
            assets.animation`myAnim1`,
            200,
            true
        )
    }
```

## Step 6: Wire up the FinishSahur overlap

When the player touches the `FinishSahur` Next button, call the next game phase. Add this outside all functions:

```typescript
sprites.onOverlap(SpriteKind.Player, SpriteKind.FinishSahur, function (sprite, otherSprite) {
    Puasa()
})
```

> **Note:** You'll build `Puasa()` later. For now, add a placeholder: `function Puasa() {}`

## Understanding the score logic

Notice the score check uses `== 15` (exactly 15) rather than `>= 15`. This means the Next button only appears the moment the 15th food is collected — not on every overlap after that. This is a common game design pattern for one-time unlock triggers.

## Done! @showdialog

Sahur time is complete! 🍱 The player can now collect 15 food items to unlock the next phase. Up next — the Pahala coin collection phase!
