# Unlock the Next Button & Complete the Game Loop

## Bring It All Together! @showdialog

This is the final tutorial! You'll wire up the animated **Next button** that appears when the player reaches the score target, and connect all the game phases into one complete flow. By the end, you'll have a fully working Ramadan game! 🌙

## Recap: The full game flow

```
intro()
    ↓ player walks into Start Gate
Sahur()
    ↓ player collects 15 foods OR 10 coins
Next button appears (FinishSahur sprite)
    ↓ player walks into Next button
Puasa()
```

## Step 1: The Next button sprite

The Next button is a `FinishSahur` sprite. It uses an image asset and an **animation** to pulse or glow to draw the player's attention. We've already added this inside the overlap events — let's understand it fully:

```typescript
NextButton = sprites.create(assets.image`NextButtonIcon`, SpriteKind.FinishSahur)
NextButton.setScale(0.15, ScaleAnchor.Middle)
NextButton.setPosition(144, 102)
animation.runImageAnimation(
    NextButton,
    assets.animation`myAnim1`,
    200,
    true
)
```

- `setScale(0.15, ...)` — the raw asset is large, so we scale it down to 15% of its original size
- `setPosition(144, 102)` — places it in the lower-right corner
- `animation.runImageAnimation` with `myAnim1` — plays a looping animation from your assets (e.g. a pulsing glow effect)
- `200` milliseconds per frame — fast enough to look animated

## Step 2: The FinishSahur overlap event

When the player touches the `FinishSahur` sprite, the next phase begins. This event must be declared **outside** all functions, at the top level:

```typescript
sprites.onOverlap(SpriteKind.Player, SpriteKind.FinishSahur, function (sprite, otherSprite) {
    Puasa()
})
```

## Step 3: Create the Puasa() function

`Puasa` means fasting. This is the next phase of the game. For now, create a placeholder — you can expand it with new scenes, countdown timers, or more collectibles in the future!

```typescript
function Puasa() {
    // The fasting phase begins here!
    // Ideas to add:
    // - New background (daytime scene)
    // - Countdown timer for how long to avoid food
    // - Bonus collectibles (prayers, good deeds)
    game.splash("Selamat Berpuasa! 🌙")
}
```

## Step 4: Review all your overlap events

Make sure you have these three overlap events at the top level of your project:

```typescript
// 1. Start the Sahur phase
sprites.onOverlap(SpriteKind.Player, SpriteKind.StartGate, function (sprite, otherSprite) {
    Sahur()
})

// 2. Collect food during Sahur
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    sprites.destroy(otherSprite)
    if (info.score() < 5) {
        music.play(music.createSoundEffect(WaveShape.Square, 400, 600, 255, 0, 100, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
    }
    if (info.score() == 15) {
        NextButton = sprites.create(assets.image`NextButtonIcon`, SpriteKind.FinishSahur)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(142, 101)
        animation.runImageAnimation(NextButton, assets.animation`myAnim1`, 200, true)
    }
})

// 3. Collect Pahala coins
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    sprites.destroy(otherSprite)
    if (info.score() < 5) {
        music.play(music.createSoundEffect(WaveShape.Square, 400, 600, 255, 0, 100, SoundExpressionEffect.None, InterpolationCurve.Linear), music.PlaybackMode.UntilDone)
    }
    if (info.score() == 10) {
        NextButton = sprites.create(assets.image`NextButtonIcon`, SpriteKind.FinishSahur)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(144, 102)
        animation.runImageAnimation(NextButton, assets.animation`myAnim1`, 200, true)
    }
})

// 4. Move to the Puasa phase
sprites.onOverlap(SpriteKind.Player, SpriteKind.FinishSahur, function (sprite, otherSprite) {
    Puasa()
})
```

## Step 5: The game entry point

Make sure the very last line of your project calls `intro()`:

```typescript
intro()
```

This is your game's entry point — everything else is triggered by player actions and overlap events.

## Ideas to extend the game

Now that the foundation is complete, here are some things you could add:

- A **countdown timer** in the Puasa phase — can the player go 30 seconds without touching food?
- A **high score** display using `game.showLongText()` at the end
- **Background music** using `music.play()` at the start of each phase
- A **difficulty system** that makes food spawn faster on repeat playthroughs
- More **SpriteKind** types for prayer mats, lanterns, and crescents

## Done! @showdialog

Congratulations — you've completed the full Ramadan Game skillmap! 🎉🌙

You've learned how to:
- Create custom sprite kinds
- Build animated multi-scene games
- Use overlap events to drive game flow
- Spawn collectibles with loops and timing
- Chain game phases with functions

Ramadan Kareem! ✨
