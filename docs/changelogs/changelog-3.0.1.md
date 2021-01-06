---
layout: default
tab: Manual
---

## Changes in 3.0.1

### Rulesets

* Allowing alternate player models now determined by ruleset
* Ruleset qcon reports the new player model (CapNBubs) as modified
* Changing ruleset or `/allow_scripts` now releases all protected keys.  Blocks `/cl_idrive` workaround.

### Input

* Added `/con_toggle_deadkey` cvar as a workaround for SDL2 deadkey-handling.  Should stop first character typed at the console being corrupt when using a keyboard layout where the console toggle key is also an operating system deadkey.
* Bugfix: keyboard operating system layout is used if the program is started and `/cl_onload` is set to a console command (was previously set to QWERTY until game started).
* Bugfix: `/cl_keypad` cvar operational again, if set (default) then keypad & basic number keys can be bound independently.  If turned off, keypad keys converted to standard keys, bindable as per QWCL.

### Display

* `/gl_loadlitfiles` now controls loading of all colored lighting, regardless if from .lit file or stored in the .bsp file.  Hidden cvar `/gl_noinlinergb` removed.
* Bugfix: horizontal fov was being increased when `/viewsize` caused effective aspect ratio to change.  `/scr_fovmode` cvar controls how ezquake keeps the fov correct.
   * `/scr_fovmode 0` (default) will use the aspect ratio of the monitor and then crop the image vertically.  This matches the approach taken in QWCL
   * `/scr_fovmode 1` will introduce horizontal letterboxing to keep the aspect ratio constant.

### Menu

* Ruleset qcon now available through menu
* Sound: desired samples available through menu
* "Light Mode" renamed to "Darken Map"
* Bugfix: F2-F12 are now bindable in menu
* Bugfix: When unbinding through menu, only keys that match the command are unbound (rather than all keys starting with the corresponding command)

### Other

* Various documentation corrections and updates.
* Bugfix: Various memory leaks patched
* Bugfix: `/playdemo <longfilename>` could crash client
* Bugfix: console background resizes as console width/height changes.
* Bugfix: ambient sound would not change volume if cl_maxfps was sufficiently high (leads to ambient sounds always playing or never playing)
* Bugfix: on Linux systems, keyboard input will be grabbed as well as mouse when `/in_grab_windowed_mouse` set.  Should stop window manager shortcuts from firing during game.
* Bugfix: `/connectbr` will default to port 27500 if no port specified
* Bugfix: No longer looks for files in root of the current drive if `/userdir` is empty

### Build environment

* Windows: can now access https:// server browser sources (libcurl library updated)
* OSX: binary should now be compatible with OSX 10.9

