JellyBOX 2
==========
- DEVICE
- name IMADE3D.JellyBOX2
- filament 1.75
- nozzle 0.4
- bed width 177
- bed depth 155
- max height 140
- extrusion absolute: false
- origin center: false

#### header = start gcode
```
;---------------------------------------
; ; ; Jellybox Start Script Begin ; ; ;
;_______________________________________
; for slicer: Kiri
; start gcode last modified Mar 28, 2019
G21               ;metric values
G90               ;absolute positioning
M107              ;start with the fan off
M117 Preparing    ;write Preparing
M190 S45          ;wait for the bed to reach 45C
M109 S180         ;wait for the extruder to reach 180C
G28               ;home all axes
G29 O             ;auto bed leveling procedure only if leveling NOT active
;M500              ;optionally save the mesh
G28 X             ;home x to get as far from the plate as possible
M420 S1           ;(re) enable bed leveling if turned off by the G28
G0 Y0 F5000       ;position Y in front
G0 Z15 F3000      ;position Z
M190 S{bed_temp} T{tool}              ;wait for the bed to reach desired temperature
M109 S{temp} T{tool}             ;wait for the extruder to reach desired temperature
; M300 S440 P300    ;play a tone
G4 P200           ;pause
; M0 Click to start print ; optional, recommended only with a rotary encoder
M117 Print starting   ;write Print starting
;================ ;PRINT:LINE start
G90               ;absolute positioning
M83               ;relative extrusion mode
G0 Z0             ;get Z down
G1 E18 F500       ;extrude __mm of feed stock
G1 E16 F400       ;extrude __mm of feed stock
G1 E8 F400       ;extrude __mm of feed stock
G4 S2             ;pause for ooze
M400              ;make sure all is finished
G0 F500 X3 Y0 Z0.6;get to the start of the LINE
G1 E2 F300        ;extrude __mm of feed stock
G1 F1000 X104 E10 ;print a thick LINE extruding __mm along the way
G92 E0            ;reset the extruder position
;---------------------------------------------
; ; ; Jellybox Printer Start Script End ; ; ;
;_____________________________________________
```
#### footer = end gcode
```
;---------------------------------
;;; Jellybox End Script Begin ;;;
;_________________________________
; end gcode last modified Nov 30, 2018
M117 Finishing Up ;write Finishing Up
M107        ;turn the fan off
M104 S0     ;extruder heater off
M140 S0     ;bed heater off (if you have it)
G91         ;relative positioning (includes extruder)
G1 E-1 F2500 ;retract the filament a bit before lifting the nozzle to release some of the pressure
G1 Z0.5 E-4 X-10 F9000 ;get out and retract filament even more
G1 E-25 F2500 ;retract even more
G90         ;absolute positioning (includes extruder)
G28 X       ;home X so the head is out of the way
G1 Y140     ;move Y forward, so the print is more accessible
M84         ;steppers off
M117 Print finished ;write Print finished
;---------------------------------------
;;; Jellybox End Script End ;;;
;_______________________________________
```

JellyBOX Original
================
- DEVICE
- name IMADE3D.JellyBOX.Original
- filament 1.75
- nozzle 0.4
- bed width 170
- bed depth 145
- max height 140
- extrusion absolute: false
- origin center: false

#### ! HEADER/ FOOTER (= START/ END) gcodes are the same as JellyBOX 2 above