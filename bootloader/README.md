to build: ```make atmega328```

To flash: ```avrdude.exe -vvvv -patmega328p -cusbasp -Pusb -Uflash:w:ATmegaBOOT_168_atmega328.hex:i -Ulock:w:0x0F:m```
