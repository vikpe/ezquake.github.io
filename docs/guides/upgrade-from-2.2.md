---
layout: default
tab: Documentation
---

## Upgrading from 2.2 to 3.0

### Video settings

3.0 now runs at the desktop resolution by default - you can toggle this behaviour with `/vid_usedesktopres`

Aspect ratios no longer need to be explicitly set.  Set `/vid_conwidth` and `/vid_conheight` to 0 and your current resolution will be scaled by `/vid_conscale` instead.

ezQuake 2 required different `/fov` settings for [different monitors/resolutions](http://wiki.quakeworld.nu/Widescreen_Guide). ezQuake 3 does not, use the same fov value no matter what resolution/monitor, it will look the same, it also supports 16:9 properly.  See below for a longer description of fov changes.

Windowed-mode console variables are now in `/vid_win_width`, `/vid_win_height`, `/vid_win_displaynumber`, to stop them independent of fullscreen settings.

### Input settings

`/in_mouse` has been removed, replaced with a simple switch, `/in_raw`.  Windows users using `/in_mouse 2/3` in ezQuake 2, nothing should need to be done.

If you are used to `/in_mouse 1` on Windows, then set `/in_raw 0`, although we recommend keeping it on for the best input handling.

### Keyboard mapping

3.0 uses the same keyboard mapping as your operating system.  `/in_builtinkeymap 1` will return standard behaviour (Quake/US keyboard layout)

If writing a config file where the key is important rather than the physical button ('r' to toggle radar, for instance), then set `/con_bindphysical 0` at the top of the file.

## General Issues

### Audio crackling

ezQuake tries to give you the lowest latency sound possible.  This is achieved by provided smaller blocks of data at a higher rate.  If your system can't keep up with the demand for audio, you might hear crackling or popping noises.  There are a couple of settings you can change to find the right settings for your system.

- `/s_desiredsamples` - this suggests an amount of data the sound card is sent with each request.  The larger the buffer the less chance there is of hearing crackling/popping noises, but also the higher the latency before a new sound will start.
- `/s_khz` - if you don't want an increase in latency, you can try lowering the quality of the sound instead.  The lower the sound quality, the lower the value of `/s_desiredsamples` can be.

> If you are familiar with older versions of the client, `/s_desiredsamples` is roughly equivalent to `s_mixahead`, which has been removed.

### Config files

Quake has used configuration files for twenty years now, and over time the rules have become somewhat complex.  `/exec config.cfg` may not do what you expect.

ezQuake will look for configuration files in the following directories:

- The game directory
- User profile directory (typically Documents/ezquake/ in Windows, or ~/.ezquake/ in Linux)
- qw folder
- ezquake folder
- id1 folder

> If the game directory is already added (because it is "qw" or "id1" for example) then first test (for the game directory) is skipped

The `/path` command will list all the files & folders being searched, in order.  To see where a particular file is being loaded from, use the `/locate` command.

> If you are working with a setup that puts default configs and media in the qw folder (such as nQuake) we recommend enabling the option "Save to Profile Dir" (either through the Config menu, or with `/cfg_use_home 1`).  Otherwise the pak files in qw/ directory will override configs saved in ezquake/, and you may encounter confusing behaviour.

### File search order

Within each of these folders, packaged files are searched in order: .wad, .pk4, .pk3, then .pak.  All files named pakX are added, where X is increasing in number starting from 0.  Then ezQuake looks for a pak.lst file.  If it finds one, all listed files are added, otherwise ezQuake will add all valid files in the folder.  (This means an empty pak.lst file will cause no custom pak files to be added).

When processing the pak.lst file, any pak/pk3 files starting "soft" will be ignored.  Files starting "soft" were intended to be loaded when using the software renderer only.  ezQuake is OpenGL only now, but still keeps this rule.

> If you have multiple .pk3 paks with conflicting files, use a pak.lst file to specify the order.  They should be listed in ascending priority (i.e. the last entry will be search first)

### Saved configuration files

ezQuake has the option of making config files much smaller, with the `/cfg_save_unchanged` option.  When set to 0, the current value is checked against the *ezQuake* default.  If it matches, the value is not written out to the file, as it is the default anyway.  This works well, if no other package has modified the default already - the value may have already changed from the ezQuake default, so ezQuake won't include it in your config file, and you won't be able to use the config file to restore the system back to its desired state.

> If you are working with a setup that executes other configurations before yours (such as nQuake), consider setting `/cfg_save_unchanged 1`.

### Fov doesn't look the same as ezQuake 2.2

This is on purpose (and correct) - ezQuake 2.2 did not handle all monitor resolutions correctly and crucially, `/vid_wideaspect` always assumed the aspect ratio was 16:10, even on a 16:9 monitor.

The way older clients interpretted the `/fov` variable was to set the horizontal-fov, then calculate the vertical-fov based on a 4:3 ratio.  This means that as the resolution becomes 'wider', the `/fov` value needed to be increased accordingly.  2.2 added the `/vid_wideaspect` cvar to do this automatically, adjusting `/fov` and `/vid_conheight` values from a 4:3 ratio to the 16:10 equivalents.

ezQuake 3.0 lets you always specify `/fov` in 4:3 format, and it calculates the equivalent height-fov for a 4:3 screen.  It then looks at your current aspect ratio (`/vid_conwidth` & `/vid_conheight` are taken into account) and calculates the appropriate horizontal

If upgrading from 2.2, you will need to change `/fov` to its 4:3 equivalent.  If you were using `/vid_wideaspect` in 2.2, setting `/fov` would give you a series of messages like this:

    ]/fov 120
    ]/vid_conwidth 640
    ]/vid_conheight 480
    ]/vid_wideaspect 1
    vid_wideaspect enabled - fov recalculated to 128.613235
    vid_wideaspect enabled - conheight recalculated to 400

