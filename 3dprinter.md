
## UBL Bed leveling
- http://marlinfw.org/docs/features/unified_bed_leveling.html

## Z Axis Sensor offset
> [M851](http://marlinfw.org/docs/gcode/M851.html) - Z Probe Offset

> [M211](http://marlinfw.org/docs/gcode/M211.html) - Software Endstops
```
M851 Z0;
G28;
G1 Z0;
M211 S0;	// This will disable the end stops so that you 
         	// will be able to proceed lower than Z=0
```          

Now adjust Z height to fit a piece of paper and note the negative Z height
(either through the LCD or through an application over USB)
```
M851 Z-1.23
M500
M211 S1		// Enable the end stops again
```

Extruder Motor steps for Gear ratio (maybe M8)
> [M92](http://marlinfw.org/docs/gcode/M092.html) - Set Axis Steps per unit 
```
M92 E152.0
```


## G Code for EEPROM
- [M500](http://marlinfw.org/docs/gcode/M500.html) - Save Settings
- [M501](http://marlinfw.org/docs/gcode/M501.html) - Load Settings
- [M502](http://marlinfw.org/docs/gcode/M502.html) - Factory Reset
- [M503](http://marlinfw.org/docs/gcode/M503.html) - Report Settings

## G Code for PID Auto tune
- [M303](http://marlinfw.org/docs/gcode/M303.html) - PID Autotune
- [M301](http://marlinfw.org/docs/gcode/M301.html) - Set Hotend PID
- [M304](http://marlinfw.org/docs/gcode/M304.html) - Set Bed PID
```
M303 E<Extruder> S<temperature> C<cycles>
```
HOTEND PID Auto Tune command:
```
M303 E0 S240 C3
```
BED PID Auto Tune Command:
```
M303 E-1 S80 C8
```

```
M301 P27.33 I2.19 D85.07
M304 P391.46 I29.14 D1314.83
```
```
M500;	// Save
M503;	// Report
```
```
HotEnd PID Autotune Result
	P 27.33
	I 2.19
	D 85.07
```
```
Bed PID Autotune Result
	P 391.46
	I 29.14
	D 1314.83
```
## Marlin G-Code
[G-Code list](http://marlinfw.org/meta/gcode/)
