# Software

There are two softwares that will be necessary for all users. Arduino - to load, or flash, data onto the
microcontroller, and a printing software. The printing software our team uses is Ultimaker Cura, if the
printer you buy is incompatible with Cura, use whatever specific printing software your machine suggests.
If you choose to use a different microcontroller system, you may also need a different flashing environment,
but that is outside of the scope of this guide.

First, download Arduino 1.8.18. This is a legacy release but in order to use the correct data 
format, SPIFFS, you must use Arduino 1.8. SPIFFS has not yet been implemented in the 2.x version of Arduino. If this is changed in Arduino IDE, 
IoTWX will adapt accordingly.

Additionally you will need Ultimaker Cura (or a different 3d printing software)
to work with and edit the 3d files. 
You will need to edit them if you have special circumstances for 
your station site or you are using a different printer than the one we suggest. 
Our gcode files (instructions for the 3d printing) are calibrated with our printer, the Ender 3 S1,
and are too fickle to be worth sharing.

### Download pages:
[Arduino IDE](https://www.arduino.cc/en/software) (Scroll down until 'Legacy IDE')

[Ultimaker Cura](https://ultimaker.com/software/ultimaker-cura/#links)

