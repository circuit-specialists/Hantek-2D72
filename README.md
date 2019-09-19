# Hantek-2D72
 Hantek 2000 series, 2D72 firmware, tools, unbrick Hantek 2D72 and other information


## Parts:
    * MCU: STM32F103VET6 (100pin)
    * ADC: AD9288BSTZ-40
    * FPGA: LATTICE XO2-1200U
    * DAC: 3PD5651E
    * DMM (multimeter): CS7721CN-1
    * OU amplifier at the output of the generator (put different): EL5166, LMH6702

## Firmware Dump:
1. Download ST-Link Utility
2. Connect ST-Link V2 to [software debug ports](Software-Debug-Ports.jpg) on main circuit board (GND, SW_CLK, SW_DAT)
3. In ST-LINK Utility, specify Address: 0x08000000, with the size : 0x80000
4. Connect to Target, or press enter
5. Click save file button (File should be 512kB)

## AWG and DMM Hardware Mod:
fit DAC902 at position U12<br/>
remove R315<br/>
R63, R70 = 50 Ohms (R63 was already fitted in my device)<br/>
C70, C71 = 20 pF (C71 was already fitted in my device)<br/>
fit R65 = 560 Ohm<br/>
Change R61 from 1,78 kOhm to 2,2 kOhm as the AWG amplitude of my device was too high with the stock resistor<br/>

In the frontend section (see picture from reply #56):<br/>
fit EL5166<br/>
fit BAV99<br/>
change 0 Ohms resistor at the output of the OpAmp to 50 Ohms<br/>
change 0 Ohms resistor at pin 3 of OpAmp to 150 Ohms<br/>
change 0 Ohms feedback resistor (at OpAmp left side) to 560 Ohms<br/>
[Mod Picture](AWG-Mod.jpg)

## DFU Mode:
* Press F1 and power on the oscilloscope at the same time to enter the programming mode.<br/>
* Connect the oscilloscope to the computer and open the device manager of the computer.<br/>
* Find a new device and right click it to update the driver. The driver files are in this path: STMicroelectronics\Software\DfuSe v3.0.5\Bin\Driver.<br/>
* Open DfuSe Demo software, click "Choose" to select the firmware (***.dfu), and click "Upgrade" to update the firmware. After updated, click "Leave DFU mode" to exit the programming mode.