## UBL Bed leveling
- http://marlinfw.org/docs/features/unified_bed_leveling.html

```
;------------------------------------------
;--- Setup and initial probing commands ---
;------------------------------------------
M502            ; Reset settings to configuration defaults...
M500            ; ...and Save to EEPROM. Use this on a new install.
M501            ; Read back in the saved EEPROM.  
```

-----------------------------------------
###### After initialize eeprom, must be set these parameters for use TMC2100 drivers
-----------------------------------------

## Must be set these parameter first.

Acceleration and Jerk value

Acceleration default value is 
Default: 3000 
Change to : 800

Jerk default value is
Default: 15
Change to : 7

### Set Acceleration 
```
M201 X800 Y800 T8400
M500
```

### Set Jerk
```
M205 X7 Y7 T7
M500
```

### Continu Test Procedures
;-----------------------------------------
;
;-----------------------------------------

```
M190 S65        ; Not required, but having the printer at temperature helps accuracy
M104 S210       ; Not required, but having the printer at temperature helps accuracy

G28             ; Home XYZ.
G29 P1          ; Do automated probing of the bed.
G29 P2 B T      ; Manual probing of locations USUALLY NOT NEEDED!!!!
G29 P3 T        ; Repeat until all mesh points are filled in.

G29 T           ; View the Z compensation values.
G29 S1          ; Save UBL mesh points to EEPROM.
G29 F 10.0      ; Set Fade Height for correction at 10.0 mm.
G29 A           ; Activate the UBL System.
M500            ; Save current setup. WARNING: UBL will be active at power up, before any `G28`.

;----------------------------------------------------
;--- Use 3-point probe to transform a stored mesh ---
;----------------------------------------------------
G29 L1          ; Load the mesh stored in slot 1 (from G29 S1)
G29 J           ; No size specified on the J option tells G29 to probe the specified 3 points
                ; and tilt the mesh according to what it finds.
```

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

## Check Status
> [M119](http://marlinfw.org/docs/gcode/M119.html) - Endstop States

## Marlin G-Code
[G-Code list](http://marlinfw.org/meta/gcode/)
