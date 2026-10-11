Known bugs
================================================================================

- Blank on playfield. Press ESC to bring up menu should fixed it, otherwise
  restart the game.
- Blank on options menu, restart the game.


Tracking down a blank frame
================================================================================

The 60 Hz presentation shows a replay of the recorded frame rather than the
framebuffer itself, so a replay bug shows up directly on screen. To find one,
run with `--regress-interp-check`: it renders every tick through the
interpolated renderer at alpha = 1 and reports the first pixel that differs
from the real frame. `--regress-replay-check` does the same via the plain
replay path.

Results go to `drawlist-regress.log`, next to `opentyrian.cfg` in the working
directory. It is written as frames are checked, not only when you quit, so a
crash or a hard kill still leaves you something to read. The game is a
GUI-subsystem binary, which is why this file exists: `stderr` is thrown away
unless you redirect it by hand.
