---
layout: default
tab: Documentation
---

# ezQuake Manual - Quick guide
(automatic conversion from internal help - last edited Sat 16-Oct-2004)

## Quick guide

## Step 1: Downloading QuakeWorld

In order to be able to play Quake on the Internet you have to download and install QuakeWorld, which was designed specifically for that purpose - Internet play. Basically QuakeWorld is a new client that improves the netcode of Quake dramatically and also adds some new features like player prediction and [bunnyhopping](help/jumping.xml) .

Since finding and configuring all the files you need to play QW can be quite a pain for newcomers, there is a solution. [nQuake](https://www.nquake.com//) is a handy installer that contains basically everything you need in order to play: [ezQuake client](http://ezQuake.SF.net/) , PAK-files, maps, textures, locs, scripts and a lot more. All put together to supply beginners as well as veterans with an easy-to-use QW installation. Get [nQuake](https://www.nquake.com//) now!
## Step 2: Configuring

nQuake comes together with configs that use the most common and optimized settings. However there might be a few things you may want to change to suit your needs, like movement/weapon keys, sensitivity, graphics settings etc.

The configs that ezQuake uses are stored in ezquake/cfg, so go there and edit your config. Please refer to the [ezQuake Documentation](http://ezQuake.SF.net/docs/) if you want an explanation on all of the variables in the config.

You can also edit your config via the QW console (loaded upon start, or bring it down with the tilde (~) key). Load your config with the_cfg_load_command, e.g_cfg_load gl_. Change the settings to suit your needs, and when you've done editing you'll need to save your config. This is done with the_cfg_save_command, e.g_cfg_save gl_.
## Step 3: Connecting to a server

Connecting to a server can be done in two ways. Either via the console or more easily through an server browser. You might already know a server IP that you got on IRC for example. To connect to the server through the console just type_connect [ip:port]_. If you don't specify a port it will try to use 27500, which is the standard port for QW servers. Most servers use 275xx as ports. Addresses that you have copied under Windows can be pasted with Ctrl+V in QW, so you don't have to type it manually all the time.

From here on you should be able to play QW on your own. We hope that you have a lot of fun and enjoy it. If you want to know more about QW, how it works and what can be done with it head over to our next section.
