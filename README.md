# Indecisive John: Line Follower Robot

A slow but effective line-following robot built on a Raspberry Pi RP2040 with a 5-sensor Maker Line, programmed in simple, readable MicroPython. Nicknamed "Indecisive John" (the reason is explained in the Limitations section).

Indecisive John was built as a course project for Embedded Systems at Democritus University of Thrace to learn how sensors, motors and microcontrollers work together.

## Overview

The robot follows a dark line on a light surface. It reads five digital line sensors, decides which way the line is, and drives two DC motors to stay on it. The whole program is a single main.py file with small functions for each movement.

## Hardware:
- **Microcontroller**:Raspberry Pi Maker Pi RP2040 board 
- **Line sensor**:Maker Line
- **Chassis**: Smart Robot Car Chasis Kit
- **Motors**:2 DC motors
- **Motor Driver**:	Dual motor driver with direction pins (IN1-IN4) and PWM enable pins (ENA, ENB)

## How it works
1. **Read** the five sensors (leftmost,left,center,right,rightmost) in a loop.Each one is 1 or 0 depending on if it sees the line or not.
2. **Match** the five readings against a list of known patterns, for example "only the center sensor sees the line" or "the two left sensors see it".
3. **Act** by calling one of the movement functions:
  forward: both motors on, 40% speed
  turn_left / turn_right: pivot around one wheel, 30% speed
  sharp_left / sharp_right: same pivot at 60% speed
  stop: both motors off
4. **Stop** if no sensor sees the line, if all five see it, or if the pattern isn't one of the known cases.

Motor speed is set with PWM at 1 kHz, converting a 0 to 1 speed value into a 16-bit duty cycle.

<img width="271" height="530" alt="image" src="https://github.com/user-attachments/assets/085bbd34-5c14-40fa-a8a0-0c38a38c6250" />


## Getting started
1. Install MicroPython on the RP2040 ([official guide](https://www.raspberrypi.com/documentation/microcontrollers/micropython.html)).
2. Copy main.py to the board using Thonny or a similar tool.
3. Connect the sensors, motor driver and motors to the board.
4. Power the robot and place it on a track with a dark line on a light surface.

## Wiring
| Function | GPIO pins |
|----------|-----------|
| Line sensors (leftmost to rightmost) | 1, 2, 3, 4, 5 |

## What I learned:
- Reading different sensor inputs and turning them to motor commands on a microcontroller
- Controlling motor speed with PWM duty cycles.
- Splitting hardware control into small, reusable functions.
- The limits of a rule-based approach: every sensor pattern has to be handled by hand.

## Limitations:
This was my first course project in a subject i was completely new to,therefore has clear limitations that i would fix today.
  - **The nickname "Indecisive John":** the code handles only 17 of the 32 possible sensor patterns. Any other pattern falls through to stop, so the robot can halt when it loses the line.
  - **Better control:** weigh each sensor by its position, compute how far the line is from the center, and adjust the two wheel speeds in proportion (proportional or PID control) instead of using a fixed table of cases.
  (At the time i had tried and researched PID control, but abandoned the idea because it was beyond what i could implement then.
- **Recovery:** remember which side the line was last seen on, and steer back toward it when the line is lost.
- **Sharper turns:** The sharp turns aren’t sharp. sharp_left is the same as turn_left with a bigger speed number. Both just stop one wheel and pivot around it, and neither reverses a wheel.Drive the inner wheel backwards for tight turns instead of only stopping it.


## Author

*Nikos Flamourtzoglou, BSc Informatics, Democritus University of Thrace*
