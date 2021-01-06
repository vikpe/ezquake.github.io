---
layout: default
tab: Documentation
---

# ezQuake Manual - Commands and variables
(automatic conversion from internal help - last edited Tue 07-Oct-2003)

## Commands and variables

## The QW console

You can change nearly every setting of QW from the game within by typing it in the console. You can either reach the console through the menues (press escape -> setup -> keybindings -> go to console) or more easily by pressing the tilde (~) key (QW always switches to american/english keyboard layout where the tilde key is located on the top left below the escape key).
## General commands and variables

Every console command is simply entered at the console (or in your cfg file) ,often followed by a value. The often used "bind" command requires the key which is to be bound followed by the action or alias to be bound to that key. For example if you type BIND W "+FORWARD" you will walk or run forward as long as you keep the w key pressed. The meaning of the "+" as well as other commands like "alias" will be explained further below in the advanced section.

If you find a command or a variable (called, say, foo) that you do not understand, type_/describe_foo.

Here are the most important general QW console commands you should know about and which you can put in your own config along with a short explanation:

(Some of the following settings can also be changed through the menus of Quake but not all of them.)

```

bind w "+forward" bind a "+left" bind s "+backward" bind d "+right"
```


Most people use the WASD keys to move around in first person shooters, because they are both near to the keys that select weapons (1 t0 7 and 0 by default in Quake) and there are lots of other easy to reach keys around. Those are often used for teambindings or scripts.

```

bind mouse1 "+attack"
```


```

bind mouse2 "+jump"
```


This is an example how two other important commands can be bound to the mouse buttons. It is completely up to you what you bind where but it is very common to bind the left mousebutton to attack and the right mousebutton to jump. The middle mousebutton is often used for a script.
## Weapon impulses

In Quake weapons are selected by impulses. For example typing impulse 2 would select the Super Shotgun. Each weapon impulse is assigned to a single weapon and the number of the impulse if by default bound to the corresponding key on the keyboard (not on the numpad!). Weapon impulses become important when creating weapon selecting scripts. Here are Quake's weapon impulses:

```

impulse 1 = Axe impulse 2 = Shotgun impulse 3 = Super Shotgun impulse 4 = Nailgun impulse 5 = Super Nailgun impulse 6 = Grenade Launcher impulse 7 = Rocket Launcher impulse 8 = Thunderbolt impulse 10 = Next weapon impulse 12 = Previous weapon
```


- **+mlook** Turns on mouselook which is only possible by doing it via console/cfg and thereby often confuses new players because they can't find it and it isn't turned on by default either.
- **+speed** Turns on always run, in QW being slow means being dead very soon. there is absolutely no need to walk in this game.
- **name [name]** Sets your name. It can be up to 11 letters long and will consist of white letters only. The colored names can either be created by an external program or through the Qizmo proxy (see for explanation elsewhere).
- **color [x] [y]** Sets both your shirt and pant color to the same type of color if you just give one value. Otherwise the first is top and the second bottomcolor. The corresponding colors to the codes are the following:
```

0 = white 1 = brown 2 = light blue 3 = olive 4 = dark red 5 = beige 6 = pink 7 = light pink 8 = magenta 9 = violet 10 = light brown 11 = blue-green 12 = yellow 13 = blue
```


