# Sonic 2 Optimized
_Sonic 2 Optimized_ is an updated version of the _Sonic 2_ game engine. Based on commit 2b066b4450ec6ff66b28a387a3e8211e710c4a05 of the community disassembly.

Note that as of writing that **there is no stable release**, therefore there is no confirmation that the game will work correctly. Download and use at your own discretion.

# Changes
## Gemeral
* Revision 02 is now the only version compiled, however any advantages that REV00/REV01 had (visible debug objects and less padding) have been backported over.
* V-blank routines are now called directly using a word-based jump, rather than a table.
* Ending sequence can now be skipped by pressing Start.

## Objects
* Changed `priority` to now directly point to the sprite queue, rather than being calculated. This considerably simplifies DisplaySprite, but also requires all objects to explicitly declare their priority value.
* Optimized the lost ring object to use a velocity table, rather than calculating it for every ring.
* Optimized the (unused) big ring object a little bit.
* Optimized most object move routines to take advantage of a quirk with the `movea.w` instruction.
* Applied miscellaneous smaller optimizations to various objects that provide slight performance boosts.

# Bug Fixes
## Major Fixes
* Fixed the game crashing when placing an object in debug mode after dying.
* Fixed multisprite objects using the wrong draw function. This also means they have the correct priority now.
* Fixed a rare crash that could occur with the ascending/descending metal platforms in Wing Fortress.

## Minor Fixes
* Fixed the title screen not having its priorities set correctly, causing various layering issues.
* Fixed Sonic's left hand disappearing for a single frame on the title screen.
* Fixed Sonic being able to clip into the first cave in Emerald Hill 2 (imported from _Sonic Jam_).
* Fixed Sonic being able to get stuck in the last cave in Emerald Hill 2 (imported from _Sonic Jam_).
* Fixed the leaf generators in Aquatic Ruin appearing when the player dies.
* Fixed Sonic being unable to use a loop in Aquatic Ruin 2 after getting to the area from below (imported from _Sonic Jam_).
* Fixed Sonic overlapping the hangable vines in Mystic Cave.
* Fixed the birds in the ending appearing in front of the Tornado, yet behind Sonic.
* Fixed the Special Stage animations not working correctly, meaning they now appear much smoother.
