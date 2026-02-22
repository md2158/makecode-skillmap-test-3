# Next Button and Game Flow

## Bring it all together! @showdialog

This is the final tutorial! 🎉

You will wire up the **Next button**, complete the full game loop, and add a win screen.

## Step 1: Wire up the FinishSahur overlap

Add a new **on Player overlaps FinishSahur** block from ``||sprites:Sprites||``.

This fires when the player walks into the Next button. For now add a win splash — you can replace this with a full Puasa phase later:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.FinishSahur, function (sprite, otherSprite) {
    game.splash("Selamat Berpuasa! 🌙")
    game.splash("Ramadan Kareem! ✨")
    game.over(true)
})
```

Find ``||game:game over WIN||`` in ``||game:Game||`` — set it to **WIN** (true) so the player sees the victory screen!

~hint Build the Puasa phase! 💡
Instead of game over, you could call a **Puasa()** function that starts a new scene — maybe a daytime sky where the player must avoid food sprites for 30 seconds using a countdown timer!
hint~

## Step 2: Review all 4 overlap events

Make sure your project has all four overlap events connected and in the right order:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.StartGate, function (sprite, otherSprite) {
    scene.setBackgroundImage(img`
        7 7 7 7 7 7 e e e e e e
        7 7 7 7 7 7 e e e e e e
    `)
    RamdhanKareem.destroy()
    StartText.destroy()
    info.setScore(0)
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.FinishSahur, function (sprite, otherSprite) {
    game.over(true)
})
```

## Step 3: Full game test

Press **Play** ▶️ and run through the complete game:

1. ✅ Intro screen loads — dark sky, banner, gate
2. ✅ Walk into gate — Sahur scene appears with trees
3. ✅ Food and coins spawn one by one
4. ✅ Collect them — score increases, sound plays
5. ✅ Score hits target — Next button appears
6. ✅ Walk into Next button — win screen! 🎉

## Congratulations! @showdialog

You have completed the full **Ramadan Game Skillmap**! 🎉🌙

You learned how to:
- ✅ Create custom Sprite Kinds
- ✅ Build a multi-scene animated game
- ✅ Use overlap events to drive game flow
- ✅ Spawn collectibles with loops and timing
- ✅ Chain all phases into a complete game loop

**Ramadan Kareem! 🌙✨**
