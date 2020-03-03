```
G90
M82
M106 S0
G21 ; Metric Value
M107 ; Turn Off FAN
M140 S65
M104 S210
G28 ; Home All Axis
M107 ; Turn Off FAN
G29 L1;
;G29 J
G1 Z15 F200 ; Move the platform down 15mm
G92 E0      ; zero the extruded 
```

```
G21 ; Metric Value
M107 ; Turn Off FAN
M140 S[bed0_temperature]
M104 S[extruder0_temperature]
G28 ; home all axes
G29 L1
;G29 J
; Wait for all used extruders to reach temperature
G1 Z2 // Protect bed for Nozzle High Temperature during waiting
M109 S[extruder0_temperature]
M117 Purge Extruder
;G92 E0
G1 Z1.0 F3000 ; lift Z
G1 X10.2 Y25 Z0.2 F3000.0 ; move to start-line position
G92 E0 ; reset extruder
G1 X10.2 Y150.0 F1000.0 E15 ; draw 1st line
G1 X10.7 Y150.0 F3000.0 ; move to side 0.5mm
G1 X10.7 Y50 F1000.0 E30 ; draw 2nd line
G1 X10.7 Y25 F5000.0 ; quick wipe
;M117 Printing...
; Done purge extruder 
;G1 Z1.0 F1000 ; move z up little to prevent scratching of surface
M117 Happy Printing
```
