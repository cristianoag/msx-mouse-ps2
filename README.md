# MSX Mouse PS2 Adapter

## Introduction

The MSX Mouse PS2 Adapter is a  device that integrates a PS/2 mouse into an MSX computer, supporting both MSX-mouse and MSX-joystick modes. 
Powered by the Atmel ATTiny2313 microcontroller and clocked at 8 MHz using the built-in oscillator, this adapter brings modern mouse functionality to 
the classic MSX platform.

Based on the work/schema developed by Caro in 2009. http://www.caro.su/msx/mous4msx.htm

## Bill of Materials

[To be included]

## Firmware and Basic Operation

The current firmware version enables the adapter to function in mouse or joystick emulation mode. Programming the ATTiny2313 is achieved through the MSX by setting the JP1 jumper to the "prog" position (pins 1-2 closed). 
In the "work" position (pins 2-3 closed), the MCU operates in mouse or joystick emulation mode. A JP2 jumper is provided to adjust the mouse resolution, particularly useful when using modern high-resolution optical mice.

To toggle between operation modes, simultaneously press both mouse buttons (left and right). 
The current mode is indicated by an LED: lit for mouse mode, unlit for joystick mode. 
Upon power-up, the default mode is mouse mode (LED is on). A blinking LED with a one-second period signals issues such as an unconnected mouse, a malfunctioning mouse, or a USB<>PS/2 adapter-related problem.

## Programming the ATTiny2313

To program or update the firmware of the Atmel ATTiny2313 microcontroller in the MSX mouse adapter, utilize the prg2313t.com tool. Before running the program, set the JP1 jumper on the controller board to the "prog" position.

The tool, designed for Intel-HEX formatted firmware, sets the FUSES bits for an 8 MHz built-in oscillator.

```bash
prg2313t [file.hex]
```

Ensure that the adapter is connected to a joystick port. In case of an unconnected adapter, an error message is displayed:

```
Error: CHIP is not found on any joystick port: 1 RESET <-: STROBE (Joy-8pin) 17 MOSI <-: TrgA (Joy-6pin) 18 MISO ->: Up (Joy-1pin) 19 SCK <-: TrgB (Joy-7pin) 20 VDD <-: +5V (Joy-5pin) 10 GND : GND (Joy-9pin)
```

For a connected controller, the tool provides information about the connected port, including:

- Signature (branded 3-byte identifier of the MCU)
- Current FUSES values
- Current MK firmware

## License

![open hardware](/images/1024px-Open-source-hardware-logo.svg.png)

This work is licensed under the CERN OHL-S v2. You may redistribute and modify this project and its documentation under the terms of the CERN-OHL-S v2.

This project is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY, INCLUDING OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A PARTICULAR PURPOSE. Please see the CERN-OHL-S v2 for applicable conditions.

Based on the original work developed by Caro in 2009.  http://www.caro.su/msx/mous4msx.htm

You should have received a copy of the CERN-OHL-S along with this project. If not, see <https://ohwr.org/project/cernohl/wikis/Documents/CERN-OHL-version-2>.