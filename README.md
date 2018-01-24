# FreeRTOS_on_RPi

This provides a very basic port of FreeRTOS to Raspberry pi.


first of all Build RaspberryPi-FreeRTOS-master.

Howto Build
Type make! -- If you get an error then:

$ cd RaspberryPi-FreeRTOS-master
$ cd .dbuild/pretty
$ chmod +x *.py
Currently the makefile expect an arm-none-eabi- toolchain in the path. Either export the path to yours or modify the TOOLCHAIN variable in dbuild.config.mk file.

You may also need to modify the library locations in the Makefile:

kernel.elf: LDFLAGS += -L"c:/yagarto/lib/gcc/arm-none-eabi/4.7.1/" -lgcc
kernel.elf: LDFLAGS += -L"c:/yagarto/arm-none-eabi/lib/" -lc
The build system also expects find your python interpreter by using /usr/bin/env python, if this doesn't work you will get problems.

To resolve this, modify the #! lines in the .dbuild/pretty/*.py files.

and now you can test your FreeRTOS step by step according to blow: 

install rt-tests packege.
to do this enter blow commands: 

$ cd ../rt-tests
$ make all

and then you can trace your OS's latency with mklatencyplot.bash script and see the ploted results

$ ./mklatencyplot.bash
Hope this helps.

I'm currently porting my BitThunder project to the Pi, which is a OS based on FreeRTOS but with a comprehensive driver model, and file-systems etc.

http://github.com/jameswalmsley/bitthunder/

James
