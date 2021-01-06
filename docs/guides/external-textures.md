---
layout: default
tab: Documentation
---

## External Textures

###### (this topic was ported quickly from old documentation and needs updated)

### 24-bit Textures

This client supports textures replacement. You can replace textures of old maps with some new pictures. Just download a texture pack and extract it to your ./qw/textures path.

We recommend [Quake Revitalization Project][qrp] and QuakeWorld GFX at [quakeworld.nu][gfxqwnu].

You can place all the textures in the root directory of the textures dir (see above) or you can create sub-dirs for each map there. E.g. ./qw/textures/dm4/ contains textures to be used only in map The Bad Place.

### Console background

You can replace the picture that is used as an console background. This file must be named conback.png and placed into ./qw/gfx directory. You can download some console backgrounds from [here][conback].

### Console font

Console font, called charset, is a picture of special format that goes into ./charsets directory. You can download fonts [here][charsets].

Once place there, use `/loadcharset` command with the name of the file with your desired console font.

In order to avoid visual artifacts, it is important to use a console font that matches your console resolution - more details [here][console-font-formats]

### Crosshairs

You can switch between some inbuilt crosshairs using the crosshair command giving it an integer number as a parameter. E.g. crosshair 4 gives you simple square.

You can also create a crosshair for yourself in 24-bit colors with alpha-transparency! Save your image as a 24-bit PNG picture with alpha-transparency channel and place it into <quakedir>/qw/crosshairs directory.
Presume, you've created file 'mycross.png'. Then type in the console crosshairimage mycross and your crosshair will appear on the screen.

You can download crosshairs from [here][crosshairs].

Other commands for manipulation with crosshairs: `/crosshairsize`, `/crosshairalpha`, `/crosshaircolor`

### Skyboxes

You can also replace textures used as the sky. Textures used as a replacement must have a special naming convetion: each file name consist of these parts: [basename][part][extension], where

- basename
  - is the name that you will use within loadsky command when want to load the sky replacement
- part
  - is one of 'bk', 'dn', 'lf', 'ft', 'rt' and 'up', and
- extension
  - is usually .png or .tga

Those files goes to your ./qw/env directory

E.g: You want to use skybox called 'Day'. Then you have to have files daybk.tga, daydn.tga, dayft.tga, daylf.tga, dayrt.tga and dayup.tga in your skyboxes directory. Then you just type `/loadsky day` into the console.

You can also use `/skygroup` command to define rules to use different sky textures in different maps.

### Skins

You can use custom player skins. Create an pcx image and place it into your ./qw/skins directory.

E.g.: You have abc.pcx, use teamskin abc command to use that image as a player skin for your teammates. Other commands are `/enemyskin`, `/teamquadskin`, `/teampentskin`, `/teambothskin`, `/enemyquadskin`, `/enemypentskin`, `/enemybothskin`.

You can download skins [here][skins].

### Head up display images

You can alter you gfx.wad using AdQuedit tool or you can use some hi-res 24-bit pictures instead. Those files go into your ./qw/textures/wad directory.

You can download HUD graphics [here][hud].

[gfxqwnu]: http://gfx.quakeworld.nu/
[conback]: http://gfx.quakeworld.nu/browse/conbacks/
[charsets]: http://gfx.quakeworld.nu/browse/charsets/
[crosshairs]: http://gfx.quakeworld.nu/browse/crosshairs/
[skins]: http://gfx.quakeworld.nu/browse/skins/
[hud]: http://gfx.quakeworld.nu/browse/hud/
[qrp]: http://qrp.quakeone.com/
[console-font-formats]: fonts.md
