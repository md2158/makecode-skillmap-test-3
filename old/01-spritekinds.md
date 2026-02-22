# Create Custom Sprite Kinds

## Welcome! @showdialog

In this tutorial, you will learn how to create **custom Sprite Kinds** for the Ramadan game.

Sprite Kinds help the game tell different sprites apart — like the player, coins, food, and trees!

## What are Sprite Kinds? @showdialog

MakeCode Arcade already has kinds like **Player**, **Enemy**, and **Food**.

But our Ramadan game needs more kinds:
- 🎋 **Decoration** — banners and background art
- 🚪 **StartGate** — the banner the player walks into
- ✨ **FinishSahur** — the Next button that appears when done
- 🌳 **Trees** — decorative trees
- 🪙 **Coin** — Pahala reward coins

## Step 1: Open the Sprite Kind menu

Click on ``||sprites:Sprites||`` in the toolbox.

Scroll down and find **"Set sprite kind"** blocks — these let you pick which kind a sprite is.

## Step 2: See the kinds in action

Every time you create a sprite, you choose its kind. Like this:

```blocks
let mySprite = sprites.create(img`
    . . . . . . . . 
    . . . . . . . . 
    `, SpriteKind.Player)
```

## Step 3: Try it yourself!

Drag out a ``||sprites:set mySprite to sprite of kind Player||`` block from the Sprites toolbox.

Click the **Player** dropdown — you can see all the built-in kinds. In later steps you will add your own!

## Great work! @showdialog

You now understand Sprite Kinds! 🌙

In the next tutorial you will use these kinds to build the **intro screen**.
