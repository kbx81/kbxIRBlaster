# kbx IR Blaster

## What?

Just another ESP32-based IR Blaster. It was designed with
 [ESPHome](https://esphome.io) in mind but should work fine with
 [Tasmota](https://tasmota.github.io/docs/) or any other app, really.

## Why?

After trying this on a perfboard with parts I had laying around, I wanted
 something more polished. I found
 [Sparkfun's IR Blaster](https://www.sparkfun.com/products/15031) which is
 quite nice and clean but I quickly realized that its IR output is somewhat
 weak and would only work if pointed _directly_ at the device it was intended
 to control. Rather than hack it up, I chose to draw up my own version of such
 a thing. I made it substantially more powerful so it can "light up a room"
 with infrared light; that is, you'll probably find that it works well even
 when it is not aimed directly at (if even near) devices you wish to control
 with it. It also uses an ESP32 module instead of an ESP8266. The ESP32 has
 dedicated hardware for IR data transmission (the RMT) which makes it somewhat
 more suitable for this purpose, despite that it is otherwise quite overkill.

## How?

Please see the [BoM](kbxIrBlaster.BoM.md) for a list of parts needed to build
 one. I had the PCBs fabricated by [Elecrow](https://www.elecrow.com) but
 nearly any PCB fabricator should be able to manufacture these without any
 issues.

The schematic and PCB were drawn in [KiCAD](https://www.kicad-pcb.org).

The PCB has on the bottom side a number of solder jumpers that enable each of
 the four FET drivers to be connected to one of two possible GPIO pins. This
 allows a single GPIO pin to control all four of them simultaneously or they
 can be broken apart onto separate GPIO pins. Labels on the underside of the
 PCB indicate what jumpers are connected where.

_Note that the solder jumpers **must be bridged** one way or the other; if this
 is not done, the FETs (and consequently the LEDs they drive) will not activate!_
 When you build one, be sure to complete this step or you'll be left in the
 dark. (Punny, I know.)

An FS1000A (such as
 [this one](https://www.amazon.com/HiLetgo-Wireless-Transmitter-Receiver-Raspberry/dp/B01DKC2EY4/))
 or similar 433 MHz transmitter module may be connected to J2 allowing the
 device to double as an RF remote controller. Bridge JP6 to enable this and
 then connect the module to pins 4, 5, and 6 on J2. When doing so, be sure to
 orient the module correctly or tragedy may result.

 ## Legal stuff and License

The circuit schematics and PCB found here are licensed under the
 [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

![Creative Commons License badge](https://i.creativecommons.org/l/by-sa/4.0/88x31.png)

_Happy building!_