# tangnano9k-vectrex
Tang Nano 9K top level module for vectrex

## Overview
- Top level module for Tang Nano 9K and circuit diagram of peripheral circuits.
- Created by modifying the DE10-lite source found in [SourceForge DarFPGA](https://sourceforge.net/projects/darfpga/files/Software%20VHDL/vectrex/).
- As stated in the README.TXT of the original package, please understand the following before using:
   - Educational use only
   - Do not redistribute synthetized files with roms
   - Do not redistribute roms whatever the form
   - Use at your own risk

## How to compile
1. Expand vhdl_vectrex_rev_0_2_2018_06_12.zip in [SourceForge DarFPGA](https://sourceforge.net/projects/darfpga/files/Software%20VHDL/vectrex/).
2. Copy the contents of the extracted folder below to vectrex_project/src/.
```
cp -a rtl_dar rtl_jkent rtl_mikej rtl_pace vectrex_project/src/
```
3. Prepare a vhdl file of ROM data, create a rom folder and put it there.
```
mkdir vectrex_project/src/rom
cp vectrex_exec_prom.vhd vectrex_project/src/rom/ (required)
cp vectrex_scramble_prom.vhd vectrex_project/src/rom/ (example of game ROM data)
```
4. Open the project vectrex_project.gprj with Gowin EDA and build it.
(Add or delete ROM data files to/from the project as appropriate.)

## About ROM data
- Obtain necessary ROM data in some way and create a vhdl file according to README.TXT included in the original package.
- Modify rtl_dar/vectrex.vhd appropriately according to the rom name and size. (How to do it is written in the comments of the source.)

## Peripheral circuits
- VGA output, audio output, key input
It worked with the circuit [hardware/tangnano9k-vectrex-peri-schematics.pdf](hardware/tangnano9k-vectrex-peri-schematics.pdf).
- This is not a recommended circuit because I just made it using parts that I happened to have on hand.
- I used the 74HC541 at 3.3V for the VGA signal buffer, but maybe I should use a part that considers the input level and output level properly.
- You might need resistors (150 ohms?) for RGB signals.
- Maybe VGA can be output to HDMI and sound can be output from there, but I have no knowledge about it, so I haven't tried it.

## Other
- 27MHz clock is used as 25MHz. It might be better to make a 25MHz clock with Tang Nano's PLL. (I don't know how to use PLL and I don't want to use IP, so I'm using 27MHz clock.)
- This project is just an attempt to practice using FPGA, so there are no plans to maintain it even if there are bugs.
- This readme was translated from the [Japanese original](README.jp.md) using Google Translate.