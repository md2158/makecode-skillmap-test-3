# Build the Sahur Scene

## The Sahur Phase Begins! @showdialog

**Sahur** is the pre-dawn meal Muslims eat before fasting begins during Ramadan. In this tutorial, you'll build the Sahur scene — swapping the intro background for an outdoor setting and placing decorative trees around the screen.

## Step 1: Create the Sahur function

Create a new function called `Sahur()`. This will be called when the player touches the Start Gate.

```typescript
function Sahur() {
    // We'll build this step by step
}
```

## Step 2: Set the Sahur background

Replace the solid background color with a detailed background image of an outdoor Sahur setting:

```typescript
function Sahur() {
    scene.setBackgroundImage(assets.image`Sahur Background`)
}
```

## Step 3: Destroy the intro sprites

The "Ramadan Kareem" banner and Start Gate banner from the intro screen are no longer needed. Destroy them to clean up the scene:

```typescript
    sprites.destroy(RamdhanKareem)
    sprites.destroy(StartText)
```

## Step 4: Reset the score

When entering the Sahur phase, reset the score back to 0 so the player starts fresh:

```typescript
    info.setScore(0)
```

Also destroy the `NextButton` in case it was left over from a previous run:

```typescript
    sprites.destroy(NextButton)
```

## Step 5: Declare tree variables

At the bottom of your project, add variables for the four trees:

```typescript
let tree1: Sprite = null
let tree2: Sprite = null
let tree3: Sprite = null
let tree4: Sprite = null
```

## Step 6: Place the trees

Add four tree sprites around the screen. Two use a green-toned image, two use a slightly different teal-toned version, giving visual variety. Position them at different spots to frame the scene:

```typescript
    tree1 = sprites.create(img`...`, SpriteKind.Trees)
    tree1.setPosition(30, 79)

    tree2 = sprites.create(img`...`, SpriteKind.Trees)
    tree2.setPosition(11, 100)

    tree3 = sprites.create(img`...`, SpriteKind.Trees)
    tree3.setPosition(115, 69)

    tree4 = sprites.create(img`...`, SpriteKind.Trees)
    tree4.setPosition(134, 85)
```

> **Tip:** Copy the full pixel art for each tree from the game's source code. `tree1` and `tree2` share the same image (green), while `tree3` and `tree4` use a teal variant.

## Tip: Scene layering

In MakeCode Arcade, sprites appear **in front of** the background image. Trees use `SpriteKind.Trees` — not `Player` — so they don't collide with anything. They're purely decorative!

## Your Sahur() function so far

```typescript
function Sahur() {
    scene.setBackgroundImage(assets.image`Sahur Background`)
    sprites.destroy(RamdhanKareem)
    sprites.destroy(StartText)
    info.setScore(0)
    sprites.destroy(NextButton)
    // tree sprites go here...
    tree1 = sprites.create(img`...`, SpriteKind.Trees)
    tree1.setPosition(30, 79)
    tree2 = sprites.create(img`...`, SpriteKind.Trees)
    tree2.setPosition(11, 100)
    tree3 = sprites.create(img`...`, SpriteKind.Trees)
    tree3.setPosition(115, 69)
    tree4 = sprites.create(img`...`, SpriteKind.Trees)
    tree4.setPosition(134, 85)
}
```

## Done! @showdialog

The Sahur scene is looking great! 🌳 In the next tutorial, you'll spawn Sahur food items for the player to collect.
