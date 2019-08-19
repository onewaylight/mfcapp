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
