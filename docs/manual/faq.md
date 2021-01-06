---
layout: default
tab: Documentation
---

# ezQuake Manual - Frequently Asked Questions
(automatic conversion from internal help - last edited Tue 07-Oct-2003)

## Frequently Asked Questions

---

## What do I need in order to play QW?

A great place to start is [nQuake](http://www.nquake.com/) . This is a pack that contains everything you need in order to play (ezQuake client, configs, maps, textures, tools, scripts, Frogbots, documentation and more). Put together to supply beginners as well as veterans with an easy-to-use QuakeWorld installation.
## I need a good cfg, and what commands should I know?

Go to the [configs section](configs.md) to find an easy-to-use cfg. To see a list of important commands, [go here](important_commands.md) .
## Where can I find servers?

The best way to find servers is with a server browser. Hit Escape, choose Multiplayer, and then Server Browser.

If you're a lazy bastard or you're seeking specific servers, you can view a good online browser [here](http://www.quakeservers.net/quakeworld/) .
## How do I bunnyhop?

Bunnyhopping is rather easy if you know how to do it. Unfortunately it is not nearly as easy to explain it but I will try my best.

The first skill to master is strafe jumping. Strafe jumping is very easy (and people coming form Quake3 will know how to do it). Just hold one of the strafe buttons pressed while jumping and use your mouse to keep jumping forward. In QW you gain a lot of speed by strafe jumping (actually you strafe faster than running forward, thats the reason). Now to bunnyhop you have to start with a strafe jump. After taking off you have to release the forward button. Keep the strafe button pressed. If you now jump again before you land on the ground you will not only keep on jumping forward again but also keep your speed. Doing that is rather easy the tricky part is to gain speed while doing it. In order to gain speed you have to move the mouse a bit into the same direction into which you strafe. If you move too far your jumps will go off so be careful. Try changing the strafe keys in between each jump. It will be easier to keep your intended direction (and its not very usefull to jump around in a circle really). You can gain even more speed after a rocket jump ar by jumping down a slope.

If you use ezQuake you can check the speed at which you are at. Type_show_speed 1_(0 to remove it again). Default maximum running speed is 320, with a strafe jump you can reach over 400, with bunnyhopping you can easily reach 700-800. Values over 1000 are possible but you need lots of space only a few maps offer.

For a much wider guide to QW's jumping techniques, read Cinclant's excellent [guide to bunny hopping](help/jumping.xml) .

---

## How do I change resolution in OpenGL?

Using the command line. Create a shortcut/bat-file with the following command line parameters:_[client] -width [x] -height [x] -bpp [x]_.

Example:

```

ezquake-gl.exe -width 800 -height 600 -bpp 32
```

## Where can I get fullbright skins and how to use them?

Grab them [here](http://gfx.quakeworld.nu/browse/skins/) and extract to qw\skins. Make sure that_noskins 2_is enabled.

Set_teamskin [skin]_and_enemyskin [skin]_. You can also set individual skins for players who have quad/pent, but it's not really necessary (look in the cfg for more info on that).

Most people use a white fullbright skin for enemies and a red one for teammates, this because white is a bit easier to distinguish.
## How do I disable powerup blends?

In software mode use_v_quadcshift 0_to disable quad screen blending and simarly for_v_pentcshift_,_v_ringcshift_and_v_suitcshift_._v_contentblend 0_will disable screen blending when underwater (or slime etc). Note that these variables are more than just 0/1 variables. For example_v_quadcshift 0.3_will still use quad screen blending, but only by 30% as much as_v_quadcshift 1_.
## How do I get low detailed textures?

- **OpenGL mode:** Try experimenting with_gl_picmip [1-6]_(the higher value, the lesser detail). If you use ezQuake GL you might also be interested in the custom made [Simple Quake Textures](http://www.drugs-bunny.tk/) .
- **Software mode:** Use_r_max_size_1 1_to enable "simple textures", similiar to the_gl_picmip_command for OpenGL. Most software users though, play with so called "lego" textures. Just set_d_mipcap 3_to enable this. You can also get this effect in ezQuake GL (see below).

## How do I make ezQuake GL look like software in "lego" mode?

ezQuake has inbuilt support for so called Degeneration textures, which make ezQuake GL look like software Quake with_d_mipcap 3_enabled. If you don't know what this is, then don't worry about it.

The following alias will enable this effect:

```

alias degeneration-2 "gl_lightmode 2;gl_scaleTurbTextures 0;gl_scaleModelTextures 1;gl_texturemode gl_nearest;gl_externalTextures_bmodels 0;gl_externalTextures_world 0;gl_picmip 0;gl_miptexLevel 3;cvar_reset gl_max_size"
```


It's also a good idea to create an alias that switches back to normal texture mode, if you'd get tired of all those lego pixels:

```

alias regeneration-1 "gl_lightmode 0;gl_scaleTurbTextures 0;gl_scaleModelTextures 0;gl_texturemode gl_linear_mipmap_nearest;gl_externalTextures_bmodels 1;gl_externalTextures_world 1;gl_picmip 0;gl_miptexLevel 0;cvar_reset gl_max_size"
```

## How do I disable the 24bit textures in ezQuake GL?

Put_-no24bit_in the command line.
## How do I enable/disable the coloured lightning in ezQuake GL?

With_gl_loadlitfiles 0|1_.
## How do I enable the particle effects in ezQuake GL?

Set all_gl_part_*_commands to 1. Be sure to check out_gl_particle_*_for enhanced and flexible effects.
## How do I make my weapon model transparent in ezQuake GL?

Change_r_drawviewmodel_to a value between 1 and 0. Example:_r_drawviewmodel 0.5_.

---

## How do I turn off mouse acceleration in Windows XP?

Download [this fix](http://koti.mbnet.fi/lamuh/files/xpmousefix.zip) ( [an Australian mirror](http://porter99.customer.netspace.net.au/xpmousefix.zip) ) and reboot. You can also try using_-noforcemparms__-noforcemaccel__-noforcespd_on your cmdline, or_-dinput_(has sideaffects; use ezStart to configure your command line).
## My mouse keeps locking up and not moving every now and then. What should I do?

Put_sys_yieldcpu 1_and_sys_highpriority 1_in your config.
## My (Logitech) mouse is still behaving a bit shitty, laggy and the buttons don't work too reliably.

Assign the mousedriver em_exec.exe realtime priority in taskmanager. You can get it to autostart in realtime priority by doing the following:

```

Start > Run > msconfig > Startup > Untick "Logi_mwx.exe"
```


Now make a batch file (text file with .bat extension) in your windows startup folder with the following:

```

start /realtime path\to\em_exec.exe (I.e. something like:) start /realtime c:\progra~1\logitech\mousew~1\system\em_exec.exe
```

## How do I get my mousewheel to work in ezQuake?

You bind things to_MWHEELUP_and_MWHEELDOWN_to use the mousewheel. In Win32 clients, if you're mousewheel isn't working even with the_-dinput_command line parameter enabled, then_m_forcewheel 1_should fix it.

You can get the mouse wheel working in Linux X11 and GLX clients too. Read linux.txt (in ezQuake\docs) for more info on this.

---

## The screen turns black or the desktop colors are fuhed up after I quit in software mode

Try adding_-dinput_to the command line.
## I get "Couldn't find glide2x.dll" or "Could not initialize GL" when I launch QW

Remove opengl32.dll from your Quake directory.
## I get "W_LoadWadFile: Couldn't load gfx.wad" when I launch QW

This error often occurs when the main pak0.pak (17.8 MB) is not available to Quake. Check that it exists and that nothing else is using it, and try again.

Note: If this occurs when you're playing a mod that has its own engine, try running it with_-game [moddir]_on the commandline, because it might not default to its own directory.
## I get "UDP_OpenSocket: bind: Unknown error" when I launch QW

You're probably running an old version of [Steam](http://www.steampowered.com/) on your computer which uses/blocks the default QW port. Update your Steam client or close it temporary.
## I'm only getting ~60 fps in ezQuake GL even though I have all low quality settings enabled

Make sure that Vertical Sync is disabled (_vid_vsync 0_).

---

## Where can I find QW demos?

 [Challenge-TV](http://www.challenge-tv.com/index.php?mode=demos&game=2) is the #1 source for QW demos out there, you name it they got it! Many of the big leagues/tournaments also host demos on their sites ( [NQR](http://www.nqr.nu/) and [QH-LAN](http://demo.qhlan.org/) for example).
## How can I watch QW demos?

QW demos come in three formats:

- **DEM - Quake Demo** This is the original uncompressed Quake demo format. It is not supported in ezQuake yet.
- **DZ - Quake Compressed Demo** This is the original compressed Quake demo format. It is not supported in ezQuake yet.
- **QWD - QuakeWorld Demo** This is the original uncompressed QW demo format. Can be played with any QW client, either via the console (_playdemo [demoname.qwd]_), or if you run some newer client via the menu ('Multiplayer -> Demos' in ezQuake).
- **QWZ - QuakeWorld Compressed Demo** These are standard .qwd demos compressed with [Qizmo](http://www.udpsoft.com/qizmo/) to reduce filesize. You will need to have Qizmo installed and_qizmo_dir_set to where Qizmo is located, e.g._qizmo_dir qizmo_if it's in '../qizmo'. You can find more info on how to setup and connect to a local Qizmo [here](help/qizmo.xml) .
- **MVD - Multi View Demo** These are multiview demos recorded by the server. This is the best and most commonly used format for QW demos. Just go to the menu and select the demo ('Multiplayer -> Demos' in ezQuake) or type_playdemo [demoname]_in the console. Standard QWD/QWZ demos can also be compressed to this format, but the single POV will remain.


Demos should be put in the ../qw/ directory.
## How do I download a demo from the QW server?

Type_cmd dl ._at the console to download the latest demo recorded (or_cmd dl .._to get the second latest demo). If you want to see a list of all demos on the server you can type_cmd dlist_, and then_cmd dl [number]_to get your demo . If you feel that the downloading is going too slow you can try increasing your rate, e.g._rate 10000_and_setinfo drate 99999999_. Note that only servers that run the [Multiview Demo Server (mvdsv)](http://mvdsv.sourceforge.net) will be able to record demos.
## How do I convert/compress a demo to another format?

Download [these demotools](http://quakeworld.ru/file.:)?id=276) and extract it somewhere in your Quake directory (e.g. ..\tools\demotools\). Then just place the demo(s) you want to convert in the same directory and run the batch file matching your needs.

Possible conversions:

```

QWD to MVD (Run:_qwdtools.exe [demo]_) QWD to QWZ (Run:_qizmo.exe -C [demo]_) QWZ to QWD (Run:_qizmo.exe -D [demo]_)
```


---

## How do I disable ambient sounds in QW?

_cl_staticSounds 0_and_s_ambientlevel 0_to disable ambient/static sounds.
## How do I observe games through a public Qizmo?

A [picture](http://equake.quakeworld.nu/qizmo.jpg) best explains

For further information on Qizmo, go the the [Qizmo section](qizmo.md) or read below.
## What is Qizmo and how to use it?

Qizmo is a so-called proxy that can change the packets sent between the client and the server. Its main features are compression of the traffic, teamplay enhancements and cheat checks. It has lots of other useful features like a server browser, fun name convertion and FPS-improving settings. Qizmo is shareware and can be downloaded [here](http://www.udpsoft.com/qizmo/) . The shareware version can be used for an unlimited time and has almost no restrictions. When you register it you get an even better compression and you will be able to play demos compressed with zip.

The best way to start Qizmo is to create a shortcut or batchfile (.bat) with this string:_qizmo c:\quake\ezQuake-gl.exe_. This way you will start up Qizmo and QW at the same time and QW will connect to the Qizmo. This way it will also be possible to check your clients for certain cheats, like hacked models. The next thing to do is to type_.menu bindstd_in the console. This will bind menu keys to your arrowkeys, enter, backspace, insert, home, pageup, pagedown, end, delete and pause. If you don't like it, change the configuration in the menu.cfg file. Browse the menu and change everything you like. After that go to config and save everything. The next time you connect to that Qizmo with the same name all your settings will be restored.

For much more information about using Qizmo, go to the [Qizmo section.](qizmo.md) 
## What about all these f_ queries?

The_f__queries enable you to check some things out about the other players on the same server. Most of them derives from various proxies like [Qizmo](qizmo.md) . These queries/commands are important for playing in online competitions because they are the only way to check clients for cheats like hacked client/models/sounds, speed cheat etc. (although they will never provide 100% protection from cheats, they still make cheating much harder).

The most important commands are_f_modified_,_f_version_,_f_speed_, and_f_server_. Go to the Qizmo section to see an explanation of each command.
## Where can I get custom maps?

 [maps.quakeworld.nu](http://maps.quakeworld.nu/) has an archive with all the maps you'll ever need, including screenshots, textures, lit-files etc.
## Where can I get .loc files for maps?

Get flintheart's [loc collection](http://maps.quakeworld.nu/locs/) . It contains customizable .loc files for all id maps as well as the most popular custom maps. Make sure to read the instructions!
## Where can I find nice QW movies?

There are a bunch of great QW movies out there. The most popular ones are probably [Frags Done Extreme 1 and 2](http://fde.qhlan.org/) , [Dag Def Extreme 1 and 2](http://www.planetquake.com/dde/) , [TeamFortress Done Extreme 1 and 2](http://tfde.quakeworld.nu/) , [QuakeWorld Reloaded](http://gamefiles.blueyonder.co.uk/blueyondergames/trailers/movies/quakeworld/qwre-hq.zip) , [Brazilian Extreme Frags](http://gamefiles.blueyonder.co.uk/blueyondergames/trailers/movies/quakeworld/bef-hi.zip) and [Frags Done Satanic 2: Refragged](http://gamefiles.blueyonder.co.uk/blueyondergames/trailers/movies/quakeworld/fdsr-hq.avi) . Then there are a bunch of other pretty good movies as well. You can find all QW movies ever released over at [blueyonder](http://gamefiles.blueyonder.co.uk/blueyondergames/trailers/movies/quakeworld/) .
## I am still confused and need more help/information

Just ask us. You can find lots of experienced QW players on IRC. Try #ezQuake or #QuakeWorld on [QuakeNet](http://www.quakenet.org/) or #QWPlayers on the ETG network.

Also check out [this section](external_resources.html) for some useful links to more websites/IRC channels offering help about QW.
