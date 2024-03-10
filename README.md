# MSX Mouse PS2 Adapter

## Introduction

The MSX Mouse PS2 Adapter is a  device that integrates a PS/2 mouse into an MSX computer, supporting both MSX-mouse and MSX-joystick modes. 
Powered by the Atmel ATTiny2313 microcontroller and clocked at 8 MHz using the built-in oscillator, this adapter brings modern mouse functionality to 
the classic MSX platform.

Based on the work/schema developed by Caro in 2009. http://www.caro.su/msx/mous4msx.htm

![MSX Mouse PS2 Adapter](/images/2024-03-10_17-17.png)

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

![Open Hardware](images/ccans.png)

This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).

* If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
* You may not use the material for commercial purposes.
* You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

**ATTENTION**

This project was made for the retro community and not for commercial purposes. So only retro hardware forums and individual people can build this project.

THE SALE OF ANY PART OF THIS PROJECT WITHOUT EXPRESS AUTHORIZATION IS PROHIBITED!