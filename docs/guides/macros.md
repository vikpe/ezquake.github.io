---
layout: default
tab: Documentation
---

## Teamplay macros

###### (this topic was ported quickly from old documentation and needs updated)

You can use Qizmo teamplay %-functions in ezQuake, e.g. %l - location, %a - armor, %b - best weapon, etc.

    %a : Armour.
    %A : Armour type.
    %b : Best Weapon and Ammo.
    %c : How many cells (ammo) you have.
    %C : Color.
    %d : Where you last died.
    %e : Number of enemies in your vicinity. (shows up as "x" for you, but as a number for your teammates).
    %E : Same as %e but remembers the situation 5 seconds after death. (shows up as "x" for you, but as a number for your teammates).
    %g : Soon appearing powerups (15 sec) or 'quad' if none or timers off
    %h : Current Health.
    %i : Name and location of item you last picked up.
    %j : Name and location of item you last pointed to (%x at %y).
    %k : Name and location of item you last picked up or pointed to.
    %l : Nearest location from .loc file (or 'someplace' if none found).
    %L : Same as %l but remembers the situation 5 secs after death, then reports your current location.
    %m : %k if less than 5 secs ago, nearest item otherwise
    %n : Will only send the message to teammates in your vicinity.
    %N : Hides the message from you.
    %o : Number of teammates in vicinity.
    %O : Same as %o but remembers the situation 5 seconds after death.
    %p : Powerups you have (quad, pent, ring, flag)
    %q : Powerups of last seen enemy.
    %r : Last reported location (%l).
    %s : Enemy led status.
    %S : Skin.
    %t : %x at %y
    %u : what you need (see need menu)
    %w : Weapon in Hand and Ammo you have.
    %x : Name of object/teammate you are looking at.
    %X : Name of object you took. (remembers for 15 seconds)
    %y : Location of object you are looking at.
    %Y : Location of item you took. (remembers for 15 seconds)
    %z : nearest waypoint, based on the direction you are looking to
    %Z : nearest waypoint, based on the direction you are moving to

You can set global color of your teammates by `/teamcolor` command, color of enemies by `/enemycolor`.  To make sure these changes are reflected in a consistent scoreboard, set `/scr_scoreboard_forcecolors 1`

You can adjust skins of teammates and enemies by `/teamskin` and `/enemyskin` commands. You can have separate skins for teammates and enemies with powerups too: see `/teamquadskin`, `/teampentskin`, `/teambothskin`, `/enemyquadskin`, `/enemypentskin`, `/enemybothskin`.

    teamcolor 13
    enemycolor 4
    enemyquadskin enquad
    teampentskin tequad

This example will give you blue teammates, red enemies, skin read from enquad.pcx picture to be used on enemies with Quad powerup and tequad.pcx texture on teammates with Pentagram protection powerup.

#### Formatting

The format of each variable can be set by specifying a format string.  For example:

    %<20r>l

Will print the standard %l value, but taking 20 characters, right-aligned.

To set the default formats for each %-function without specifying each time, set user-cvars:

    /set tp_length_l 10
    /set tp_align_l r
