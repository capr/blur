---
tagline: fast box blur
---

## `local boxblur = require'boxblur'`

Fast box blur algorithm for `bgra8` and `g8` pixel formats.
The implementation is based on the moving-average technique, resulting in
constant time for any blur radius, making it suitable for full-screen
animated blurs.

Speed is 70 fps @ full HD per pass for the color variant, and 300 fps per
pass for the grayscale variant, measured on a 5000-passmark-score CPU.

## API

------------------------------------------------------------ --------------------------------------------------
`boxblur.new(img, max_radius, [passes], [format]) -> blur`   create a new blur object for a [bitmap]
`blur:blur([radius], [passes]) -> bmp`                       blur `img` (returns a [bitmap])
`blur:invalidate()`                                          tell blur that the source image changed
------------------------------------------------------------ --------------------------------------------------

A blur object holds all the temporary buffers necessary for blurring the same
image multiple times using a different radius without allocating new memory
each time. Each blur action returns a potentially different [bitmap] object.
