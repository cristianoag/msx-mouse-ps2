# msx-mouse-ps2
MSX Mouse PS2 Adapter

## Introduction

This adapter connects to any of the joystick ports in a MSX computer and enables the use of an PS/2 mouse in MSX-mouse or MSX-joystick modes. The adapter is based on the Atmel ATTiny2313 microcontroller. Clocked by  the built-in 8 MHz oscillator.

## Bill of Materials

[To be included]

## Firmware and Basic Operation

The current firmware version allows the adapter to work in mouse or joystick emulation mode. You can program the the ATTiny2313 using the MSX. To do that, set the JP1 to the "prog" position (pins 1-2 closed). 
In In the "work" position (pins 2-3 are closed), the MCU works in mouse or joystick emulation mode. A JP2 jumper is provided to control the mouse resolution (which is necessary when working with modern 
high-resolution optical mice).

To switch the operation mode, press both mouse buttons, left and right, at the same time. The current mode is displayed Led. If it's lit - the adapter is mouse mode, otherwise it is operating in joystick mode. 
When the power is turned on, by default, the adapter operates in mouse mode - (LED is on). If it blinks with a period of about 1 second, it means either the mouse is not connected, or it is not working, or the mouse 
connected via a USB<>PS/2 adapter does not work in PS/2 mode.

## Programming the ATTiny2313

The prg2313t.com tool was designed for programming or updating the firmware of the ATMEL ATTiny2313 microcontroller, installed in the MSX mouse adapter, which is plugged into one of its joystick ports. 
Before running the program, you need to set the JP1 jumper on the controller board to the "prog" position. 

By default, the program sets the FUSES bits for it to work with a built-in oscillator at 8 MHz.

`prg2313t [file.hex]`

file.hex is the name of the file containing the firmware in Intel-HEX format.


If there is no adapter connected to any of the joystick ports, you will see the following error:

```
Error: CHIP is not found on any joystick port: 1 RESET <-: STROBE (Joy-8pin) 17 MOSI <-: TrgA (Joy-6pin) 18 MISO ->: Up (Joy-1pin) 19 SCK <-: TrgB (Joy-7pin) 20 VDD <-: +5V (Joy-5pin) 10 GND : GND (Joy-9pin)
```
The numbers on the left are the pin numbers of the microcontroller.

 If a controller is connected to one of the joystick ports, a message is displayed about the number of the port to which it is connected and the following are read from the MCU:

```
Signature (branded 3-byte identifier of the MC);
Current FUSES values;
Current MK firmware.
```

