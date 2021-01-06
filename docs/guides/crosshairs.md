---
layout: default
tab: Documentation
---

## Crosshairs

###### (this topic was ported quickly from old documentation and needs updated)

##### Crosshair format

You can use a builtin crosshair using `/crosshair x` where x is beteeen 2 and 6. `/crosshair 1` will use the + symbol from your charset.

##### Custom Crosshair Symbol

"crosshair 1" uses the plus symbol from your charset. Like all characters in your charset, the plus symbol is an 8x8 image in your charset. If you change this image, "crosshair 1" will change.

This client gives you the option of changing what "crosshair 1" looks like without editing your charset. To do this create a file called "crosshair.txt" in c:\quake\ezquake\crosshairs\crosshair.txt (change c:\quake to your quake dir).

The format of "crosshair.txt" is

    XOOOOOXO
    OXXOXXOO
    OXOOOXOO
    OOOXOOOO
    OXOOOXOO
    OXXOXXOO
    XOOOOOXO
    OOOOOOOO

where

    X (or x)     draw a pixel
    O (or o)     dont draw a pixel

##### Crosshair Colour

You change the colour of your crosshair with "crosshaircolor x" where x is 0..255.

##### Crosshair Size

You can change the size of your crosshair with "crosshairsize x".

You can use "crosshairsize x" where x is any number between 0.2 and 8. Even decimals work. Note however that some values will distort the crosshair in GL. This is because of conwidth and width (conheight and height) being different. Change crosshairsize slowly (by 0.05 at a time say) to find a 'sweet spot'. You get best performance when width (height) is an integral multiple of conwidth (conheight).

Crosshair size is independent of conwidth and conheight. Also if you wish to sue large crosshairs (using crosshairsize 10 etc) then its best to make a high resolution crosshair PNG image rather than using the 8x8 inbuilt crosshairs.

##### Crosshair Alpha

`/crosshairalpha x` where x is 0..1 will determine the level of transparency of your crosshair.

##### Crosshair Images

You can use a PNG/TGA/PCX image as your crosshair. The image should be placed in c:\quake\ezquake\crosshairs\ (except change c:\quake as needed).

To load the crosshair use `/crosshairimage image_name` where 'image_name' is the name of the crosshair image you put in the above directory.

To unload the crosshair use `/crosshairimage ""` in the console, or make an alias `/alias unload_crosshair crosshairimage $qt$qt` ($qt is the macro for ").

The variables `/crosshairsize`, `/crosshairalpha` and `/crosshaircolor` all work for crosshair images too (although sometimes you might not want color to work).

##### Making Crosshair Images

Firstly pick a size. The image should be square and preferabely have width and height being a power of 2. 64x64 is a good example.

The problem with powers of 2 is that there is no middle pixel. For example if you have a 64x64 image with top left pixel coordinates (1,1) and bottom right coordinates (64,64), then the middle is at (32.5, 32.5) which isn't a real coordinate. (32,32) and (33,33) are the two real coordinates closest to the middle. The client centres the 64x64 crosshair so that the (32,32) pixel is centred on screen. In otherwords (32,32) is treated as the centre.

In general if you have a crosshair image of width = height = 2\^n with top left coordinate (1,1) and top right coordinate (2\^n, 2\^n) then the centre of the crosshair should be positioned over pixel (2\^(n-1), 2\^(n-1)).
