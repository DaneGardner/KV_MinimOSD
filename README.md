I've forked the project because I wanted to add some things that don't really belong in the main repository.  I'm making them public so I have somewhere to keep my code (yay GitHub!), and in the hopes that someone else finds my modifications useful.

This has been forked from v2.3 of the KV Team OSD project from https://code.google.com/p/rush-osd-development/


Watchdog Timer
==============
I kept having brownouts during flight, despite an addition of a heavy capacitor on the board.  The problem was that the program would go into a locked up state and I'd lose all OSD information, though I still had video.  I realized that there needed to be a way to restart the OSD quickly when this happened, so I added code to use the watchdog timer.  When the processor hangs, it won't update the WDT, and it will be reset within a 250 milliseconds.  If the flight controller is already armed, it will also skip the long splash screen at the beginning, and go straight into displaying data.

To use the watchdog timer features, you'll have to reflash the Atmega328 chip with a new bootloader that supports the WDT.  See the hex file in the bootloader folder for a precompiled one.

To disable, remove the preprocessor define for WATCHDOG in the Config.h file (it's on by default here).


Fast MAX7456 Chip Initialization
================================
I realized that there are a lot of stepped manual delays in the initialization code for the OSD chip, which made a WDT reset horrendously slow.  I trimmed the fat a bit on the timing, and have seen no ill effects.  To disable, remove the preprocessor define for FASTINIT in the Config.h file.
