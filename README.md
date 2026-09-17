# FPGA Mouse Click Counter

A VHDL application for the Nexys A7 FPGA board that counts mouse-button clicks and displays the result on the board's seven-segment display. It was developed as a two-person university Digital Systems Design project.

## Features

- Left click increments the counter.
- Right click decrements the counter.
- A switch reverses the left/right behaviour.
- An enable switch holds the current value when disabled.
- The centre button resets the counter.
- The counter wraps between `0` and `255`.
- An LED indicates whether left click is currently assigned to increment.

## Hardware

- Digilent Nexys A7 FPGA board
- USB mouse connected to the board's USB HID host port
- On-board switches, centre button, LED, and seven-segment display

The Nexys A7's auxiliary microcontroller presents compatible USB mouse input to the FPGA through a PS/2-style clock and data interface.

## Project structure

```text
.
|-- constraints/
|   `-- Nexys-A7.xdc
|-- docs/
|   `-- FPGA and mouse application.pdf
|-- src/
|   |-- HexTo7Segm.vhd
|   |-- MPG.vhd
|   |-- UpDownCounter.vhd
|   `-- main.vhd
|-- third_party/
|   `-- digilent/
|       |-- MouseCTL.vhd
|       |-- PS2Interface.vhd
|       `-- README.md
|-- .gitignore
`-- README.md
```

## Controls

| Board control | Function |
| --- | --- |
| `SW0` | Reverse left/right click functions |
| `SW1` | Enable counter updates |
| Centre button | Reset counter to zero |
| `LED0` | Left click is assigned to increment |
| Seven-segment display | Current counter value |

## Open in Vivado

1. Create a Vivado RTL project targeting the Nexys A7 board.
2. Add all VHDL files from `src/` and `third_party/digilent/` as design sources.
3. Set `src/main.vhd` as the top-level module.
4. Add `constraints/Nexys-A7.xdc` as the constraints file.
5. Run synthesis, implementation, and bitstream generation.
6. Program the board and connect a USB mouse to its HID host port.

The original project report contains the system diagrams, protocol explanation, and user manual: [FPGA and mouse application](docs/FPGA%20and%20mouse%20application.pdf).

## Third-party modules

The PS/2 interface and mouse-controller modules are based on Digilent code. Their original copyright headers are preserved under `third_party/digilent/`.

