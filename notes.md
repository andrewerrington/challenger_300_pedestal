# Notes for datarefs and actions in DDEN Challenger 300 flight simulator model for X-Plane 11

## APU
APU is a three position rotary switch, with 45° between positions. Left is latching, right is momentary.  
sim/cockpit/engine/APU_switch and  
sim/cockpit2/electrical/APU_starter_switch  
report the current state of the APU switch:  
0 - OFF  
1 - RUN  
2 - START  
Note: START is a momentary position as the knob springs back to RUN when released.

Command sim/electrical/APU_off turns the switch to OFF  
Command sim/electrical/APU_start turns the switch to START. When the command stops the switch reverts to the RUN position.  
**NB This is a continuous action and can not be activated by UDP commands.**


## SYSTEMS TEST
SYSTEMS TEST is an eight-position latching rotary switch, with 36° between positions, and a momentary switch function when pressed. The top position is OFF, and moving the rotary switch changes cl300/test_rot from 0 to 7:

0 - OFF  
1 - ANNUN A  
2 - ANNUN B  
3 - PROBES  
4 - STALL/RUD LIM  
5 - ICE DET  
6 - FIRE DET  
7 - TAWS  

To activate the test the switch must be pressed for a few seconds.

cl300/test_push = 1 - button is pressed  
cl300/test_push = 0 - button is not pressed  


## ENGINE
L STARTER and R STARTER are three position rotary switches, with 45° between positions. Centre is OFF, with momentary action to the left and right.  
cl300/en_starter_l and cl300/en_starter_r report the switch state, and can be set by writing to the dataref:  
0 - CRANK  
1 - OFF  
2 - START  

AUTO SYNC is a three-position latching rotary switch, with 45° between positions.  
sim/cockpit2/switches/jet_sync_mode reports the switch state, and can be set by writing to the dataref:  
0 - OFF  
1 - N1  
2 - N2

EVENT is not supported in the simulator, but is connected to an input in the simulator hardware.
