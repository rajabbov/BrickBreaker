# BrickBreaker

![Kotlin](https://img.shields.io/badge/Kotlin-7F52FF?logo=kotlin&logoColor=white) ![Android](https://img.shields.io/badge/Android-3DDC84?logo=android&logoColor=white) ![minSdk 24](https://img.shields.io/badge/minSdk_24-555)

A full Breakout-style arcade game written **without a game engine** — just Android Views, a `ValueAnimator` as the game loop and hand-written collision maths. Clear 90 bricks with a paddle you drag along the bottom of the screen, and don't lose all three balls.

## Features

- **90 bricks** in a 9 × 10 grid, generated in code
- **Touch-controlled paddle** — follows your finger horizontally
- **Physics** — bounces off walls, the ceiling, the paddle and bricks; bricks disappear on hit
- **3 lives** with a message after each lost ball, then a game-over screen
- **Live score** counter

## How it works

### Game loop
Instead of a `SurfaceView` thread, a `ValueAnimator` with an effectively infinite duration fires on every frame. Each tick calls `moveBall()` and `checkCollision()`, then positions the views — simple, smooth and tied to the display's refresh rate.

### Collisions
Axis-aligned bounding-box checks against the screen edges, the paddle and each brick:

```kotlin
if (ballY + ball.height >= paddle.y && ballY + ball.height <= paddle.y + paddle.height
    && ballX + ball.width >= paddle.x && ballX <= paddle.x + paddle.width) {
    ballSpeedY *= -1
}
```
Hitting the bottom edge costs a life and resets the ball; at zero lives, `gameOver()` shows the result.

## Project structure

```
com.example.brickbreaker
└── MainActivity.kt
```

<sub>1 source file · 211 lines of code · 1 layout</sub>

## Tech stack

| | |
|---|---|
| **Language** | Kotlin |
| **UI** | XML layouts |
| **Min / Target SDK** | 24 / 34 |

## Getting started

```bash
git clone https://github.com/rajabbov/BrickBreaker.git
```

1. Open the folder in **Android Studio** (Ladybug or newer).
2. Let Gradle sync.
3. Run the `app` configuration on a device or emulator.

## Known limitations

- No levels or increasing speed yet — a natural next step.

---

Made by **Ibrohimjon Rajabboyev** · [@rajabbov](https://github.com/rajabbov)