- **team [name]** Will set your team for teamgames. A maximum of 4 letters is allowed. The teamnames are case sensitive but most people use small letters.
- **crosshair 0|1|2|3|4|5|6|7** This will change the crosshair. In ezQuake there are 7 different crosshairs. 0 turns it off.
- **crosshaircolor [0-255]** The defaultcrosshair color is red. If you prefer another try and play around with the values.
- **sensitivity [x]** This sets your mouse sensitivity. In general the lower the number the slower the mouse will move. Values differ from pc setup to setup. While 10 can be rather slow on some, it can be ultra fast on others. You should test and adjust this from within the game.
- **m_pitch [x]** This controls the speed at which your mouse moves up and down. Most of the time the default value (which is 0.022) seems to be good.
- **m_filter 0|1** Turning on the mouse filter will smooth out the mouse movement. It has some disadvantages such as the fact that it lags mouse movement by 1 frame (14ms at 72fps). Players with 100hz+ mice shouldn't need it, especially if using -dinput, but it's down to personal preference really.
- **scr_conspeed [x]** This determines the speed with which the console scrolls down. It's good to set it to a high value like 5000 because its slow default speed gets annoying especially when you are testing and using the console often.
- **con_notifytime [x]** If you want messages to be displayed for a longer or shorter time play around with this setting (default is 3).
- **fov [x]** This sets the field of view in degrees. The default value is 90 and the maximum is 170. The higher the value the more you see which is good but the weirder looks the environment wich is not good with values higher than 130.
- **rate [x]** This sets the rate at which your client sends a packet to a server. For more detailed information look in the "ping and lag" section. If you use a modem use 2500, 5000 for isdn connections and 10000 (the maximum) for high bandwidth connections.
- **pushlatency -999** This setting affects the prediction of your client. -999 turned out to be a nice setting regardless of your actual latency. More info at [ping and lag.](ping_lag.md) 
- **noskins 0|1|2** This turns on and off custom skin support. 0 means no skins are supported and every player will use the base skin. 1 means that customskins are supported and will be downloaded from the server. 2 also enables custom skins but won't download skins you don't have yet from the server.
- **cl_sbar 0|1** This lets you switch between the two different styles in which the status bar is displayed. In style "0" all the players information is displayed at the bottom of the screen. In style "1" only health, armor and ammo of the current weapon are displayed at the bottom. The weapons you collected and the ammo for them are displayed on either the right or left side of the screen. The display on the bottom will be transparent depending on your viewsize.
- **cl_hudswap 0|1** Switches the cl_sbar display to the left ro the right side of the display.
- **viewsize [10-110]** Sets how much of the action is displayed on the screen. The highest value will hide some vital information like health, armor, etc. while lower values mean more frames per second.
- **bind tab "+showscores"** The showscores command will display the fragcount and names of all players connected. It also shows their ping, packetloss and time in minutes they are connected to the server.

## Advanced commands

The following commands are not absolutely necessary but they are useful when you want to play QW seriously because they can help you to improve your game. Since they are not documented they are also not easy to find and the average user would not even think that they exist.

- **v_kickroll 0** Turning kickroll to 0 means that you do not lean anymore when you get hit.
- **v_kickpitch 0** You wont look up a bit anymore when being hit.
- **v_kicktime 0** Determines how long the kick effects last, in this case 0 seconds of course.
- **v_idlescale 0** When standing still the view remains idle. A few other commands determines how much you pitch forwards, sidewards etc. when this setting is turned to "1". Turning it on is not recommended (its off by default btw) except if you want to play "drunken quaker". Could also be used to create some sort of "screensaver".
- **cl_rollangle 2.0** **cl_rollspeed 200** These two commands determine how far you and the other players lean to the left and right when strafing and how fast they straighten out when strafing is stopped. The values given here are the default values. Higher angle values helps you to predict other players movement. It depends a lot on your personal preferences wether you use default or higher values. Just play around a bit with them to see which you prefer.
- **cl_bob 0** This turns off the up and down movement of your weapon (if it is displayed).
- **cl_forwardspeed 3096** **cl_sidespeed 3096** **cl_upspeed 3096** **cl_backspeed 3096** Setting the speed of the various types of movement to higher values than the default ones (200 for forward and backward, 320 for sidespeed) is not of much use because the maximum values are determined by the server. But well, you never know :-)

## Building advanced cfgs/scipts/aliases

QW has a powerful script language that allows you to built many usefull and also not so useful scripts. In this section we will present some of the most common scripts and explain how they work. First you need to know the how QW's script language works:

The format for binding a key is as follows

```

bind
```


Putting a + or - in front of a command will execute it only as long as you keep that key pressed and what happens when you stop pressing that key. The most common commands where this is used are the movement commands like "+forward". As long as you keep the key pressed you will move forward. Commands can not be only those hardcoded into QW but also those defined by yourself. Such a command is called an "alias". Basically an alias is a list of commands which will be executed one ofter the another and can be bound to a single key. Multiple commands must be enclosed by quotation marks and sepereated by semicolons. It is possible put an alias into another one.

Example:

```

alias myname "name myname;color 4;team abc;exec team.cfg"
```


```

bind n myname
```


This simple alias would change your name, your color, your team and execute another config at the same time by simply pressing the n key.
