---
tags: [component, CG_Drawing]
---
- Path: `app.js` §2 (`transpile()`)
- Role: converts a supported subset of OpenGL/GLUT C++ (includes, float suffixes, `display()`/`main()`, loops, locals, math) into JS run via `new Function(sandbox)` against the [[GLEmulator]].
- Talks to: [[GLEmulator]]
- Back: [[ARCHITECTURE]]
