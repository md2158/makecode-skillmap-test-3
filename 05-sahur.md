# Build the Sahur Scene

## The Sahur Phase Begins! @showdialog

**Sahur** is the pre-dawn meal eaten before fasting during Ramadan. 🌙🍱

When the player walks into the Start Gate, the game transitions to an outdoor Sahur scene.

In this tutorial you will swap the background, clean up intro sprites, and place decorative trees.

## Step 1: Swap background and clean up intro

Go to your **on Player overlaps StartGate** block from Tutorial 2. Delete the splash placeholder.

Set the Sahur background image and destroy the intro sprites, then reset the score:

```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.StartGate, function (sprite, otherSprite) {
    scene.setBackgroundImage(img`
        7 7 7 7 7 7 7 7 7 7 7 7 7 7 7 7
        7 7 7 7 7 7 7 7 7 7 7 7 7 7 7 7
        e e e e e e e e e e e e e e e e
        e e e e e e e e e e e e e e e e
    `)
    RamdhanKareem.destroy()
    StartText.destroy()
    info.setScore(0)
    sprites.destroy(NextButton)
})
```

~hint Background image tip 💡
Click the image box → switch to **My Assets** → select your **Sahur Background** image!
hint~

## Step 2: Place trees on the left side

Add 2 green trees on the left side of the scene to frame the outdoor setting.

Still inside the overlap block, create both tree sprites and position them:

```blocks
    let tree1 = sprites.create(img`
        . . . 7 9 . . . 7 9 . . . . . .
        . . 9 9 9 9 9 . 7 9 9 . . . . .
        . 9 3 3 7 7 . 9 6 9 7 . . . . .
        . . . . . . . . . . . . . . . .
        . . . . 4 e e e e . . . . . . .
        . . . . 4 e e e c . . . . . . .
        . . . e 4 e e c e . . . . . . .
        . . . e e e e c e . . . . . . .
        . . . . 4 e e e c . . . . . . .
        . . . . . e e e . . . . . . . .
        `, SpriteKind.Trees)
    tree1.setPosition(30, 79)
    let tree2 = sprites.create(img`
        . . . 7 9 . . . 7 9 . . . . . .
        . . 9 9 9 9 9 . 7 9 9 . . . . .
        . . . . 4 e e e e . . . . . . .
        . . . . 4 e e e c . . . . . . .
        . . . e 4 e e c e . . . . . . .
        . . . . . e e e . . . . . . . .
        `, SpriteKind.Trees)
    tree2.setPosition(11, 100)
```

## Step 3: Place trees on the right side

Add 2 teal-toned trees on the right for visual variety and depth:

```blocks
    let tree3 = sprites.create(img`
        . . . 7 5 . . . 7 5 . . . . . .
        . . 5 5 5 5 5 . 7 5 5 . . . . .
        . . . . 4 e e e e . . . . . . .
        . . . . 4 e e e c . . . . . . .
        . . . e 4 e e c e . . . . . . .
        . . . . . e e e . . . . . . . .
        `, SpriteKind.Trees)
    tree3.setPosition(115, 69)
    let tree4 = sprites.create(img`
        . . . 7 5 . . . 7 5 . . . . . .
        . . 5 5 5 5 5 . 7 5 5 . . . . .
        . . . . 4 e e e e . . . . . . .
        . . . . 4 e e e c . . . . . . .
        . . . . . e e e . . . . . . . .
        `, SpriteKind.Trees)
    tree4.setPosition(134, 85)
```

Press **Play** ▶️ → walk into the gate → you should see the outdoor scene with all 4 trees! 🌳

## Done! @showdialog

The Sahur outdoor scene is set! 🌳🌙

Next up — **spawning Sahur food** for the player to collect!
