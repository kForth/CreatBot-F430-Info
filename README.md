# [CreatBot F430 Information](#creatbot-f430-information)

## [Firmware](#firmware)

### [Printer](#printer-firmware)

The CreatBot firmware is a custom version of the popular Marlin firmware.
Our F430 shipped with CreatBot Firmware v5.5, based off of Marlin v1.1.6.

The F430 is currently running a custom version of CreatBot Firmware v5.6, the original source code was acquired from CreatBot.
This custom version isn't fully set up and you currently can't move the print head with the LCD interface.

Source code for the unmodified v5.6 firmware can be found here:
https://github.com/kForth/Marlin/tree/Creatbot-v5.6

Source code for the modified version in-use can be found here: 
https://github.com/kForth/Marlin/tree/Creatbot-v5.6-Modified

Source code for the unmodified v6.1 firmware can be found here:
https://github.com/kForth/Marlin/tree/Creatbot-v6.1

### [LCD](#lcd-firmware)

The CreatBot F430 LCD panel uses a precompiled [DGUS](http://www.ampdisplay.com/documents/pdf/DWIN%20DGUS%20DEV%20GUIDE_V40_2014.pdf) firmware, it is not easily changed.

The printer firmware ends/receives button events and field values rather than drawings the screens itself.

Helpful links:
- https://github.com/andrivet/ADVi3pp
- https://github.com/Desuuuu/DGUS-reloaded
- http://www.ampdisplay.com/documents/pdf/DWIN%20DGUS%20DEV%20GUIDE_V40_2014.pdf

## [Hardware](#hardware)

### [Hot Ends](#hot-ends)
The CreatBot F430 has two hot ends, one low-temp and one high-temp.

The hot ends can use any standard MK8 nozzle with a 5mm thread length.

Low-Temp Hot Ends Specs:
- Block Material: Aluminum
- Nozzle Material: Brass
- Max Temperature: 260°C
- Heater: 40?W
- Sensor: Marlin option "-1" => "Thermocouple with AD595" (Actually uses an AD597)

High-Temp Hot Ends Specs:
- Block Material: Brass
- Nozzle Material: Steel
- Max Temperature: 420°C
- Heater: 40?W
- Sensor: Marlin option "-1" => "Thermocouple with AD595" (Actually uses an AD597)

The two hot ends share a cooling fan, the fan is a blower-style fan with a split duct routing the airflow to both nozzles.

### [Heated Bed](#heated-bed)
The CreatBot F430 uses a 350?W silicone rubber heater to heat the printer bed.
The heater is controlled by a Single Phase Solid State Relay:
<!-- - [Product Link](https://www.aliexpress.com/item/1005001315733171.html) -->
- Part Number:      MGR-1 DD220D25
- Load Current： 	25A
- Control Voltage： 3-32VDC
- Load Voltage： 	5-220VDC
- Control Current： DC3-25mA
- On voltage： 	    ≤2V
- Off Leakage Current：≤2mA
- On-Off Time： 	 ≤10ms
- Insulation Resistance ： 	 1000M/500VDC
- Ambient Temperature 	 -30~75 C

The heater is powered by a MeanWell LRS-350-24 power supply:
- Datasheet: https://www.meanwell.com/productPdf.aspx?i=459
- 350W, 14.6A @ 24VDC Output

The heated bed uses a thermistor:
- Marlin option 1 -> "100k Thermistor - best choice for EPCOS 100k (4.7k pullup)"

### [Heated Chamber](#heated-chamber)
The CreatBot F430 uses two ?W heaters to heat the build volume.

The heaters are powered directly by the 120VAC input.

The heaters are controller by two 30A SAL-12VDC-SL-A relays:
- Datasheet: https://datasheet.lcsc.com/lcsc/1811151537_Ningbo-Songle-Relay-SLA-12VDC-SL-A_C55194.pdf

The heated chamber uses a thermistor:
- Marlin option 1 -> "100k Thermistor - best choice for EPCOS 100k (4.7k pullup)"

## [Electronics](#electronics)

### [Motherboard](#motherboard)

This F430 motherboard is version 9.2.3, the pcb is green in colour.

The motherboard pcb also has the following markings:
- 9.2.2 2016/09/19 PM
- 9.2.3 2017/04/22 AM

The motherboard is powered by a MeanWell LRS-150-24 power supply:
- 150W, 6.5A @ 24VDC Output
- Datasheet: https://www.meanwell.com/productPdf.aspx?i=420
- Output is connected to large capacitor bank.

The motherboard uses ? stepper drivers.

### [Extruders](#extruders)
The CreatBot F430 has two extruders, one for each hot end. There is a left and right hand version of the extruder.

The extruders are similar to the MK8 extruder design.

The extruders each have a filament runout sensor and a stepper cooling fan.

### [Stepper Motors](#stepper-motors)

#### Stepper Motor Info
| Axis | # Motors |   Driver |             Model # |   Frame | Length | Phase Current |
|:----:|---------:|---------:|--------------------:|--------:|-------:|--------------:|
|  X   |        1 |  TMC2100 | 42HS48-1304JA05-D24 | NEMA 17 |  48 mm |         1.3 A | RMS Current Limit 1.3A (1.8A Peak): Vref = 1.83V for TMC2100
|  Y   |        1 | THB6032S |  42HS63-1504A05-D21 | NEMA 17 |  63 mm |         1.5 A | 
|  Z   |        1 | THB6032S |  42HS63-1504A05-D21 | NEMA 17 |  63 mm |         1.5 A | 
|  E   |        2 | THB6032S |  42HS34-1204A05-D11 | NEMA 17 |  34 mm |         1.2 A | 

#### Steps Per MM
| Axis |  Orignal |    Tuned |
|:----:|---------:|---------:|
|  X   |  78.7402 |  78.6878 |
|  Y   | 131.2336 | 131.0226 |
|  Z   | 640.0000 | 639.7246 |
|  E   | 130.0000 | 130.0000 |

See https://www.thingiverse.com/thing:2484766 thingiverse page for info on how these were tuned.

### [Leveling Probe](#leveling-probe)
The CreatBot F430 uses a knock-off BLTouch probe.
- Knock-Off: https://www.aliexpress.com/item/4000465085766.html
- Genuine: https://www.antclabs.com/bltouch-v3

The genuine probe does not seem to work with the printer.

The knock-off probes can be drilled out to use the replacement pins from the genuine probe.

### [LCD Panel](#lcd-panel)
The CreatBot F430 uses a Touchscreen DGUS LCD panel:
- Model: [DMT48270M043_02WT](https://www.aliexpress.com/item/32815821437.html)
- Resolution: 480 x 272
- Touchscreen: Resistive
