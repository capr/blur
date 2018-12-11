---
tagline: fast box blur
---

## `local boxblur = require'boxblur'`

Fast box blur algorithm for `bgra8` and `g8` pixel formats.
The implementation is based on the moving-average technique, resulting in
constant time for any blur radius, making it suitable for full-screen
animated blurs.

Speed is 70 fps @ full HD per pass for the color variant, and 300 fps per
<<<<<<< HEAD
pass for the grayscale variant, measured on a CPU with a single-thread
passmark value of around 2000.
=======
pass for the grayscale variant, measured on a CPU with a single-threaded 
passmark score of around 2000.
>>>>>>> cdfb98e9552a8168fe0753266fb713809b8fa0b4

## API

------------------------------------------------------------ --------------------------------------------------
`boxblur.new(img, max_radius, [passes], [format]) -> blur`   create a blur object for a [bitmap]
`boxblur.new(w, h, format, max_radius, [passes]) -> blur`    create a blur object for painting on
`blur:blur([radius], [passes]) -> bmp`                       blur `img` (returns a [bitmap])
`blur:repaint()`                                             override with painting code
`blur:invalidate()`                                          tell blur that the source image changed
------------------------------------------------------------ --------------------------------------------------

A blur object holds all the temporary buffers necessary for blurring the same
image multiple times using a different radius without allocating new memory
each time. Each call to `blur()` returns a potentially different [bitmap]
object which contains the blurred image.
