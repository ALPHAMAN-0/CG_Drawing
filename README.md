# Coordinate Visualizer

An **AIUB Computer Graphics** study tool. Paste your OpenGL / GLUT **C++** code and instantly see two synced views:

- **Graph View** — OpenGL's coordinate plane as labeled graph paper: origin at the center, X/Y axes, gridlines, range `-1 … +1`, **y pointing up**. Every `glVertex2f` is plotted as a dot and labeled with its exact `(x, y)`.
- **GLUT Display View** — the shape rendered exactly as it appears in the real OpenGL window: black background from `glClearColor`, correct window size from `glutInitWindowSize` (e.g. `320×320`, `500×500`), filled primitives.

It solves the everyday CG problem: *"which coordinates produce this shape, and what does that point look like on screen?"*

## Live demo

`https://<user>.github.io/<repo>/`

> Replace `<user>/<repo>` with your GitHub username and repository name.

## How it works

`paste C++` → **transpile to JavaScript** → run against a **Canvas-2D emulation of OpenGL immediate mode** → record draw commands → repaint both views + the vertex table. Everything runs in your browser — no server, no build, no install.

## Supported GL / GLUT subset

- **Drawing:** `glClearColor`, `glClear(GL_COLOR_BUFFER_BIT)`, `glFlush`, `glPointSize`, `glLineWidth`, `glBegin`/`glEnd` with `GL_POINTS`, `GL_LINES`, `GL_LINE_LOOP`, `GL_LINE_STRIP`, `GL_TRIANGLES`, `GL_TRIANGLE_FAN`/`STRIP`, `GL_QUADS`, `GL_QUAD_STRIP`, `GL_POLYGON`, `glColor3f` (0–1), `glColor3ub` (0–255), `glVertex2f` (+ `2i`/`2d`).
- **GLUT:** `glutInit`, `glutInitWindowSize`, `glutInitWindowPosition`, `glutInitDisplayMode`, `glutCreateWindow`, `glutDisplayFunc`, `glutMainLoop`, plus your `initGL()`.
- The transpiler also handles real C++ niceties: `#include`, `1.0f`/`-.7f` float suffixes, `void display()` / `int main(int argc, char** argv)`, `for` loops, local variables (`float`/`int`/`double`), and math (`sin`, `cos`, `sqrt`, `M_PI`, …).

Anything outside this subset shows a friendly message rather than crashing.

## Presets

Load any example from the **Preset** dropdown: the tutorial set (white window, points, line, X/Y axes, polygon, 4-objects-in-4-quadrants), **Lab Task-1** (rectangle, red trapezoid, 4 colored quadrant objects), **Class Task-1** (nested R/G/B triangles, `500×500`), and assignment stubs (rainbow flag, AIUB text). Load a task, screenshot both views, and drop them into your submission.

## Run locally

No build, no npm. Either:

```bash
# option A: just open the file
open index.html

# option B: serve it (recommended)
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deployment (GitHub Pages)

Pushing to `main` auto-publishes via [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).

**One-time setup:** in the repo, go to **Settings → Pages → Build and deployment → Source = "GitHub Actions"**. For a free account the repo must be **public**.

## Project structure

```
index.html                  # app shell
styles.css                  # styling
app.js                      # transpiler + GL emulator + dual-canvas renderer + presets
README.md
.github/workflows/deploy.yml
```

## Credits

Built for the AIUB Computer Graphics course. Not affiliated with Khronos or the OpenGL project; emulates a small subset of the API for learning purposes.
