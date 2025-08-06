# Sonic 2 Rewritten
_Sonic 2 Rewritten_ is an updated version of the _Sonic 2_ game engine. Based on commit 2b066b4450ec6ff66b28a387a3e8211e710c4a05 of the community disassembly.

Note that as of writing that **there is no stable release**, therefore there is no confirmation that the game will work correctly. Download and use at your own discretion.

# Changes
## General
* Revision 02 is now the only version compiled, however any advantages that REV00/REV01 had (visible debug objects and less padding) have been backported over.
* V-blank routines are now called directly using a word-based jump, rather than a table.
* Added the ability to change characters on the level select, just like in _Sonic 3 & Knuckles_.
* Ending sequence can now be skipped by pressing Start.
* Restored the original PLC queue speed from _Sonic 1_ (slightly improves load times).
* Applied layout changes introduced in _Knuckles in Sonic 2_.

## Players
* `move_lock`, `invulnerable_time`, `invincibility_time`, and `speedshoes_time` are now handled as a byte each, rather than a word, which frees up **$32-$35** in the player SST to compensate for the loss of **$1F-$21**.
* Changed `interact` to now directly point to the object Sonic and Tails are interacting with, which slightly improves performance.

## Objects
* Changed `priority` to now directly point to the sprite queue, rather than being calculated. This considerably simplifies DisplaySprite, but also requires all objects to explicitly declare their priority value.
* Optimized the lost ring object to use a velocity table, rather than calculating it for every ring.
* Optimized the (unused) big ring object a little bit.
* Optimized most object move routines to take advantage of a quirk with the `movea.w` instruction.
* Applied miscellaneous smaller optimizations to various objects that provide slight performance boosts.

## Sound
* Restored higher quality drum and SEGA samples from _Sonic 1_.
* Improved the sound-queuing system to not be as intensive with stopping the Z80.

# Bug Fixes
## Major Fixes
* Fixed the game crashing when placing an object in debug mode after dying.
* Fixed multisprite objects using the wrong draw function. This also means they have the correct priority now.
* Fixed some rare crashes that could occur with the Chemical Plant boss.
* Fixed a rare crash that could occur with the Hill Top boss.
* Fixed some pressure switches in Oil Ocean 2 using invalid subtypes, which could cause problems if the code is significantly rewritten.
* Fixed a rare crash that could occur with the Oil Ocean boss.
* Fixed a rare crash that could occur with the Metropolis boss.
* Fixed a rare crash that could occur with the ascending/descending metal platforms in Wing Fortress.

## Minor Fixes
* Fixed the SEGA chant being at the wrong pitch.
* Fixed the title screen not having its priorities set correctly, causing various layering issues.
* Fixed Sonic's left hand disappearing for a single frame on the title screen.
* Fixed the GAME/TIME OVER text flickering for a single frame.
* Fixed many misplaced objects and rings, it is now possible to get a perfect bonus in every stage.
* Fixed Sonic getting stuck on bridges if he enters debug mode while standing on them.
* Fixed Sonic being able to clip into the first cave in Emerald Hill 2 (imported from _Sonic Jam_).
* Fixed Sonic being able to get stuck in the last cave in Emerald Hill 2 (imported from _Sonic Jam_).
* Fixed the Chemical Plant boss not spewing out smoke when it is defeated.
* Fixed the leaf generators in Aquatic Ruin appearing when the player dies.
* Fixed Sonic being unable to use a loop in Aquatic Ruin 2 after getting to the area from below (imported from _Sonic Jam_).
* Fixed the Casino Night boss behaving strangely after hitting them for the first time.
* Fixed Sonic overlapping the hangable vines in Mystic Cave.
* Fixed the balloons in the Metropolis boss not bursting after hitting the player until they touch the floor once.
* Made the balloons pop in the Metropolis boss when defeated (technically not a bugfix, but it prevents the sprite limit from being overloaded in the results, also _Sonic 3 & Knuckles_ does this as well for its throwback boss).
* Fixed the clouds in the ending popping into existence on the right side of the screen.
* Fixed the birds in the ending appearing in front of the Tornado, yet behind Sonic.
* Fixed the Special Stage animations not working correctly, meaning they now appear much smoother.

# Special Thanks
* Aurora - optimizations ported from _AMPS in Sonic 2_; **do not attempt to contact this user**
* [Devon](https://github.com/Ralakimus) - _Sonic Jam_ object data
* [Hivebrain](https://github.com/cvghivebrain/Sonic1sq) - optimizations and fixes ported from _Sonic 1 Squared_
* Mercury - bridge debug mode fix
* RedhotSonic - ring loss optimization, Sonic 3K priority manager
* [RetroKoH](https://github.com/RetroKoH/S1Fixed) - optimizations and fixes ported from _S1Fixed_
* Everyone who has contributed to the thread "some changes and fixes for _Sonic 2_", this game is extremely buggy
