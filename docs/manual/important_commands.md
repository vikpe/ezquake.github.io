---
layout: default
tab: Documentation
---

# ezQuake Manual - Important commands
(automatic conversion from internal help - last edited Sat 16-Oct-2004)

## Important commands


The most important and commonly used commands which are used while playing QW will be explained below. All have to be entered into the console which can be brought up by the tilde (~) key:

- **connect [ip:port]** The "connect" command is always followed by an IP address/hostname and will connect you to the server specified. Sometimes you also have to add the port after the IP address unless the server runs on the default port 27500. You can paste addresses for example from IRC into the QW console by pressing Ctrl+V at the same time. Examples:
```

connect 160.45.32.200:27501 connect archroy.barrysworld.com
```


- **disconnect** This command is needed to disconnect you from a server.
- **reconnect** You need this to reconnect to the last server you were connected to because you either timed out, QW loaded the map but you didn't spawn or something else happened. You also need to reconnect if you want to changer into spectator mode or vice versa.
- **spectator 0|1** If you want to spectate a game you have to set spectator to 1 before connecting or reconnecting to a server. If you want to connect as player you have to set it to 0 (default) before connecting or reconnecting to a server.
- **join** If you are already on a server as a spectator and want to join the game, just type this command instead of writing_spectator 0_followed by_reconnect_. Faster and easier!
- **observe** Works the same way as the_join_command. If you are playing on a server and want to reconnect as a spectator, use this command.
- **cl_chasecam 0|1** **cl_hightrack 0|1** There are different modes of spectating. When chasecam is set to 0 you can float around the map yourself with the movement keys and position yourself to any area you are interested to. When chasecam is set to 1 the cam will follow one player. You can use the attack/jump button to change the tracked player and wether you see everything through the players eyes or wether the cam is positioned above him. If hightrack is turned on the camera will always follow the player who has the most frags.
- **password [x]** Some servers are password protected. If you happen to know the password you have to type password and after that the password itself before connecting to that server. Sometimes the observer spots on a server are also password protected and the password is submitted in a different way. Type spectator followed by the password in the console before connecting. Examples:
```

password hejsan (then connect ip:port) spectator pylly (then connect ip:port)
```


- **quit** If you are fed up with playing just type this at the console and you are relieved...
- **team [x]** When playing a team game you have to set your team by typing "team" followed by the teamname which can be up to four letters long. Note that teamnames are case sensitive and can contain spaces and special characters. Examples:
```

team red (puts you in team red) team " red" (puts you in team _red, therefore the ") team "^-er^-" (puts you in team -er- (putting the ^ before a character will make it appear red instead of gray))
```


- **sensitivity [x]** This controls the sensitivity at which your mouse works and has to be followed by a number. Example:
```

sensitivity 5.2
```


- **fov [x]** This command determines your field of view. Allowed values range from 10 to 170. Much more than 130 and less than 90 are not very useful though.

## Kombat Teams/KTPro commands

Most QW servers run a mod called either Kombat Teams or KTPro (KTPro is a newer and improved version of the older Kombat Teams). These are modifications of the QW server designed specifically to make competitive play more easy (no changes to the general gameplay have been made though). The most important commands on these servers are explained below:

- **ready** Everyone has to type this before the countdown that starts the game begins.
- **break** This will either stop the countdown or, if a match is going on, vote to stop the match. Matches will only be stopped if the majority of players votes for breaking.
- **timeup** **timedown** Change the timelimit by 5 min increments.
- **dmm[1-7]** Changes the deathmatch mode. The usual deathmatch modes are dmm1 (standard in 4on4) and dmm3 (standard in 1on1 and 2on2). All the different modes are explained below:
```

dmm1 = weapons disappear when you take them and return after 30 seconds, ammo returns after 20 seconds. dmm2 = as described above, but no health or armor on maps. dmm3 = weapons stay when you take them, ammo returns after 20 seconds. dmm4 = spawn with 255 armor and health, plus all weapons except for the grenade launcher.
```


- **powerups** Toggle powerups on or off.
- **[mapname]** You can vote for a mapchange by simply typing in the name of the new map you wish to play (it has to be supported by the server though). A majority of all players on the server has to vote for the map to change.
- **whonot** Check who has already gone ready and who is holding things up.
- **commands** **options** **cmd help** Use these three to get a more detailed list of commands and settings available in KTeam/KTpro.

