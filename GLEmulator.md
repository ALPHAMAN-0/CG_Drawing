---
tags: [component, CG_Drawing]
---
- Path: `app.js` §1 (`GL_FUNCS`, `GL_CONSTS`, `resetGL()`, `G` state)
- Role: emulates a subset of OpenGL/GLUT immediate mode (`glVertex2f`, `glBegin/End`, `glutInitWindowSize`, etc.) over Canvas-2D, recording draw commands into `G.commandList`; color stored internally as 0–255 ints.
- Talks to: [[Transpiler]]
- Back: [[ARCHITECTURE]]
