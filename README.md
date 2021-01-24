# EasyGate1541

![](https://github.com/DL2DW/EasyGate1541/blob/main/Images/EasyGate1541.jpg)



EasyGate1541 is a replacement for the gate array (MOS 325572-01) of the Commodore disk drive VC1541. It completely replaces the chip in socket UC1.

I put the gate array into a CPLD from Xilinx (XC9572XL). Additionally I added LEDs. These are rather to be understood as a small gadget, since lines were still free. 



# Building

The board itself is quite simple in construction. It consists basically only of the CPLD, a voltage converter from 5V to 3.3V and the LEDs with series resistors, as well as the blocking capacitors.

The whole then in the dimensions of a 40pin DIP IC. Since everything was soldered on the back, the front is "clean".

![](https://github.com/DL2DW/EasyGate1541/blob/main/Images/EasyGate1541_Top.jpg)



The LEDs have been mounted on the bottom side. There are corresponding holes for this so that the LEDs can be seen from above.

The power LED is connected to the voltage converter. You can see whether the voltage converter is working.

The Clock LED is connected to the clock input and slowed down accordingly so that it flashes. If this LED does not blink, the clock coming from UF6 is probably missing.

Further there is a motor LED, which indicates when the motor is running, or should run. So the corresponding signal comes from VIA 6522.

And finally there is a Write LED, which always lights up when a write access takes place.

If you don't want these LEDs, you can simply omit them. They are not needed for operation.

![](https://github.com/DL2DW/EasyGate1541/blob/main/Images/EasyGate1541_Bottom.jpg)



Where which LED color is used, I leave to personal taste. As a "serving suggestion" I offer the following graphic, according to which I have provided the LEDs:



![](https://github.com/DL2DW/EasyGate1541/blob/main/Images/EasyGate1541_LEDs.jpg)



## Firmware flashing

The firmware is available as SVF, XSF and JED file and can be imported with a JTAG programmer. A simple SVF player is sufficient for this. I simply put the JTAG interface on the free unused PINs. These are not connected on the board of the 1541.

The easiest way is to put the whole thing on a breadboard and wire it up as follows:

| Pin  | Description |
| ---- | ----------- |
| 1    | +5V         |
| 7    | TDI         |
| 9    | TMS         |
| 11   | TCK         |
| 13   | VREF (3.3V) |
| 20   | GND         |
| 33   | TDO         |

The 5V is supplied via a power supply and then the JTAG interface is connected according to the above mentioned assignment. Then flash the SVF file and you are done.

After that the replacement chip can be plugged into the floppy.



For a better overview, here is an illustration of how to connect the whole thing on a breadboard:



![](https://github.com/DL2DW/EasyGate1541/blob/main/Images/EasyGate1541_JTAG.jpg)



The easiest and cheapest way to upload the firmware via JTAG is a FT232H module. This module is available at AliExpress for about $7. With this module and the software xc3sprog the JED file can be flashed very easily.

I recommend the following manual: https://github.com/1c3d1v3r/neatPLA/tree/master/programming

There you will also find the links to the xc3sporg software and the flashing procedure. The manual can also be used for the EasyGate1541. Only the connection of the FT232H module is different. And the JED file from my repository must be used.



# BOM

Except for the CPLD, comparison types can also be taken. 

| No#  | Designator | Part                            | Description                                |
| ---- | ---------- | ------------------------------- | ------------------------------------------ |
| 1    | U1         | MaxLinear SPX5205M5-L-3-3/TR    | Voltage regulator SOT-23-5                 |
| 2    | U2         | Xilinx XC9572XL-10VQG44C        | CPLD VQFP-44                               |
| 3    | D1         | Everlight 25-21/GHC-YSU/2A      | LED green, 1206                            |
| 4    | D2         | Everlight 25-21/BHC-XR2S1/2A    | LED blue, 1206                             |
| 5    | D3         | Everlight 25-21/T1D-ANQHY/2A    | LED white, 1206                            |
| 6    | D4         | Everlight 25-21SURC/S530-A4/TR8 | LED red, 1206                              |
| 7    | C1 - C3    | Kemet C0603C104J4RACTU          | Capacitor, 100nF, 16V, X7R, 0603           |
| 8    | C4, C5     | Kemet C0805C106J8RACAUTO        | Capacitor, 10µF, 10V, X7R, 0805            |
| 9    | R1 - R4    | Yageo SR0603FR-7T1KL            | Resistor, 1k, 1%, 1/4W, 0603               |
| 10   | CN1, CN2   | Mill-Max 800-10-020-10-002000   | Pin Header, 20pin, precision, Pitch 2.54mm |



# PCB

The PCB can either be ordered directly from [PCBWay](https://www.pcbway.com/project/shareproject/EasyGate1541.html), or you can create it yourself from the Gerber files available here.

[![PCBWay](https://www.pcbway.com/project/img/images/frompcbway.png)](https://www.pcbway.com/project/shareproject/EasyGate1541.html)




If you liked my project, I would be very happy about a small coffee donation.

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/R6R62T6RN)



# License

The contents of this repository is released under the following license:

- the "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License" (CC BY-NC-SA 4.0) full text of this license is included in the [LICENSE.CC-NC-BY-SA-4.0](https://github.com/DL2DW/EasyGate1541/blob/main/LICENSE.CC-NC-BY-SA) file and a copy can also be found at https://creativecommons.org/licenses/by-nc-sa/4.0/
