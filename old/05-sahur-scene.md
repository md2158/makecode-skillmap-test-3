# Build the Sahur Scene

## The Sahur Phase Begins! @showdialog

**Sahur** is the pre-dawn meal eaten before fasting starts during Ramadan. 🌙

In this tutorial you will build the Sahur scene by:
- Swapping in a new background image
- Removing the intro sprites
- Placing decorative trees around the screen

## Step 1: Swap the background

When the player touches the Start Gate, the scene changes. Inside your **on sprite overlaps** block, add a **set background image** block:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    scene.setBackgroundImage(img`
        7 7 7 7 7 7 7 7 7 7 7 7 7 7 7 7
        7 7 7 7 7 7 7 7 7 7 7 7 7 7 7 7
        e e e e e e e e e e e e e e e e
        e e e e e e e e e e e e e e e e
    `)
})
```

~hint How do I use my real background? 💡
Click the grey image box and switch to the **My Assets** tab. Choose your **Sahur Background** asset!
hint~

## Step 2: Destroy the intro sprites

The greeting banner and start gate are no longer needed. Add **destroy sprite** blocks for both:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
    scene.setBackgroundImage(img`
        7 7 7 7 7 7 7 7
        e e e e e e e e
    `)
    RamdhanKareem.destroy()
    StartText.destroy()
})
```

## Step 3: Reset the score

At the start of Sahur, reset the score back to zero:

```blocks
    info.setScore(0)
```

Find this in ``||info:Info||`` → **set score to 0**.

## Step 4: Place Tree 1 and Tree 2

Create two tree sprites using your tree pixel art and position them on the left side of the screen:

```blocks
let tree1 = sprites.create(img`
    . . . 7 9 . . . 7 9 . . . . . .
    . . 9 9 9 9 9 . 7 9 9 . . . . .
    . 9 3 3 7 7 . 9 6 9 7 4 7 6 . .
    . . . . . . . . . . . . . . . .
    . . . . 4 e e e e . . . . . . .
    . . . . 4 e e e c . . . . . . .
    . . . . 4 e e e c . . . . . . .
    . . . e 4 e e c e . . . . . . .
    `, SpriteKind.Player)
tree1.setPosition(30, 79)

let tree2 = sprites.create(img`
    . . . 7 9 . . . 7 9 . . . . . .
    . . 9 9 9 9 9 . 7 9 9 . . . . .
    . . . . 4 e e e e . . . . . . .
    . . . . 4 e e e c . . . . . . .
    `, SpriteKind.Player)
tree2.setPosition(11, 100)
```

## Step 5: Place Tree 3 and Tree 4

Add two more trees on the right side using a slightly different teal-toned image:

```blocks
let tree3 = sprites.create(img`
    . . . 7 5 . . . 7 5 . . . . . .
    . . 5 5 5 5 5 . 7 5 5 . . . . .
    . . . . 4 e e e e . . . . . . .
    . . . . 4 e e e c . . . . . . .
    `, SpriteKind.Player)
tree3.setPosition(115, 69)

let tree4 = sprites.create(img`
    . . . 7 5 . . . 7 5 . . . . . .
    . . 5 5 5 5 5 . 7 5 5 . . . . .
    . . . . 4 e e e e . . . . . . .
    . . . . 4 e e e c . . . . . . .
    `, SpriteKind.Player)
tree4.setPosition(134, 85)
```

~hint Trees are decoration! 💡
In the full game, trees use a custom **Trees** kind so they do not trigger overlap events. They are just pretty scenery!
hint~

## Done! @showdialog

The Sahur outdoor scene is looking great! 🌳🌙

Next tutorial — spawning Sahur food for the player to collect!
