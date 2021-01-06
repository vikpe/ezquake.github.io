---
layout: default
tab: Manual
---

## Changelist for 3.2.2

### Changes
- `/gl_outline 1` supported again in `thunderdome` ruleset, by request of Thunderdome tournament organiser VVD.
- Higher number of lightmaps supported to help with some Team Fortress maps

### Bugfixes
- `/demo_jump` would cause multiple entries in the itemsclock (reported by Milton)
- `/tp_loadloc 0` invalidated by mvd-stats code always running & loading loc files
- Loading corrupt .wav files could lead to buffer overrun

### Other
- Compiles with -fno-common flag (default on newer versions of gcc)
- FreeBSD change to support 64-bit systems (?) - patch supplied by VVD
