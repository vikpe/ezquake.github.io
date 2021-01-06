---
layout: default
tab: Documentation
---

## Colored text

###### (this topic was ported quickly from old documentation and needs updated)

ezQuake supports setting the color of text in strings. This is often used to make certain elements stand out in team messages.

First you need to set `/scr_coloredText 1`.

Then you can type colored text. The syntax is "{&cRGBtext&r}" where R is a hexadecimal number in range of 0,1,...,E,F specifying amount of red in the resulting color. Same is G for green and B for blue. E.g. '888' is gray, 'f0f' is pink.

Note: values of those numbers get expanded to RRGGBB format so e.g. color '04f' can be found as color #0044FF in most graphics editors.

### White text

Inside braces, text defaults to white.  &cfff should correspond to white but is interpretted as a special code for colored text off (equivalent of &r)

Example:

- `/say "{&cff0this text will be yellow}, {&cfff}this will be the default orange {and this will be white text}"`

Note: The color of the text depends on the console font you use. Most console fonts have white letters. This client mixes the resulting color from these letters. If your standard console font color is not white, you might get different results.

Due to backward compatibility issues, colored text is not allowed to be used in the player's name.

Examples

- `{&c0b0safe&cfff}` equivalent with `{&c0b0safe&r}`
- `{&cf00enemy&cfff}` `{&c04fquad&cfff}`
