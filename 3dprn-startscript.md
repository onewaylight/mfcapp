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
G92 E0 ; reset extruder

G1 Z1.0 F3000 ; lift Z
G1 X10.2 Y25 Z0.2 F5000.0 ; move to start-line position
G1 X10.2 Y150.0 F1500.0 E10 ; draw 1st line
G1 X10.7 Y150.0 F5000.0 ; move to side 0.5mm
G1 X10.7 Y25 F1500.0 E20 ; draw 2nd line
G92 E0
G1 Z2.0
;G1 X10.7 Y25 F5000.0 ; quick wipe
;M117 Printing...
; Done purge extruder 
;G1 Z1.0 F1000 ; move z up little to prevent scratching of surface
M117 Happy Printing
```



; Custom Start G-code on Cura
M104 S{material_print_temperature_layer_0} ; Set Extruder temperature
M140 S{material_bed_temperature_layer_0} ; Set Heat Bed temperature
M190 S{material_bed_temperature_layer_0} ; Wait for Heat Bed temperature
M109 S{material_print_temperature_layer_0} ; Wait for Extruder temperature
G28 ; Home all axes
M117 Purge extruder
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
G1 X0.1 Y20 Z0.3 F5000.0 ; Move to start position
G1 X0.1 Y200.0 Z0.3 F1500.0 E15 ; Draw the first line
G1 X0.4 Y200.0 Z0.3 F5000.0 ; Move to side a little
G1 X0.4 Y20 Z0.3 F1500.0 E30 ; Draw the second line
G92 E0 ; Reset Extruder
G1 Z2.0 F3000 ; Move Z Axis up little to prevent scratching of Heat Bed
M117 By your command!
; End of custom start GCode
