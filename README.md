This is a demonstration of a side-scroller involving a character that can run and jump around. It was started a while back as a college project, but was eventually abandoned. I decided to put the source online after fixing some bugs and other issues, in case anybody finds it useful. The code is not the cleanest ever, but can be freely used as a basis for other projects. If you do decide to use any of the code, please share a link. Bug fixes/improvements are also welcome.

Project Organization
--------------------

`boot.a` is the main assembly file and includes all other files.


Sprites
-------
Individual sprites are in `sprites/*.SPR` -- they are in C64 file format(i.e. 2 origin bytes at the beginning of the file) and can be loaded by the sprite editor.
These sprites are all compiled into a single file, `sprites/gamesprites.spr` which is included in the assembly file. See `sprite_info.a` to see descriptions.

`sprite_info.a` contains info about sprite sequences and offsets.


Tools
-----

[DASM](http://sourceforge.net/projects/dasm-dillon/) 2.20.11 20140304 - Assembler
C1541 (included with [VICE](http://vice-emu.sourceforge.net/) emulator) - .D64 manipulation tool
[SpriteWorld](http://csdb.dk/release/?id=31201) - sprite editor

