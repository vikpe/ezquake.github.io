---
layout: default
tab: Documentation
---

# ezQuake Manual - Qizmo
(automatic conversion from internal help - last edited Tue 07-Oct-2003)

## Qizmo

## What is a proxy and why Qizmo?

A proxy is a program that works with network packets moving between a QW client and a QW server. It can both analyze and alter those packets. The first proxy, FAQproxy, was created to be able to play QW from behind a very restrictive firewall. More and more features were added to this and later to other proxys. Some of them, like the powerup and item timers were considered cheating and thus removed. Later protection from cheats became one of the main features of the modern proxies. Nowadays Qizmo is basically the only proxy being used because it has lots of advantages over the other available proxies and because it is mandatory in almost all online leagues and competitions. The main features of Qizmo include: menu system, teamplay help, server browser/pinger, voice channels, data compression and fps boosting.
## Installation and setup

Qizmo is shareware and can be downloaded from the [Qizmo Homepage](http://www.udpsoft.com/qizmo/) . It is free and there are no restrictions in its funtionality. If you decide to register it however you will receive and even better data compression. After downloading Qizmo just put the files in a directory of your choice. After starting both Qizmo and your QW client you have to type_connect localhost_to connect to the Qizmo. It is much smarter and easier though to start both from the command line like this:

```

[path to qizmo] [qizmo options] [path to qwcl] [qwcl options]
```


for example:

```

c:\quake\qizmo\qizmo -p 27501 c:\quake\qwcl -nosound
```


This way you will start Qizmo which in turn automatically starts QW client and connects to it. It is also the only way to enable the f_ checks explained below and which are necessary to play in online leagues.

After you have connected you should type_say proxy:menu bindstd_. You can now browse the menu with the arrow keys. Enter, backspace, insert, home, pageup, pagedown, end, delete and pause will also be bound to menu actions (pause turns the menu on and off). If you do not like this selection of keys you can change the "menu.cfg" file. It is a good idea to add "exec menu.cfg" to your "autoexec.cfg".

Now you can change anything you like in the menus. You can save you current setup by going to "config" and choosing "save". Your setup will be saved under your nickname in the ../cfg/ subdirectory. There next time you connect to the Qizmo with that nickname your setup will be restored.

For more important info like starting Qizmo through gamespy, setting access rights for different users and all its command line options check the readme file that comes with Qizmo.
## Issuing commands to a Qizmo

There are in general two ways to control Qizmo. Either through the menu or by the console. Using the menu is easier of course but sometimes using the console is still faster and thus more comfortable. Especially when it comes down to common and often used commands like_reconnect._But that command (and many others) are not only used by Qizmo but also by the QW client. A command that should be executed by the proxy has therefore to be preceded by a_._. In our example you woudl have to type_.reconnect_. In case you are connecting through more than one Qizmo you would want to issue that command towards the last proxy in the chain. In this case you have to use a , in front of the command. In our example it would be_,reconnect_.
## f_ queries

The f_ queries enable you to check some things out about the other players on the same server. They will only work when the others are using a proxy as well. Some are unique to Qizmo. The queries are important for playing in online competitions because they are the only way to check clients for cheats (although they will never provide 100% protection from cheats they make cheating much harder). The most important f_queries are:

- **f_modified [x]** This will check for altered models and sounds in your pak files which could be used for cheating. If a model does not have the original crc size its name will be reported. If nothing is modified it will report the crc value over all models. You might specify x which will be added to this value.
- **f_version** This will report both the version of the proxy used as well as the operating system.
- **f_speed** This will display the running speed in %. Values over 100% are considered cheating but can also occur on win9x systems that have not been rebooted for a long time. In this case just reboot and the speed will be below 100% again. It is actually possible to get f_speed values over 100% with qw2.33, probably due to errors in calculation. On fast CPUs up to about 100.05 and higher values aren't that uncommon.
- **f_skins** This will report the percentage of fullbright pixels in team and enemy skins.
- **f_cmdline** Displays the commandline of other users.
- **f_system** Displays info about the systems of the people connected to the server.
- **f_server** From the Qizmo readme: Each Qizmo responds with 'x->y', where x is a crc of the ip address of the proxy and y crc of the address where the player is connected to. So you should get either:
```

player1: x->y player1: y->z player2: x->z
```

where x and z should be same for everyone on the server and y changes for different server side proxies. If this is not the case, someone might be using a bot."
Sometimes f_server does not give the expected results when connected to a public Qizmo that does not have reverse dns (?). The same public Qizmo will give the same results for all connected players though, so it can easily be validated.

This will also help to determine if there are other proxies in between. There are some public Qizmos which are known for reporting wrong crc values. To check wether this is the case connect to the same proxies as the user whose Qizmo reported wrong, type .f_server and your Qizmo should report exactly the same (wrong) crc values.


## Data compression and "chaining" of Qizmo

One of the most usefull features of Qizmo is the data compression. Qizmo can compress the packets sent from your client to the server making them much smaller. Smaller packets mean that you can use a higher rate. A higher rate means much smoother gameplay and more fps. By connecting through one or more Qizmos the routing of the packets might also be changed resulting in lower pings. How does this work exactly?

Without Qizmo in between packets will move from you client to the server and vice versa. If you have a low bandwitdh internet connection not many packets can be send at the same time, thus you will have to lower your rate or you might suffer from packet loss. Now you start a Qizmo on your machine and from there on connect to another public Qizmo which is either very near to the server you want to play on or somewhere at your internet service provider. If compression is turned on on both of the proxies you can use a much higher rate than before because each Qizmo will compress the packets it receives from the client/server while the other Qizmo will decompress them.z

Since both Qizmos are physically very near to the client or server (and the public Qizmo usually has much higher bandwidth) the increased traffic between that Qizmo and the server/client does not matter. By connecting through different Qizmo's you can also improve the connection dramatically to server where you would usually have never been able to get a playable ping and packetloss. Because of all this with Qizmo international competition has become a reality.
## Turning on compression

Before being able to turn on the compression you have to make sure that your setup looks at least like this: client -> Qizmo1 -> Qizmo2 -> server

It might be a bit confusing to turn on compression because there are option to compress/decompress both outgoing and incoming packets especially because both menus look very similar and you have to make sure you turn it on on the right Qizmo.

In the above setup make sure you are on "Qizmo1". The name of that Qizmo is displayed in the upper right corner of the menu (if you see another name then go to "previous proxy" or "next proxy" to make sure you are on the right Qizmo). Then go the the "data compression" menu. There you select the "c2s" tab (client to server, in our example Qizmo1 to Qizmo2). In that menu set "compress outgoing" to "on". Now you have to go to Qizmo2 (either use the "back" buttons or the home key with default keybinds to get to the main menu, there press "next proxy"). Once you are sure you are on Qizmo2 go to "data compression" and this time choose the "s2c" tab (server to client, in our example Qizmo1 to Qizmo2). There you have to turn on "outgoing compression". If you did everything right both Qizmos should now diplay info about the compression rates in the "data compression" menus.

There are a few other settings available with which you can improve the perfromance of your Qizmos. If there is a good connection between the two proxies you can turn on the "quality line" mode. If the connection is not so good however it will multiply any packetloss between the two (type .showdrop and ,showdrop to see proxy - proxy pl). If you are low on bandwidth you could also turn on "lossy compression" which will drop some unnessecary data here and there. You can also make the Qizmos repeat their packets which helps if you suffer from a lot of packet loss. But this is only a good idea if you have a large bandwidth (dsl and higher).

If you intend to use the same setup regularly make sure you save this configuration in the "config" menu so that you don't have to turn everything on again the next time you connect to those Qizmos.
## FPS settings

Qizmo can help you to improve your fps alot by changing things that are usually not changeable without hacking your exe or the paks. All these settings can be found an changed in the "FPS settings" menu. Since some of the settings will take more bandwidth than the default ones you should always use them on your local Qizmo only!

- **Explosions: [normal|tarbaby|teleport|blood|off]** The dynamic lighing that occurs when rockets and grenades explode can take a lot of fps (and the explosions looks rather ugly too especially in gl). Choosing something else will remove these lighting effects. It takes some time though to get used the new "explosion" type.
- **Powerup glow: [on|off]** This will turn off the glow of powerups you are wearing. If you turn this off (and also use different rocket explosions) you can leave flashblend on in gl.
- **Powerup glow: [on|off]** This will turn off the glow of powerups you are wearing. If you turn this off (and also use different rocket explosions) you can leave flashblend on in gl.
- **Muzzleflashes: [on|own off|all off]** When someone fires a weapon there will be a small flash near his weapon which can be turned off by this option.
- **Gib filter: [on|bodies|off]** Although gibs are fun they can cost you lots of fps. You can either turn them off completely or just remove the dead bodies.
- **Rockets: [normal|grenade]** You can replace the normal rockets with the grenade model. This has two advantages. The dynamic lighting effect which costs fps will be removed and the smoke trail of grenades is much smaller and won't block your sight.
- **Userinfo filter: [on|off]** "Usually when someone changes their userinfo the new settings are broadcast to every player on the server. This filter drops all 'noaim' (some people change noaim all the time for different weapons) or 'rate' (Qizmo spams these when 'autodrop rate' is on) setinfos." (info taken form the Qizmo readme)
- **Nail filter: [off|1/2|2/3|3/4]** You can reduce the number of nails which will save some bandwidth because nails don't compress very well.
- **Damage filter: [on|off]** Turns off the red flash when being hit.
- **Ambient sounds: [on|off]** This will turn off ambient sounds like humming lights, wind or other effects which woudl otherwise disturb you from hearing other more important sounds made by other players.
- **Pickup flashes: [on|off]** This will remove the flash when picking up an item.
- **Powerup blend: [on|off]** Will turn off the palette change when bearing a powerup.

## Sound and voice channels system

Qizmo comes with its own sound system which is superior to the one qw uses because it offers more options. In order to make it work you have to turn off qw sound by starting it with the -nosound paramater. Now you can turn on Qizmo sound system by going to "sound system" and setting "play gamesounds" to "on". Most of the other settings in that menu deal with the voice channels explained below and can be left as they are when not using them. What you should however do is to go to the "settings" and turn on the "enhanced stereo" effects which will give you a slightly better 3d sound than qw usually has (also depends a lot on your soundcard, though).

Voice channels you can communicate with other players in real time which is very usefull in teamplay. First you have to turn on the voice channel system in the sound system menu. You also have to turn on "voice capturing" to make your microphone work. In order to talk to your teammates they all have to be on the same Qizmo. Now you can go to "voice channels" and join up to 8 different voice channels. You will also be asked by Qizmo which key you want to bind to activate a given voice channel. There are two predefined voice channels. "Near" lets you only talk to teammates near you that are in your field of view. "Feedback" will send you own voice back to you for testing purposes.

For more info about Qizmos sound settings check the Qizmo readme (the sound section is actually rather good imo).
## Server browser

Qizmos built in server browser is a good tool to ping and connect to servers without using another program like gamespy making it much more comfortable (although Qizmo server browser has some limitations). The server browser works much like similar tools by pinging server lists (either custom made ones or master servers where the online servers report). One of the advantages of the Qizmo server browser is that it reports ping times to a server much more accurate and in general works faster.

From the main menu select "server browser" to get to it. As mentioned it works quite the same as Gamespy etc. so you first have to select a server list. In order to do this you have to go to the "sources" tab. There you will find a list of master servers (and also custom server lists if available). Choose one or more of them. Then you have to go to the "ping" tab. There you must first choose "update sources". Qizmo will ask the master server for the list of servers it currently has. If you chose a custom server list in the sources you don't have to update it. Now choose "start pinging" and Qizmo will ping and get information from all all servers in the list.

When finished Qizmo will also display info on how many servers where pinged, how many responded, how many people are playing on those servers etc. Before moving to the "List" tab you should go to "Sort" before to sort the servers, usually by ping or players. In the "List" all servers are displayed with their name and how many people are currently playing on them.

After selecting a server from the list the "ctrl" menu will be brought up giving you the ability to finally connect to it. Just select the "connect to" option to do so. In the same menu you can also choose between connecting as player or spectator and wether you want to connect from this proxy or the last one (depends on from where you ping the servers. For example if you have your own custom server list you will usually ping from your local Qizmo and you have to select "connect from: last" to make the last prxy in the chain to connect to the server). Finally you can use "back" to return to the list of server. On the same level of that menu you can also show some more detailed info, for example about the players, by moving left/right to go to the "players", "rules" and "source" menus.

Beside just pinging the master servers you can also create you own custom server list. To do that you go to the "sources" tab and select "add source". You will first be asked for the type of source, type "file" at the prompt. After that you will be asked for the name which will be shown in the list and also for the actual file name. It is important to add the file extension, too. If you have an existing list, you can add further servers to it from within Qizmo without having to use a text editior. To do this use the "add server" option as normal, but then goto the "source" menu and you can add it to other sources, including serverlist files (provided they arent read-only). In this way you can e.g. copy servers from masters to your own custom file.

Two tabs from the server browser have not been ecplained yet: "Control" and "Filters". Both are not really needed in day to day play. "Control" only replaces the most common commands to connect, reconnect to a server etc. Usually it is easier to just use the console (by typing ",reconnect") or the action is already covered in the "ctrl" tab of the server list. With the "Filter" tab you can determine which servers from a list to display. For example only teamplay servers. However the most common master server lists are not so large that you need them to be sorted in that way.
## Teamplay help

One of the most important features of Qizmo is the teamplay help. In the days without proxies teamplay was a lot different from what it is today. People soon dicovered that communication in teamplay games was crucial for winning. However typing something in the console takes time, too much time to be actually usefull. So people started binding keys to standard messages which were often used. For example something like "Rocket Launcher secured". Since the complexity of teamplay increased rapidly a lot of those binds were needed for different situations. So people built whole menus of teamplay binds with alias files of several hundreds of kilobyte size.

Later someone had the smart idea to let a proxy do most of that for you. With a proxy you could decrease the number of keys to be used for teamplay messages by a large number while still maintaining a large complexity and variety of them. The inclusion of the teamplay help commands probably had a larger impact on teamplay as it is known today than anything else.
## How does it work?

Using a proxy for team messages is superior to using simple aliases because proxies use variables (called %-commands in Qizmo). For example you want your teammates to know that a certain area of the map is secured. You could use an alias like:

```

alias rlsecure "say_team rocket launcher is secured"
```


If you want your team to know that a different area is secured you would use another alias and thus another key or some sort of menu system. Adding a variable to that you can have only one bind for different areas. The one needed here would be the "%l" command which replaces the %l in a message to the actual area where you currently are (the position and the name of that area are determined by a .loc file explained below). So the only alias you need would be:

```

alias secure "say_team %l is secured"
```


All other %-commands work after the same principle (except that only %l needs a loc file to work) and you can tell your teammates how much ammo/health/armor you have, wether items are available or wether you are in need of items.
## Using teamplay help

The teamplay help menu of Qizmo offers a lot of option. Instead of explaining them one after the other i will explain what to do in which order to get as much teamplay help by Qizmo as needed. Some of the option available are usually not used or turned off server side. If you want to know more about the options available which are not described below refer to the Qizmo readme.
## Setting team/enemy skin and color

Qizmo has some "overrides" which allow you to set specific skins and/or colors to teammates and enemies. Just go to the menu and type the name of the skin you want to be displayed. You can also set skins through the console by using the ".skin" command. Examples:

```

.skin blue red (teammates will wear blue.pcx and enemies red.pcx as skin) .skin * red (no change for teammates, enemies will wear red.pcx as skin)
```


Usually people play with one colored fullbright skins, for example a red one for enemies and a blue one for teammates.

Color forcing works just the same as skin forcing and is usefull if you play just with base skin or if different colors in the scoreboard confuse you. Again you can either use the menu or the console:

```

.color 13 4 (teammates blue, enemies red) .color * 4/12 (no change with teammates, enemies wear red/yellow)
```

## Creating .loc files

The %l commands is the most common and important of all teamplay commands because telling your teamates what is going on at a certain location of the map is crucial. In order to be able to use it you have to create a .loc file which stores the name and exact position of a location. A .loc file is created by creating "beacons" on a map each carrying a name describing the area. The .loc file will always be named after the map (for example dm3.loc) and will be loaded when you change to that map. The file has to be stored in the same directory as Qizmo.

Before you can begin to create your locs you have to connect to that map either on a local or an internet server. Now you just go to the location that you want to be marked, choose "mark current location" from the menu, enter a name for the location at the prompt and it will be saved in your .loc file. The menu also has options to delete the the nearest mark or replace the last one. The more locations you mark the more precise the information in your .loc file will be because the %l-command will always display the nearest mark. It is a good idea to have an alias for testing while setting your marks (something like alias test "say_team i am at %l") so that you can check for errors.

If you are not willing to make a .loc file yourself you can also use the "Include automarks" function if Qizmo which will mark all important items like weapons, powerups etc. on a map.
## Creating teambinds

The following codes can be used in teammessages (and only in teammessages=say_team !):

```

%A : Armor type. %a : Armor. %b : Best Weapon and Ammo. %e : Number of enemies in your vicinity. %h : Current Health. %l : Nearest location from .loc file (or 'someplace' if none found). %n : Will only send the message to teammates in your vicinity. %N : Hides the message from you. %o : Number of teammates in vicinity. %p : Powerups you have (quad, pent, ring, flag). %w : Weapon in Hand and Ammo you have. %x : Name of object you are looking at. %y : Location of object you are looking at. %g : Soon appearing powerups (15 sec) or 'quad' if none or timers off. %i : Name and location of item you last picked up. %j : Name and location of item you last pointed to (%x at %y). %k : Name and location of item you last picked up or pointed to. %m : %k if less than 5 secs ago, nearest item otherwise. %d : Where you last died. %r : Last reported location (%l). %S : Skin. %C : Color. %L,%O,%E : Like %l,%o,%e, but remembers the situation 5 secs after death. %q : Powerups of last seen enemy. %t : %x at %y %z : nearest waypoint, based on the direction you are looking to. %Z : nearest waypoint, based on the direction you are moving to. %u : what you need (see need menu).
```


You see there are lots of possibilities with that many commands. Here are some examples for common team messages:

_/safe message_

```

say_team $/nick %l safe %b %p
```


This message would display information about the current area being safe. It also displays your best weapon and how much ammo you have for that weapon. If you have a powerup this will also be added. The "$/" replaces the actual name of the player with a short nickname.

_/item availabe_

```

say_team $/nick %x @ %y
```


This will tell your names that the item you are looking at is vailable to be picked up.

_/status report_

```

say_team $\nick [%a %h %b] at %l %p
```


This message will give your teammates information about your current status by telling them your armor, health and best weapon. It also displays your current location and the type of powerup you have.

More usefull and advanced teammessages can be found in the teamplay strategy section of this guide.
## Weapon aliases

Qizmo can replace the commonly used bestweapon aliases with a more effective and reliable method. Instead of having some alias containing something like "impulse1;wait;impulse;...;impulse 7" you can define one single impulse that selects the best weapon for which you have ammo. This makes weapon selection faster. Go to the "Misc stuff" menu and then to "weapon impulses". You can define up to 4 different weapon impulses. Qizmo will ask you for "number" and "list". Number is the impulse you want to use and list is the list of different weapons you want to go through. For example if your weapon impulse is "10 2345678" you can bind a key/button to impulse 10 and when you press the button you will shoot with the best weapon you have ammo for.

Even though the Qizmo readme claims that this method is more reliable this is not quite the truth. If you suffer from some packetloss and compression is turned on the weapon impulse will sometimes not work correctly. For example it will shoot with the shotgun even though you have a rocketlauncher and ammo for it.
## Demo playing

Qizmo comes with a built in demo player. Of course you don't necessarily need Qizmo to playback demos, qw client is sufficient too, but it is much more comfortable. One of the main advantages is that Qizmo can play back the much smaller compressed demos created by Qizmo. It does also play older demos which were recorded with older QW clients.

To access the Qizmo demo play you have to go to the "demo player" menu. There you can select the demos to view which must all be in the ../qw/ directory or the demo directory you specified through the -e parameter. The option of playback should be pretty obvious and include playback, fast forward, pause etc.
## Demo recording

Qizmo also offers advanced methods of recording demos. The most usefull feature is obviously_easyrecord_which will record demos of each map you play and which will name them properly according to the mode of play (ffa, duel, teamplay etc.). A new demo will be recorded with each map. So you can concentrate on playing and later you can delete demos you don't like. There are also some firther options which are not so important but you can even record voice messager!
## Client list and observing

One of the most usefull features of Qizmo is accessed through the client list, observing of other players. Usually there are not more than 4 spectators allowed on a server while much more people want to see the game. If a spectator is connected through a Qizmo and you are on the same Qizmo you can observe him that means you can see everything he does as if you were spectating on the server yourself.

Just go to the "client list" menu. There you can now set up some setting concerning youself in the "control" tab. For example you can define the number of people allowed to observe you or wether they need a password if you want to maintain some privacy.

If you go to the "follow" tab you will see the list of players connected to the same Qizmo. If you select one of them you will follow him and connect to the server where he is playing. This way you don't have to mess around with the server browser.

If you go to the "observe" tab you will see the list of players as well but when you select them you will start observing. You will not actually connect to the server where that player currently is but you will see everything he does.

Finally there are also tabs for kicking people that observe you and bringing up the server menu.
## Fun conversion

Qizmo has a nice feature which renders the once popular custom name/script generators useless. With Qizmo you can create your own fun names and scripts containing special characters and colors. Go to the "misc stuff" menu and turn "fun conversation" on. The console will then display what character sequences will be changed. For example putting a "$" in front of a number will make it a golden number while putting a "^" in front of letters will make them red. This will work in all messages and also with names and even with teamnames.
## Last words

You should now be able to use the most useful features of Qizmo and you should now also understand how they work. If you need more information for example on menu items not explained here refer to the Qizmo readme file. Now that you have some basic knowledge you should have no problems in understanding the sometimes confusing readme.

If you like Qizmo, and i am sure you will, you should register it. You will not only receive an even better compression (and a few other nice things) but you will also support the authors because without them and their Qizmo there would be no QW anymore.
