---
layout: default
tab: Documentation
---

## Player Skins

###### (this topic was ported quickly from old documentation and needs updated.  In particular, check how skin-forcing in 4v4 works with ktx & current competitive rulesets)

Textures used on the players in the game are called skins. This page explains how skins are handled in our client.

Each player has own "skin" setting represented by the variable in every QuakeWorld client. Also each player has own set of textures stored in Quake/qw/skins directory (usually pcx or png format). From this directory the client reads the textures that it will apply on players according to skin rules.
Our client uses very wide range of skin rules and this page should explain how the skin for each player is chosen.
General settings and commands

- `/showskins`
  - Lists skins assigned to each player
- `/skins`
  - Free the skins cache, load or download them again
- `/baseskin`
  - Skin that will be used on the player if no rules are found
- `/skin`
  - The name of your own skin
- `/noskins`
  - Allows you to turn off skins rules completely or when set to 2, disallow downloading of skins from the server
- `/allskins`
  - Sets one skin to all the players
- `/cl_name_as_skin`
  - Use player's name or player's id number to load the skin.
- `/gl_nocolors`
  - Allows to set same 24-bit texture on all players, regardless of color choice

##### Basic Skin Forcing

The client allows you to force one universal skin to be used for all your teammates or one universal skin to be used for all the enemies. You do that with teamskin and enemyskin variables.

You can also distinguish players that carry Quad or Pent powerup. For this, use enemyquadskin, enemypentskin, teamquadskin and teampentskin. Also special case is a player that carries both powerups at the same time. For that case use enemybothskin and teambothskin settings.

All these settings can be also found in the Options menu at the Player tab.

##### Color forcing

You can also use variables r_enemyskincolor r_teamskincolor r_skincolormode teamcolor and enemycolor to force colors on your team/enemy players.
Special Skin Forcing

There were two important moments in QuakeWorld history that changed how skins were used.

In the beginning those players who used empty "skin" setting couldn't be recognized by their skin from other players and those who used their own skin name could be recognized by all other players on the server (if they had the appropriate texture installed in their client).

The Qizmo proxy however introduced a special feature that allows you to artificially set different colors (not skins, but the effect is the same) on each player. However for very long time (until the year 2006) players weren't much aware of this feature.

When basic skin forcing feature (see above) came, most players used it and had one skin for all teammates and one skin for all enemies.

But it shows that for teamplay games clans prefer to use special name of skin for each player and turning off basic skin forcing for teammates, making it possible for your teammates to recognize you. However this will make you recognizable also for the enemies - if they have proper skin textures installed in their Quake directory.

The issue of "being recognizable also for the enemies" is still undecided rule in QuakeWorld. Some players suggest disabling this possibility, some use the Qizmo feature to distinguish enemy players, some players put skin textures to their skins directory so that they distinguish enemy players too.

##### Teammates skin forcing

As stated above, using different skin for different players in your team has become a habit in QuakeWorld.

This client offers you a feature to *set different skin for each teammate even if they do not have different skin names set*. To do that, use `/teamforceskins` variable (follow the link for more info).

##### Enemies skin forcing

Because using different skin for every enemy is a subject of current QuakeWorld discussions, the possibility to use different skin on each enemy is limited and controled.
Limitation: This feature will only work if the very same Qizmo feature works - that is - only if server allows it in it's FPD setting.
Control: If you use this feature, it will be reported in f_skins response and also auto-announced every time you change it.

This feature can be enabled using the `/enemyforceskins` variable.

For example by setting `/teamforceskins 1` and your teammate is ". ParadokS", he will get "_ ParadokS" skin name assigned since the algorithm replaces some characters with underscore so that you get proper file name.

By setting "enemyforceskin 3", your enemies in a 4on4 game will have skins "e1", "e2", "e3", "e4". That means you need to have e1.pcx, e2.pcx, ... (or png) files in your skins directory. Your teammates will get the same skins assignments if they use "enemyforceskins 3", so you can share "red guy has RL!" info in your team. However if you play the very same team another time on another server, it's players will get different permutation of "e1", ..., "e4" skins assigned, so "the red guy" can be someone else the next time.

These rules have lower priority then basic skin forcing. Therefore you need to turn `/teamskin` and `/enemyskin` off if you want to use those.
