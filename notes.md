# Notes for datarefs and actions in DDEN Challenger 300 flight simulator model for X-Plane 11

## APU
sim/cockpit/engine/APU_switch and  
sim/cockpit2/electrical/APU_starter_switch  
report the current state of the APU switch:  
0 - OFF  
1 - RUN  
2 - START  
Note: START is a temporary position as the knob springs back to RUN when released.

Command sim/electrical/APU_off turns the switch to OFF  
Command sim/electrical/APU_start turns the switch to START. When the command stops the switch reverts to the RUN position. NB This is a continuous action and can not be activated by UDP commands


## SYSTEMS TEST
Moving rotary switch changes cl300/test_rot from 0 to 7:

0 - OFF  
1 - ANNUN A  
2 - ANNUN B  
3 - PROBES  
4 - STALL/RUD LIM  
5 - ICE DET  
6 - FIRE DET  
7 - TAWS  

To activate test the switch must be pressed for a few seconds.

cl300/test_push = 1 - button is pressed  
cl300/test_push = 0 - button is not pressed  

