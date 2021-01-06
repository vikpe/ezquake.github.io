---
layout: default
tab: Manual
---

## Changes in 3.0

### General

* Major overhaul of backend code - now using SDL2 library for all three platforms.  Linux & OSX versions in particular are now much improved.
* Now use 4:3 `/fov` value and ezQuake will adjust for your resolution
* Added `/ruleset thunderdome`, a less restrictive version of smackdown
  * Advanced particle effects are allowed in-game
  * `/cl_rollalpha` is enabled, allowing `cl_rollangle` to tilt opponents in the direction they are moving, but not the current player
* Added `/ruleset qcon`, a more restrictive version of smackdown for tournament play
  * `/play` & `/playvol` commands are disabled
  * MP3 player is disabled
  * `/gl_outline` is disabled
  * `/gl_brush_polygonoffset` is disabled
  * A hard limit of 10 sequential wait commands
  * Hud images cannot be changed during the game
* Added AFK status on scoreboard (see `/scr_scoreboard_afk` and `/scr_scoreboard_afk_style`)
* Added support for 'new' player model by CapnBub (passes f_modified)
* Added `/gender` to control gender of player in messages.  Requires server support for streak messages to be correct
* Added `/con_fragmessages 2` option to show frag messages in the console, but not in the notification area
* Added `/con_mm2_only` option to hide all messages which are not mm2 (`/say_team`) from the notification area during game
* Added `/lg_color` command & `/gl_custom_lg_color_enabled` to allow lg bolt color to be set without replacing texture
* Added ability for all mm2 codes to have fixed widths and alignments set.  For example `/say_team %<10r>l` will print the player location, but fixed-width 10 characters, aligned right.  Defaults can be set by (e.g.) `/set tp_length_l 10; /set tp_align_l r`
* Added `/tp_tooktimeout` & `/tp_pointtimeout` to customise time before last taken/pointed item is blanked
* Added `/cl_textencoding` to control outgoing formatting of unicode characters.  FTE's ^U encoding now supported
* Added `/hud_score_bar` options to allow player/team names to stay in the same order, regardless of current tracked player
* Bugfix: server browser should be more stable
* Bugfix: scoreboard would not appear in auto-screenshot if console was down at match end
* Bugfix: `/cl_delay_packet` could cause packet loss
* Bugfix: extended uptime led to jerky player prediction
* Bugfix: starting client direct from qw:// url could lead to viewsize, fakeshaft having incorrect settings
* Bugfix: where chat icons & player identifications were shown during intermission
* Bugfix-ish: `/setinfo rsnd 0` causing item pickups to not be detected... not fixed, but should happen less often
* Removed `/vid_wideaspect`

### Input

* Added `/in_raw` to enable raw input (enabled by default).  Replaces `/in_mouse` input selection method.
* Added `/sys_inactivesound 2`, will play sounds when out of focus but not minimised
* Added `/in_release_mouse_modes`, controls when the mouse cursor is released by the application when in windowed mode
* Added `/m_accel_power`, `/m_accel_senscap`, `/m_accel_offset` - mouse acceleration now uses [povohat's method](http://www.quakeworld.nu/forum/topic/6488)
* `/sys_disableWinKeys` now releases its lock on alt-tab, and re-establishes when switching back.
* Now uses operating system keyboard layout by default.  `/in_builtinkeymap 1` switches back to Quake/American default
* Removed `/m_showrate`

### Audio

* Lower latency audio - audio is now mixed in its own thread
* Added `/s_desired_samples` to suggest a buffersize to audio thread
* Added `/s_listdrivers` to print supported sound drivers (SDL information)
* Added `/s_audiodevice` to choose which audio device to use (`/s_audiodevicelist` gives list)
* Removed `/s_mixahead`

### Video settings

* Added `/vid_usedesktopres` to tell client to run at desktop resolution (enabled by default).
* Added `/sys_disable_alt_enter` to block alt-enter toggling fullscreen (disabled by default)
* Added `/vid_conscale` to scale screen resolution by constant if `/vid_conwidth` or `/vid_conheight` are zero
* Added `/vid_displaynumber` to set which display to run on when fullscreen
* Added `/vid_win_displaynumber`, `/vid_win_width`, `/vid_win_height` - windowed equivalents of fullscreen settings
* Added `/vid_win_save_pos`, `/vid_win_save_size` to set cvars when window moved/resized by operating system events
* Added `/vid_24bit_depth` toggles using 24-bit z-buffer (enabled by default)
* Removed `/vid_mode`, `/vid_customwidth`, `/vid_customheight`

### QTV

* Added `/qtv`: `/qtv <server>` will spectate `<server>` via QTV (requires that server is listed on [QTV website](http://qtv.quakeworld.nu))
* Added `/find`: `/find <name>` will return all players matching `<name>` (requires that server is listed on [QTV website](http://qtv.quakeworld.nu))
* Added `/qtv_fixuser` to allows corrupt player userinfo strings from older versions of QTV to be corrected
* When spectating via QTV, `/join` command will connect you to the server
* Bugfix: muzzle flashes no longer appear in incorrect positions
* Bugfix: stop `/cl_demospeed` from causing frozen explosion effects (can re-enable with `/qtv_allow_pause`)

### Demo playback

* New hud element 'static_text'.  Enabled only when spectating, allows custom, multi-line text area on screen
* Added support for playback of .qwd demos from QW 2.1 and up (protocol versions 24/25)
* Added `/cl_demoteamplay` to let you view standard QW `+showteamscores` when watching NQ (.dem) demos.  Players with -99 frags will appear as spectators
* Bugfix: `/demo_jump` - works on .dem files, doesn't break prediction of players in .qwd files
* Bugfix: `/playdemo x.mvd` will not attempt to play x.qwd then x.mvd
* Bugfix: `/demo_capture_max_vid_len` allows splitting of .avi into multiple files, rather than producing corrupt .avi file due to limits of the format
* Bugfix: `/cam_pos` now stops tracking player.
* Bugfix: `/demo_jump` doesn't lose free-floating camera position during a rewind
* Bugfix: .dem playback - player colors, particle trails, textures, third-person cameras and .lit files should work as normal.
* Bugfix: .qwd playback - player prediction enabled, should be much smoother
* Bugfix: scoreboard now obeys `/teamlock` (current player can have enemy color)

### Other

* Console variables can have "auto" values supplied, so the user can see the value being used by the engine rather than just the default values & currently set
* Added `/con_bindphysical` to toggle `/bind <key>` interpretting `<key>` as based on operating system or Quake layout.  Defaults to 1 at start of every configuration file and is reset at end.
* Added `/f_focusgained` trigger
* Added `/batteryinfo` command
* Upper limit of 10 seconds on console notification times.
* When searching for textures, precedence given to individual files over those found in .pak or .pk3 files
* Can associate client directly with URLs in browser (i.e. `ezquake-gl.exe qw://<serverip>`)
* Command and variable documentation is now compiled into the executable
* Single makefile to make all platforms
* Scripts to build using Travis CI and Docker
* Removed: plugin system, software renderer, assembly code, security module, TCL scripting, FTE2 voice chat


