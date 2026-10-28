Undecisive John: Line Follower Robot

A slow but effective line-following robot built with a Raspberry Pi RP2040 and a Maker Line sensor, programmed in simple, easy-to-understand MicroPython.

Overview

Undecisive John was built as a course project for Embedded Systems at Democritus University of Thrace to learn how sensors, motors and microcontrollers work together.

Hardware
Microcontroller:Raspberry Pi Maker Pi RP2040 board 
Line sensor:Maker Line
Chassis: Smart Robot Car Chasis Kit
How it works
Read the Maker Line sensor to see where the line is under the robot.
Decide which way to steer:
Drive the motors to correct the robot's position, then repeat in a loop.

<img width="271" height="530" alt="image" src="https://github.com/user-attachments/assets/085bbd34-5c14-40fa-a8a0-0c38a38c6250" />


Getting started
Install MicroPython on the RP2040 (official guide).
Copy main.py to the board using Thonny or a similar tool.
Wire the sensor and motors as shown in the wiring section below.
Power the robot and place it on a track with a dark line on a light surface.
Wiring

[Add a photo or table of which pins connect to which parts.]

What I learned
[Example: reading sensor input and turning it into motor control]
[Example: tuning speed against reliability]
[Anything that went wrong and how you fixed it]
Possible improvements
[Example: smoother steering with PID control]
[Example: speed adjustment on curves]
Author

Nikos Flamourtzoglou, BSc Informatics, Democritus University of Thrace
