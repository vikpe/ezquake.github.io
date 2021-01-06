---
layout: default
tab: Manual
---

## Changes in 3.1

### Main features from 3.0.1
- Internal server updated to mvdsv 0.32 (can run KTX again)
- Support for large map formats (BSP29a and BSP2) added
- Client-crash during `/vid_restart` fixed
- URL server browser sources fixed in OSX
- FTE's VOIP support re-introduced.  Must have SDL 2.0.5 or higher for microphone support
- Support for MVDSV protocol extension, improved coord accuracy for players & entity locations only (smoother gameplay on high ping)
- Support for MVDSV protocol extension to help with movement through teleports on high ping (`/cl_pext_lagteleport 1` to enable)

### Demo playback
- Various bugs fixed with `/cl_multiview`, particularly when using `/cl_mvinset 1`
- Matchless .mvd files should now play back correctly
- Trying to spectate a ghost/invalid-player now moves on to the next player, rather than 'sticking' on the current
- `/mvd_autotrack_team` no longer sometimes switches back to generic autotrack selection
- Item timer wasn't spawned for 2nd mega when player holds 2 megas and health falls under 100h
- Item timer not spawned if player with mega fell under 100h but immediately picked up standard health
- Item timer not spawned if player picked up armor after previously dying with armor left over
- Item timers/game-clock could be incorrect on long server uptimes or long QTV connections
- Connecting to a game in progress broadcast by QTV 1.11 should immediately set correct gametime
- Connecting to server with protocol extensions doesn't break subsequent .dem playback
- Added `$demoname` and `$demolength` (expected length of demo in seconds) macros to help with demo capture
- `/cl_demospeed` now ignored during timedemo (some logic would think the game was paused)
- `/demo_capture` in image mode will now also produce a .wav file of the corresponding audio
- `/demo_capture_background_threads` allows background writing of screenshots
- Can now playback demo files from within .zip files on linux systems
- Client disconnections in .qwd with no explanation (client kicked in KTPRO?) doesn't end playback
- `/demo_jump_mark` now detects marked points by any player/spec, not just the one currently tracked
- `/demo_jump_rewind` added, when demo mark detected the client will play this many seconds prior to the mark being inserted

### HUD
- New Hud changes
  - all hud elements should now support the 'scale' property
  - `frags` hud element has extra fliptext options, and can display fighting-game-style power bars
  - `groups` no longer spam error messages when specified image can't be loaded
  - `score_enemy`, `score_team` HUD elements now respect `/teamlock` setting
  - `weaponstats` hud element added, same functionality as `/scr_weaponstats`
  - `itemsclock` hud element has option to display simple item icon instead of 'RA' etc
  - `itemsclock` can have item types filtered out (remove GA, for instance)
  - `gamesummary` hud element added, flashing/counting total item pickups over match
  - `keys` hud element can target other players when playing back .qwd file
  - `keys` hud element now works with recent server-side race demos
  - `score_team`/`score_enemy` should match `+showteamscores` when Team Fortress team scoring detected
  - Radar can use simpleitems for icons, show arc of fov, highlighting name fixed
- Old Hud changes
  - `/scr_sbar_lowammo` option added, to control low ammo warning when using oldhud
  - New 'compact' mode added (`/scr_compactHud 4`)
- Improved menu scaling on high resolutions

### Renderer
- dynamic lighting performance improved (ported from fodquake)
- Can specify color of projectiles/shaft without creating custom textures (`/gl_custom_*_color`, `/gl_custom_*_fullbright`)
- `/r_shaftalpha` now works when custom lg color set
- `/r_rocketlightcolor` can now have an alpha element specified to control the strength of the effect
- `/cl_gibfilter` will now filter gibbed heads even before the player respawns
- `/gl_outline 2` option for visualising geometry (cheats-enabled only, for map developers)
- `/crosshairscale` allows larger built-in crosshairs to be built (rather than just making small images bigger)
- `/crosshairscalemode` controls crosshair coordinates/sizes for pixel-to-pixel accuracy.
- `/r_skincolormodedead` added, `/r_skincolormode` for corpses (-1 to use same)
- `/r_lerpframes` caused all statics to use frame 0 of the model file (aka: large torches renderered as small on start.bsp)
- `/r_lightdecayrate` controls how fast dynamic lights decay (1 = Quake default, 2 = ezQuake standard)
- Support for translucent players in KTX's multi-race mode
- Support for alpha-tested textures in standard Quake maps, not just halflife BSPs

### Networking/server-browser
- Support for MVDSV protocol extension, improved coord accuracy for players & entity locations only
- Support for MVDSV protocol extension to help with movement through teleports on high ping (`cl_pext_lagteleport` to enable)
- Added `/cl_delay_packet_deviation` to create random variation in ping
- Fix issues with `/cl_delay_packet` (packet loss and jerky movement) when using the internal server
- Server browser no longer corrupts sources.txt when saving
- Server browser will now display searchstring when no servers match filter
- Server browser no longer requires write access to folder when using URL sources
- URL sources working in OSX again

### Input
- `/weapon 10` and `/weapon 12` implement client-side weapon cycling
- `/m_accel` values less than zero now ignored
- `/vid_grab_keyboard` stops window manager keybinds from interfering with the client (or vice versa)
- `/vid_minimise_on_focus_loss` allows out of focus window to run fullscreen
- Caps-lock keyboard status doesn't toggle when using it as a bindable key (Windows only)

### Sound
- Rulesets that block message triggers now also block sound triggers
- Custom chat-sound selection is now only valid when spectating or watching demos
- `/s_chat_custom 0` now disables chat noises again
- `/s_show 2` now functions in non-debug builds, if map is in standby

### System
- Gamma: support ramp sizes other than 256
- Mod trying to open directory on linux now fails correctly
- Desktop resolution scaling now handled correctly on Windows
- `/vid_gamma_workaround` - runtime toggle of workaround to set hardware gamma on Linux
- `/gl_gamma 0` is not treated as `/gl_gamma 1` on startup
- `/cfg_load` now respects `/con_bindphysical` setting
- Heapsize defaults to using 128MB rather than 32MB (some newer TF maps require this)
- Standard connection qw:// URLs now set `/spectator 0`

### Other/misc
- Single player games saved on non-normal difficulty should load correctly even if `<gamedir>/server.cfg` set `skill`
- Menu: left/right now changes values, rather than changing tab
- `/tp_msg...` commands can be used in teamplay macros
- `/fov` set by the user updates `/default_fov`
- 'flashed' state (blocking tp_msgpoint from working) wouldn't clear unless using MTFL ruleset (Team Fortress)
- `/dir` command can take parameters to change output format (hide extensions/folders/filesize) - requested for nquake
- `/alias` without arguments displays the contents of the alias
- `/con_timestamps 2` is restricted for players during the game
- `/scr_scoreboard_drawfps` removed
- `/ruleset qcon` (or any future ruleset that restricts sounds from server) now also restricts ktsound events

### Internal
- All thread-handling now uses SDL thread functions
- Recursive legacy commands are blocked correctly
- Fix crash when particle time set to 0
- Fix crash when MSAA not supported
- Fixed out-by-one bug on demo playlist
- Buffer overflow bug in server browser fixed
- Buffer overflow bug in regular expression handling fixed
- Buffer overflow bug when checking if filename is valid

### Build system
- Meson build system added
- Build no longer relies on xxd utility
- Simple linux build script (`build-linux.sh`)
