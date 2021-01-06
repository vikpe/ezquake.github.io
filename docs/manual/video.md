---
layout: default
tab: Documentation
---

# ezQuake Manual - Video settings
(automatic conversion from internal help - last edited Sat 16-Oct-2004)

## Video settings


This section deals with how you can get more frames per second out of QW and how to improve visibility both in software and in OpenGL mode.

## OpenGL or software?

There are two different versions of QW. The 3D accelerated version called OpenGL QW and the software VGA version often called "lego" QW. Although everyone has a 3D card nowadays there is still a large amount of people playing the software version of QW. Both versions have their advantages and disadvantages. The GL version looks very nice and has a lot more effects and eyecandy options, while software usually looks very ugly but many people claim that it offers better "control" of the game. In the end it depends on your personal preferences which version you use.
## Fullbrights?

Quake was designed as a single player game in the first place and such games live on the atmosphere created in the levels. An easy way to create atmosphere is to have many dark areas and even more atmosphere is created when eyes glow in in thoses dark areas. Thus there are some colors in Quake which are always "fullbright" even in the darkest areas. Now after the introduction of custom skins with QW some clever people made skins that only had these colors. This way they could always see their enemies regardless of how dark the surrounding area is. Nowadays after years of controversy fullbright skins are accepted as a standard in the QW community.
## General video stuff

## Setting the resolution

QW can be run at almost any solution modern graphic boards offer. You can both use the old 320x200 VGA resolution or something like 1800x1400. There are two ways to set the resolution, either through the video modes menu in the options or by using the command line. In glQW the only way to change the resolution is by the command line. The video modes menu tells you which resolutions are possible with your current setup, but you can also bring up the console and type "vid_describemodes". To set the resolution by the command line you have to use the -width and -height parameters (for example: c:\quake\ezquake-gl.exe -width 800).

- **cl_maxfps [x]** The more fps you have in QW the better but there might be some situations where you have to cap your frames per second (for example when you are on a low bandwidth connection, because more fps means also more net traffic). The command to do this is "cl_maxfps" followed by a number. 0 means no limit while 56 would create no more than 56 fps. There is a limit built in in QW at 72 fps (there are ways to circumvent this, several hundred fps are in fact possible in QW). You should always aim to get those 72 fps (to show your fps type_show_fps 1_).

## Checking and testing FPS

The best way to see and test if a certain setting improves your fps or not is to use the "timedemo" command. It will run the specified demo as fast as possible and at the end tell you how much time it needed and how many frames per second were displayed. Since QW itself does not come with demos and many of the commands QW has do not work with NQ (which has demos) you need something else to compare your fps. One of the most common demos is overkill.mvd [(download)](demos/overkill.mvd) To run it just type_timedemo overkill.mvd_after putting it in your QW directory.
## OpenGL settings

OpenGL QW looks considerably better and runs much faster on slow systems than the software version. While it works perfect with voodoo boards (and actually promoted them almost as much Rebel Assault promoted CD-ROM drives) it is often problematic to run on modern 3D graphic cards (GeForce, Radeon etc.). It depends a lot on the drivers wether it will run stable or cause regular lockups of the computer. Another serious issue is that glQW is often very dark and inexperienced users have a hard time in changing that.
## Resolutions

The more FPS the better so you should aim for the maximum 72 FPS in glQW as well. On modern systems these are fairly easy to reach even at high resolutions. The lowest resolution possible shoudl be something like 320x200 or 320x240 depending on whoch card/drivers you have (older Voodoo cards start at 512x384 for example), the upper border is limited by your hardwares' capabilities as well. Note that resolutions can only be changed through the command line. If you are running the GL version in a high resolution the font (for example in teammessages) might get harder to read. You can make it (and the status bar as well) larger by using the conwidth/conheight command line parameters.

Example:_ezquake-gl -width 800 -conwidth 400_

This would start ezQuake GL in 800x600 resolution while the font and status bar will be displayed in a lower resolution of 400x300 (it will also improve overall FPS a bit).

