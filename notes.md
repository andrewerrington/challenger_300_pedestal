# Notes for datarefs and actions in DDEN Challenger 300 flight simulator model for X-Plane 11

## APU
APU is a three position rotary switch, with 45° between positions. Left is latching, right is momentary.  
`sim/cockpit/engine/APU_switch` and  
`sim/cockpit2/electrical/APU_starter_switch`  
report the current state of the APU switch:  
0 - OFF  
1 - RUN  
2 - START  
Note: START is a momentary position as the knob springs back to RUN when released.

Command `sim/electrical/APU_off` turns the switch to OFF  
Command `sim/electrical/APU_start` turns the switch to START. When the command stops the switch reverts to the RUN position.  
**NB This is a continuous action and can not be activated by UDP commands. It must be started with XPLMCommandBegin and ended with XPLMCommandEnd, usually via a PlugIn function.**


## SYSTEMS TEST
SYSTEMS TEST is an eight-position latching rotary switch, with 36° between positions, and a momentary switch function when pressed. The top position is OFF, and moving the rotary switch changes `cl300/test_rot` from 0 to 7:

0 - OFF  
1 - ANNUN A  
2 - ANNUN B  
3 - PROBES  
4 - STALL/RUD LIM  
5 - ICE DET  
6 - FIRE DET  
7 - TAWS  

`cl300/test_push` reports the switch state, and can be changed by writing to the dataref. To activate the test the switch must be pressed for a few seconds.
1 - button is pressed  
0 - button is not pressed  


## ENGINE
All buttons except IGNITION and MACH HOLD have covers over them. In the simulator they can not be pressed without lifting the covers. In software, the button
state can be altered by writing to the dataref regardless of the state of the cover.

L ENGINE FIRE
R ENGINE FIRE
`cl300/fire_engn_l_h` and `cl300/fire_engn_l_h`  
  
0 - OFF  
1 - FIRE  

`cl300/fire_engn_l` and `cl300/fire_engn_r` is the brightness of the indicator LED in the button (showing "FIRE")


APU FIRE
`cl300/fire_apu_h`
  
0 - OFF  
1 - FIRE  

`cl300/fire_apu` is the brightness of the indicator LED in the button (showing "FIRE")


FIRE EXT 1 & 2
`cl300/fire_ext_1_h` and `cl300/fire_ext_2_h`  
  
0 - OFF  
1 - ARMED 

`cl300/fire_ext_1` and `cl300/fire_ext_2` is the brightness of the indicator LED in the button (showing "ARMED")


AUTO APR
`cl300/fire_autoapr_h`
  
0 - OFF  
1 - ON  

`cl300/fire_autoapr` is the brightness of the indicator LED in the button (showing "OFF"). It is lit when `cl300/fire_autoapr_h` is 0.  


MACH HOLD
`cl300/engn_mach_h`

0 - OFF  
1 - ON  

`cl300/engn_mach` is the brightness of the indicator LED in the button (showing "ON").  


IGNITION
`cl300/engn_ign_h`

0 - OFF  
1 - ON  

`cl300/engn_ign` is the brightness of the indicator LED in the button (showing "ON").  


L STARTER and R STARTER are three position rotary switches, with 45° between positions. Centre is OFF, with momentary action to the left and right.  
`cl300/en_starter_l` and `cl300/en_starter_r` report the switch state, and can be set by writing to the dataref:  
0 - CRANK  
1 - OFF  
2 - START  

AUTO SYNC is a three-position latching rotary switch, with 45° between positions.  
sim/cockpit2/switches/jet_sync_mode reports the switch state, and can be set by writing to the dataref:  
0 - OFF  
1 - N1  
2 - N2

EVENT is not supported in the simulator, but is connected to an input in the simulator hardware.


