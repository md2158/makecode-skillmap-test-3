# Create Custom Sprite Kinds

## Welcome to the Ramadan Game! @showdialog

In this tutorial, you'll learn how to define **custom Sprite Kinds** — special categories that let MakeCode Arcade tell different types of sprites apart, like players, coins, food, and decorations.

By the end, you'll have all the sprite kinds you need for the full Ramadan game!

## What is a Sprite Kind?

MakeCode Arcade comes with built-in kinds like `Player`, `Enemy`, and `Food`. But for our game we need more — like a `StartGate`, `Coin`, `Trees`, and more.

We create them inside a `namespace SpriteKind` block using `SpriteKind.create()`.

## Step 1: Open the namespace

At the top of your project, before anything else, add this block to define your custom sprite kinds:

```typescript
namespace SpriteKind {
    export const Decoration = SpriteKind.create()
    export const Table = SpriteKind.create()
    export const FinishSahur = SpriteKind.create()
    export const Trees = SpriteKind.create()
    export const StartGate = SpriteKind.create()
    export const Coin = SpriteKind.create()
}
```

## Step 2: Understand each kind

Here's what each custom kind is for in our game:

- **Decoration** — Background art like the "Ramadan Kareem" banner
- **Table** — Reserved for future use (food tables)
- **FinishSahur** — The animated Next button that appears when Sahur is complete
- **Trees** — Decorative trees in the outdoor Sahur scene
- **StartGate** — The banner the player walks into to begin the Sahur phase
- **Coin** — The Pahala (reward) coins the player collects

## Step 3: Why is this important?

Custom sprite kinds are what make `sprites.onOverlap()` work correctly. When the player touches a `StartGate`, the game knows to start the Sahur phase. When they touch a `Coin`, it increases the score. Without separate kinds, the game couldn't tell them apart!

## Try it!

Add the `namespace SpriteKind` block to your project. Notice how the new kinds now appear in the Sprites dropdown throughout MakeCode.

```typescript
namespace SpriteKind {
    export const Decoration = SpriteKind.create()
    export const Table = SpriteKind.create()
    export const FinishSahur = SpriteKind.create()
    export const Trees = SpriteKind.create()
    export const StartGate = SpriteKind.create()
    export const Coin = SpriteKind.create()
}
```

## Done! @showdialog

Great work! You now have 6 custom sprite kinds ready to use throughout your game. In the next tutorial, you'll use `Decoration` and `StartGate` to build the intro screen. Keep going! 🌙
