# Spawn Pahala Coins

## Earn Your Rewards! @showdialog

**Pahala** means spiritual reward in Arabic and Indonesian. In this phase, your player collects 10 glowing coin sprites representing good deeds during Ramadan. You'll learn how to use loops with `pause()` to create a satisfying drip-feed of collectibles.

## Step 1: Declare the coin variable

At the bottom of your project, add:

```typescript
let GetPahala: Sprite = null
```

## Step 2: Understand the timing pattern

Instead of spawning all 10 coins at once, we use a loop with `pause(500)` inside it. This means one coin appears every 0.5 seconds, giving the player time to react and move toward each one as it appears.

```typescript
for (let index = 0; index < 10; index++) {
    // create coin
    pause(500)
}
```

## Step 3: Spawn the Pahala coins

Inside the loop, create a coin sprite at a random position. The coin image is a 16x16 gold coin with a highlighted center:

```typescript
    for (let index = 0; index < 10; index++) {
        GetPahala = sprites.create(img`
            . . . . . . . . . . . . . . . . 
            . . . . . . . . . . . . . . . . 
            . . . . . 4 4 4 4 4 . . . . . . 
            . . . 4 4 4 5 5 5 d 4 4 4 4 . . 
            . . 4 d 5 d 5 5 5 d d d 4 4 . . 
            . . 4 5 5 1 1 1 d d 5 5 5 4 . . 
            . 4 5 5 5 1 1 1 5 1 1 5 5 4 4 . 
            . 4 d d 1 1 5 5 5 1 1 5 5 d 4 . 
            . 4 5 5 1 1 5 1 1 5 5 d d d 4 . 
            . 2 5 5 5 d 1 1 1 5 1 1 5 5 2 . 
            . 2 d 5 5 d 1 1 1 5 1 1 5 5 2 . 
            . . 2 4 d d 5 5 5 5 d d 5 4 . . 
            . . . 2 2 4 d 5 5 d d 4 4 . . . 
            . . 2 2 2 2 2 4 4 4 2 2 2 . . . 
            . . . 2 2 4 4 4 4 4 4 2 2 . . . 
            . . . . . 2 2 2 2 2 2 . . . . . 
            `, SpriteKind.Coin)
        GetPahala.setPosition(randint(0, 100), randint(0, 100))
        pause(500)
    }
```

## Step 4: Where does this code go?

This loop belongs inside the `Sahur()` function — specifically called **after** the food-spawning loop. The game flow is:

1. `intro()` — greeting screen
2. Player walks into Start Gate → `Sahur()` runs
3. Inside `Sahur()`: food loop runs, then coin loop runs
4. Player collects all foods → Next button appears
5. Player touches Next button → `Puasa()` runs

So the Pahala coins spawn alongside the Sahur food, but they use a different sprite kind (`Coin` vs `Food`) so their overlap events are handled separately.

## Step 5: Handle coin collection

Add an overlap event for `Coin` sprites (outside `Sahur()`):

```typescript
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    sprites.destroy(otherSprite)
    if (info.score() < 5) {
        music.play(
            music.createSoundEffect(WaveShape.Square, 400, 600, 255, 0, 100, SoundExpressionEffect.None, InterpolationCurve.Linear),
            music.PlaybackMode.UntilDone
        )
    }
    if (info.score() == 10) {
        NextButton = sprites.create(assets.image`NextButtonIcon`, SpriteKind.FinishSahur)
        NextButton.setScale(0.15, ScaleAnchor.Middle)
        NextButton.setPosition(144, 102)
        animation.runImageAnimation(NextButton, assets.animation`myAnim1`, 200, true)
    }
})
```

The Pahala coins unlock the Next button at score **10** (vs food at **15**).

## Challenge: Change the coin spawn range

The coins spawn in a `randint(0, 100)` area. Try changing the max value to `150` or adding a minimum like `randint(20, 130)` to spread them more evenly and avoid corners.

## Done! @showdialog

Pahala coins are flowing! 🪙 In the final tutorial, you'll wire up the animated Next button and complete the full game loop.
