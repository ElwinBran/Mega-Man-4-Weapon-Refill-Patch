# Mega Man 4 Weapon Refill Patch
This patch for Mega Man 4 makes weapon energy refill upon death in the whole game. 
A detailed description can be found [on the RomHacking page of this hack](http://www.romhacking.net/hacks/4720/), as well as an alternative download link.
In this README you will find further information on how this patch was made and reference material.

## Tools
- [The FCEUX NES emulator](http://www.fceux.com/web/download.html), for disassembly, hex editing, memory viewing, testing and even breakppoints.
- [LunarIPS](https://www.romhacking.net/utilities/240/), to create a patch file.

## Process
The project was started off by looking up the values that required changing.
These were acquired by simply using the weapons in game and looking for changed values in the RAM afterwards.
It was required that the weapon refill happened only when the player died. It was found out that when the players health energy is refilled is a good point to insert the weapon refill code. Then the health energy value was found allong with code that changes it.
These offsets were found using a Memory breakpoint. 
Unlike previously patched Mega Man games did Mega Man 4 not have any free space to insert the code on.
The NES can swap 'ROM banks' at any time by calling the right Memory Mapper Controller Registers. This allows the CPU to access another part of the ROM effectively. 

After trying a bank switch when the health would refill, the problem became looking for a bank with free space, which proved to be easy. 
Because the bank switch code takes quite a number of byte, the original code had to be carefully ported partly to the new free space. 
Often it will be required to return to the original bank, but it turned out this was unnecessary for Mega Man 4. 

## References
In order to write the code a lot of knowledge was required. Here I list the sources specifically used for this project.
A big thanks for the people behind these to make 6502 programming more accessible.
- [An excellent reference for quickly looking up the value of an opcode.](https://www.masswerk.at/6502/6502_instruction_set.html)
- [Basic ROM information that was required to understand the mapper.](https://datacrystal.romhacking.net/wiki/Mega_Man_4)
- [This Question on the NesDev forum, the user Quietust made a post that really made me understand what I had to do to get the bank switch going.](https://forums.nesdev.com/viewtopic.php?t=17851)
