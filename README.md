# TIAPortal
SCL

It's a program for paint cell. Project created in TIA Portal for PLC S7-1200. You can see instruction description below.

Equipment list:
M1-2 - Air handling unit motors
M3-4 - Exhaust motors
Gas burners
Y1 - Servo/Recirculation shutter (closed loop)
Y2 - Servo/Recirculation shutter (closed loop)
T1 - Temperature in the cell
Fire signal
Emergency Stop
Light

1. Coloring. The surface to be painted is heated, the composition is applied. Parts of the solvent evaporate.
2. Drying. The air is heated in the chamber with a constant intake of up to 15% of fresh air (manually adjustable). It is forbidden to exceed the temperature standards, otherwise it will lead to burning of the coating.

The operator presses "start painting program" on the screen of the painting process. The preparation phase begins: then the light turns on, the blinds Y1 and Y2 open. When the end positions of the shutters are reached, the units of exhaust and supply fans are sequentially started as a pair (M1+M3, M2+M4). After the engines reach operating speed, if the current temperature differs downward from the setpoint, a command is given to start the burners, the system starts to work in automatic mode, turning the burner on and off to maintain the set temperature. You can start coloring. At the end of the dyeing of the product, the operator must leave the chamber, close all the doors to the chamber, press the “End of painting” button, after which the program stops.

Next, you need to start the program by pressing the "Start Drying" button.
After pressing the "Start Drying" button, the light is switched off and the blinds Y1 and Y2 are closed. When the end positions of the blinds are reached, the exhaust fans stop, the supply fans continue to work, the temperature is set and maintained within the “drying” mode setting (conditional +80). The drying timer has a direct countdown that starts from the moment the program starts. The drying process can be stopped without waiting for the end of the timer using the "stop drying" button. After drying is completed, the drying purge mode begins.

Paint purge: shutters Y1 and Y2 are open, supply and exhaust fans are running, burners are on. The conditions for disabling the mode are: the temperature drops to the temperature set in the recipe (conditionally +20), or the temperature in the chamber (sensor T10) becomes <= temperature outside the chamber + - 2 degrees (sensor T11). If one of the conditions is met, the purge runs for about 3 more minutes and turns off.

Drying purge: shutters Y1 and Y2 are closed, only supply fans are running, burners are on. The conditions for disabling the mode are: the temperature drops to the temperature set in the recipe (conditionally +20), or the temperature in the chamber (sensor T10) becomes <= temperature outside the chamber + - 2 degrees (sensor T11). If one of the conditions is met, the purge runs for about 3 more minutes and turns off.

Block list:
- the burner cannot operate when the ventilation motors are switched off.
- when pressing the emergency stop button located on the control cabinet door, the burner and all fans are turned off, all processes and timers return to their original state.
- it is forbidden to start when the fire extinguishing system is turned off or the fire extinguishing sensor is triggered.
- when the fire extinguishing system sensor is triggered, all chamber nodes are turned off, the dampers move to the drying position, sealing the chamber (blinds Y1 and Y2 close), the light is on for 30 seconds and turns off.
- when the service doors and gates are open, it is impossible to start and work the drying process of the product.
- if during the operation of any of the types of programs an error is generated on the supply or ventilation device (frequency converter, one / both supply motors), then this device is turned off and a purge is started, which continues on the remaining equipment to preserve the integrity of the heat exchangers;