- **gl_polyblend 0|1** Turning this setting to 0 will get you rid of all palette changes when taking ring/quad/penta or when under water. Water will be crystal clear and nothing will change when powered up (in contrast to seeing everything through a fog in blue or red colors). It will also get you rid of the red flash when you are hit. This helps alot because enemies will be much easier to see and it also saves some fps.
- **gl_waterwarp 0|1** This setting will turn of the waterwarp. Helps a lot in underwaterfights and improves fps.
- **gl_flashblend 0|1** Usually there would be an annoying glowing ball around rockets and explosions. By setting the flashblend setting to zero these will be turned off. The drawback however is that the red and blue glow around the pentagram and quaddamage as well as those players bearing them will also be removed. Furthermore the areas where rockets are flying will be lit dynamically which can cause drops in fps.
- **r_dynamic 0|1** This will turn off the dynamic lightning effects that occur when flashblend id turned to 0. Helps your fps alot in large areas and during battles with lots of rockets.
- **gl_subdivide_size 2028** This will change the looks of the skies. Higher settings will make it look worse and will improve fps in large oben areas but the difference is hardly noticable.
- **gl_ztrick 0|1** Another setting that will help your fps without a noticable difference. (actually it turns off the clearing of the z-buffer making the graphic display less precice).
- **gl_triplebuffer 0|1** This will enable triple buffering which can improve fps a fair bit especially on voodoo based cards. It will also stop the toolbar from flickering (if that happens at all).
- **gl_keeptjunctions 0|1** If you don't care much about the graphics you can turn this setting to 0. The drawback is that sometimes you will see some pixels where they do not belong especially in gaps between ammo boxes and the floor or where the water surface ends.
- **gl_texturemode GL_LINEAR_MIPMAP_LINEAR (Best quality)** **gl_texturemode GL_LINEAR_MIPMAP_NEAREST (Medium quality - default)** **gl_texturemode GL_NEAREST (Worst quality)** **gl_texturemode GL_NEAREST_MIPMAP_NEAREST** These are the four different determine how much the textures are smoothed. Lower settings don't help ypur fps much (if at all) but some people dislike the smoothing.

## "Lego" textures in ezQuake GL

ezQuake has inbuilt support for Degeneration textures made by def, which make ezQuake GL look like software Quake with_d_mipcap 3_enabled. If you don't know what this is, then don't worry about it.

The following alias will enable this effect:

```

alias degeneration-2 "gl_lightmode 2;gl_scaleTurbTextures 0;gl_scaleModelTextures 1;gl_texturemode gl_nearest;gl_externalTextures_bmodels 0;gl_externalTextures_world 0;gl_picmip 0;gl_miptexLevel 3;cvar_reset gl_max_size"
```


It's also a good idea to create an alias that switches back to normal texture mode, if you'd get tired of all those lego pixels:

```

alias regeneration-1 "gl_lightmode 0;gl_scaleTurbTextures 0;gl_scaleModelTextures 0;gl_texturemode gl_linear_mipmap_nearest;gl_externalTextures_bmodels 1;gl_externalTextures_world 1;gl_picmip 0;gl_miptexLevel 0;cvar_reset gl_max_size"
```

## Software settings

The software version of QW is often called "lego" QW because most people use settings that lower the resolution of the textures so much that each pixel looks like a software block. Together with the speed of QW compared to the modern shooters I have also heared people calling it Pixel Blizzard which fits it quite well, too.
## Resolution

With software QW it's considerably hard to get the maximum of 72 FPS at higher resolutions. So the one and only video mode you should use is 320x200. This also ensures maximum visibility by reducing the resolution of the textures.

- **d_mipcap [x]** Setting this value to 3 (default is 0) will reduce the detail of the surroundings textures to a minimum. You will see very large pixels which looks very strange in the beginning but you will get used to it very fast. It will both improve your frames per seconds as well as the overall visibility of players and objects.
- **d_mipscale [x]** This command does the same as mipcap but this time to the opjects. The only drawback of this command is that player which are not very customized to the maps yet might have a hard time what kind of item is laying in front of them.
- **d_subdiv16 1** This toggles extreme perspective correction, setting it to 1 improves fps a bit and the difference in the perpective is not very significant.
- **r_drawviewmodel 0|1** This will turn off the display of the weapon you are wielding. Will give you some more fps but you need some time to get used to look at the status bar to see which weapon is selected.
- **r_waterwarp 0|1** This will turn off the warping of the water when swimming benaeth the surface. This not only saves some fps but also makes enemies underwater easier to see.
- **v_contentblend 0|1** Turns off the palette change when underwater and makes it easier to see things.