ezQuake 2.2 would over-ride what you manually set the values to, and replace them with 16:10 equivalents.  If you then saved your config through ezQuake, it would write out these values.  ezQuake 3.0 will be interpretting this `/fov` as a 4:3 value, and probably not giving you the view you want.  To work your way back to a 4:3 fov, use the `/calc_fov` command in 3.0, which will tell you the equivalent 4:3 `/fov` value to use.  If you are on 16:10 resolution, you should now be seeing what you saw before.  If on a 16:9 resolution, it might still look a little different, but this is because 3.0 is showing you the correct aspect ratio, and not forcing 16:10.

#### Did that, fov still doesn't look the same as 2.2

It's possible you may have to run `/calc_fov` twice, that is to feed the value it gives you not into `/fov`, but back into `/calc_fov` once more.  If saving your config in ezQuake 2.2 with `/vid_wideaspect` enabled, it would save this setting before saving the 16:10 `fov/con_height` values.  When executing the configuration then, it would interpret these 16:10 values as 4:3 and effectively run the process twice.  For example, if we continue from the above example:

    ]/cfg_save ezquake2
    Saving configuration to C:\Users\...\ezquake2.cfg
    ]/vid_wideaspect 0
    ]/exec ezquake2
    Execing C:\Users\...\ezquake2.cfg
    vid_wideaspect enabled - fov recalculated to 128.613235
    vid_wideaspect enabled - conheight recalculated to 333
    vid_wideaspect enabled - fov recalculated to 136.304581

So to get back to a 4:3 fov for 3.0, we need to run:

    ]/calc_fov 136.304581
    Use fov 129 (128.613235)
    ]/calc_fov 128.613235
    Use fov 120 (120.000000)

If you have been used to playing this way for many years, going back to the correct aspect ratio might take a bit of getting used to.

#### Viewsize affects fov

In 3.0, reducing the viewsize could lead to horizontal-fov getting larger as the aspect ratio increased.  This was a bug, fixed in v3.0.1

### Key binds

In 2.2, `/cl_keypad` could be set to 0, which meant all keypad buttons were remapped to standard buttons.  This has been removed, so affected configurations need to be changed:

    ]/bind kp_enter X       // instead of bind enter X
    ]/bind kp_minus X       // instead of bind - X

etc.  The names to use when binding to the keypad buttons are:

    Num Lock: kp_numlck or kp_numlock
    /       : kp_slash, kp_divide
    *       : kp_star, kp_multiply
    -       : kp_minus
    +       : kp_plus
    home/7  : kp_home, kp_7
    up/8    : kp_uparrow, kp_8
    pgup/9  : kp_pgup, kp_9
    left/4  : kp_leftarrow, kp_4
    5       : kp_5
    right/6 : kp_rightarrow, kp_6
    end/1   : kp_end, kp_1
    down/2  : kp_downarrow, kp_2
    pgdwn/3 : kp_pgdn, kp_3
    ins/0   : kp_ins, kp_0
    del/.   : kp_del
    enter   : kp_enter

`/cl_keypad` has been reinstated as of v3.0.1

