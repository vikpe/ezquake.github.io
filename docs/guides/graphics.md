---
layout: default
tab: Documentation
---

## Graphic Options

(this topic was ported quickly from old documentation and needs updated)

##### Fakeshaft

The Lightning Gun fires 10 shots per second with 30 damage points each (300 damage points per second) in QuakeWorld.

In original QuakeWorld the rendered beam position was also updated only 10 times per second, according to where the last damage hit went.

By enabling fakeshaft feature, the shaft beam will not stay on the same position for the whole 100 miliseconds.
If you move your crosshair away from where the last shaft hit went, the shaft will try to come back to your current crosshair position by small steps, made by linear interpolation.
If you use full fakeshaft, shaft beam will always point straight to the crosshair.

That means, by using this feature, you are less distracted by the old shaft beam position and you can concentrate to where you are actually aiming.
However you will kind of lose the visual information of where the last server-side position of your lightning gun beam.

It is a matter of personal preference as to what the 'best' value to use is.  However on anti-lagged servers, the old `/cl_fakeshaft 0` setting may be misleading.

- `/cl_fakeshaft 0`
  - Disable fakeshaft, classic Quake/QW
- `/cl_fakeshaft 0.5`
  - Enable 50% fakeshaft - the beam position will be half-way between last confirmed server position, and your current crosshair position
- `/cl_fakeshaft 1`
  - 100% fakeshaft - the last position from server is ignored, the beam always points at crosshair
- `/cl_fakeshaft 2`
  - Special form of fakeshaft, specifically for antilag server.  The beam will always point at your cursor position 2 frames previous.

To track what fakeshaft options other players are using, type "f_fakeshaft" into game chat.

##### Turning off textures

The client allows a great deal of customisation when rendering the world

- `/r_drawflat 1`
  - Ignore textures from the map and render the world as shades.  Colors are set depending on the normal of the surface - surfaces pointing more vertically than horizontally will be rendered as floors, others as walls.
  - `/r_wallcolor color`, `/r_floorcolor color`
    - Sets the colors to use for walls and floors/ceilings respectively
- `/r_fastsky`, `/r_fastturb`
  - Determines if sky & turb textures (other liquids, such as teleporters) should be rendered flat
  - `/r_telecolor`, `/r_skycolor`, `r_lavacolor`, `/r_slimecolor`
    - Sets the colors of liquids that are being rendered as flat color
- `/r_skyname`
  - Sets the name of a skybox to use instead of sky textures.  See section on [external textures][external-textures] for more info.
- `/gl_textureless 1`
  - Turns off textures, setting the color of each surface to the top-left pixel of corresponding texture
- `/gl_max_size num`
  - Sets the detail level for textures, where num is between 1 (`/gl_textureless`) and 16384 (max detail)

##### New particle system

The following variables use the new visually enhanced particles when set to 1 and use the old system when set to 0. All of them default to 0.

    gl_part_explosions    used for explosions.
    gl_part_trails        used for (rocket etc) trails.
    gl_part_spikes        used for spikes (nailgun etc).
    gl_part_gunshots      used for gunshot (etc) effects.
    gl_part_blood         used for blood effects.
    gl_part_telesplash    used for teleport splashes.
    gl_part_blobs         used for blob explosions (EMP's).
    gl_part_lavasplas     used for lava splashes (Spy Gren).
    gl_part_inferno       used for pyro flames in TF.

The following variables control the behaviour of the new particle effects. They do not effect the old particle effects.

    gl_bounceparticles    whether sparks rebound off walls. Bouncing particles look nicer, but may eat up CPU.
    gl_clipparticles      setting this will limit the number of blended particles close to you (fps benefit)

The particle engine has evolved from the QMB particle engine. QMB was a quakenet (not quakeworld) quake engine developed by DrLabMan. (website no longer available)

FAQ

- Q1. What are Blop Explosions and Lava Splash?
  - A1. These are really only used in teamfortress. Blob explosions are what happens when an EMP grenade explodes (and when a spy grenade first explodes). LavaSplash is the red stuff a spy's gas grenade creates. LavaSplash also happens sometimes in dm when the map ends.
- Q2. I lose a lot of FPS with when using the new QMB effects. WTF?
  - A2. Tough. Good things come at a price.
- Q3. The new effects don't look so good. WTF?
  - A3. Make sure you have ezquake/pak0.pak (should have been installed when you installed the .exe's).
- Q4. What about axe effects ?
  - A4. There's a lot of effects in quakeworld, especially when you consider custom mods like teamfortress. Hence it is impossible to have a variable for every effect. Things which do not have variable (like axe effects) are controlled by the gl_part_gunshots variable.
- Q5. I have set the gl_part_* variables to 1 but I still get the old particles. WTF?
  - A5. Make sure you've installed ezquake/pak0.pak from the zip file/installer you downloaded from the web. Inside that pak file are some particle textures that are important.

[external-textures]: external-textures.md
