# Custom Sprite Kinds

## Welcome to the Ramadan Game! @showdialog

Selamat datang! 🌙

In this tutorial you will add **custom Sprite Kinds** — special labels that help the game tell different objects apart, like coins, food, trees, and gates.

## Step 1: What are Sprite Kinds?

Every sprite needs a **Kind**. MakeCode Arcade has built-in kinds like Player, Enemy, and Food — but our Ramadan game needs its own!

Click on any **create sprite** block, open the **Kind** dropdown, scroll to the bottom and click **"Add a new kind..."**

Add these 5 kinds one by one:
- **Decoration** — the Ramadan Kareem banner
- **StartGate** — the banner the player walks into
- **FinishSahur** — the Next button that appears when done
- **Trees** — decorative trees in the scene
- **Coin** — Pahala reward coins

```blocks
let test = sprites.create(img`
    . . . . . . . . 
    . . . . . . . . 
    `, SpriteKind.Decoration)
```

## Step 2: Why kinds matter — overlaps

Kinds are what make **overlap events** work. The game checks which kinds touched and fires the right event.

Drag out an **on sprite overlaps** block from ``||sprites:Sprites||``. Notice the two Kind dropdowns — your custom kinds now appear in both!

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.StartGate, function (sprite, otherSprite) {
    game.splash("Gate touched!")
})
sprites.onOverlap(SpriteKind.Player, SpriteKind.Coin, function (sprite, otherSprite) {
    game.splash("Coin collected!")
})
```

~hint Why not just use Food for everything? 💡
If coins and food were both **Food** kind, the game couldn't tell them apart — collecting a coin would trigger the food event too! Separate kinds give each object its own identity.
hint~

## Step 3: Confirm and clean up

Delete the test sprites and overlap blocks — these were just to check everything works.

Check your Kind dropdown on any sprite block. You should see all 5 custom kinds listed alongside the built-in ones:

```blocks
let a = sprites.create(img`
    . . . . . . . .
    . . . . . . . .
    `, SpriteKind.Decoration)
let b = sprites.create(img`
    . . . . . . . .
    . . . . . . . .
    `, SpriteKind.StartGate)
let c = sprites.create(img`
    . . . . . . . .
    . . . . . . . .
    `, SpriteKind.FinishSahur)
```

## Done! @showdialog

All 5 custom Sprite Kinds are ready! 🎉

Next up — building the **Intro Screen** with the Ramadan Kareem banner and Start Gate!
