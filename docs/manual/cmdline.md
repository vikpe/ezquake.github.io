---
layout: default
tab: Documentation
---

# ezQuake Manual - Command line
(automatic conversion from internal help - last edited Tue 07-Oct-2003)

## Command line


_For command line configuration use a program called ezstart.exe_. QW can of course be started by simply doubleclicking on the executable, but there are a few command line parameters which should be used to make QW run even better and which can sometimes solve problems as well. The easiest way is to create a shortcut or even better a batch (.bat) file for starting QW. The most important command line parameters are described below:

- **-width xxx and -height xxx** These set the video resolution (by default software QW will start in 320x200 and gl QW in 640x480). To see all the resolutions your graphic board supports you have to type "vid_describemodes" at the console. The modes available depend on your type of board, driver version and your systems ram.
- **-bpp 32** This will start QW with 32 bit colors. When running software QW you should set it to 8.
- **-heapsize [x]** This allocates the given amount of ram to QW in bytes. By default QW won't take more than 16mb of ram but when you have more than 32mb system ram you should force it to take more since the more ram it can use the less hd (and sometimes video or sound) lag you will have.
- **-dinput** Turning directinput on will make your mouse movement much smoother.
- **-zone 8192** This increases your keys and message memory buffer from default of 48kb to 8192kb. Your keys will respond much better.
- **-window** When you put this in front of the -width and -height command it might solve some problems you might have with certain video modes. QW does not run in a window but even lower resolutions will be a bit slower than usually.
- **-dibonly** This command often solves problems that occur with software QW in combination with modern GeForce graphic cards, like screen turning black when quitting QW or the colors on the desktop look wrong.

## So your QW starting command line could look something like this then:

ezquake-gl.exe -noscripts -ruleset smackdown -heapsize 81920 -zone 8192 -sndbits 16 -sndspeed 48000 -dinput -m_smooth -bpp 16 -width 640 -conwidth 640 +set vid_displayfrequency 85 +set s_khz 44

There are a few more commands which are not commonly used. For an explanation on those refer to the Quake and QW readme files.
