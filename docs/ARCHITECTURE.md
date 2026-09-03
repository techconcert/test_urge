# Architecture

## Delivery model

`index.html` is the complete application. It contains markup, CSS, JavaScript, and GLSL strings so a prototype can be copied into a static host or evaluated without a build system.

## Rendering modules

Each visual is isolated in a class and owns its canvas, graphics context, animation loop, and pointer handlers.

| Module | Technology | Purpose |
| --- | --- | --- |
| `Option1_ShaderView` | WebGL fragment shader | Quiet Flow water and rocks |
| `Option5_AerialDriftView` | WebGL fragment shader | Slow overhead variation of the water world |
| `Option2_FluidSolverView` | WebGL 2 | Interactive ink/fluid solver |
| `Option3_ClearDepthsView` | Canvas 2D | Murky pond and timed finger reveals |
| `Option4_TouchGrassView` | Canvas 2D | Spring-based grass interaction |
| `Option1b_OceanJourneyView` | WebGL + foam feedback buffer | Anchor progression and ripple interaction |

The session shell creates these modules, starts only the selected view, and leaves the others stopped. This separation makes it safe to move a winning experience into a future native or web application.

## Shared session state

The session shell owns a single `SESSION_DURATION` and `remaining` value. Switching modes must not reset this value. The small timer reset button restarts the shared session deliberately.

Anchor has its own visual journey state, including phase labels and feedback-buffer foam. Its rendering state is separate from the shared countdown.

## Motion and interaction

Motion should remain low-frequency and legible. Avoid sharp geometry morphs, abrupt scene replacement, rapid autonomous movement, and reward-style random events. Pointer interactions should provide immediate but soft feedback and should not require precision.

## Adding a view

1. Add a canvas section using the `view` class.
2. Implement a self-contained renderer class with `start()` and `stop()` methods.
3. Add the instance to `views` and register its mode button.
4. Add translated title, guidance, and hint keys.
5. Verify that switching into and out of the view preserves the shared timer.
