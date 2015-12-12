StepperDriver
=============

Arduino library for controlling stepper motors via a driver board.
Currently supported: <a href="https://www.pololu.com/product/2134">DRV8834</a> Low-Voltage Stepper Motor Driver
Future plans for: <a href="https://www.pololu.com/product/1182">A4988</a> and
<a href="https://www.pololu.com/product/2131">DRV8825</a>.

Motors
======

4-wire bipolar stepper motor or 6-wire unipolar in 4-wire configuration (leaving centers out).

Connections
===========

Minimal configuration from <a href="https://www.pololu.com/product/2134">Pololu DRV8834 page</a>:

<img src="https://a.pololu-files.com/picture/0J4344.600.png">

Wiring
======

- Arduino to driver board:
    - DIR - A8
    - STEP - A9
    - M0 - A10
    - M1 - A11
    - SLEEP - 3.3V
    - GND - Arduino GND
    - GND - Motor power GND
    - VMOT - Motor power 2.5-10.8V (for DRV8834)

- driver board to motor (this varies from motor to motor, check motor coils schematic).
  I just list the motor wires counter-clockwise
    - A1 - RED
    - A2 - GRN
    - B1 - YEL
    - B2 - BLU 

- 47uF capacitor between GND - VMOT 
- 470K resistor from GND - M0 (without this, modes that put M0 in high-impedance do not work)

- Set the max current on the driver board to the motor limit.
- Have a motor power supply that can deliver that current.

Set Max Current
===============

The max current is set via the potentiometer on board.
Turn it while measuring voltage at the passthrough next to it.
Needed voltage = 0.5 * max current(A). For example, for 1A you will set it to 0.5V.
This is based on this formula V = I*5*R where I=max current, R=0.1ohm (as installed on Pololu board).

Code
====

See the BasicStepperDriver example for a generic driver that should work with any board
supporting the DIR/STEP indexing mode.

The Microstepping example works with a DRV8834 board.

Hardware
========
- Arduino-compatible board
- A <a href="https://www.pololu.com/category/120/stepper-motor-drivers">stepper motor driver</a>, for example DRV8834, DRV8825, DRV8824, A4988.
- A <a href="http://www.circuitspecialists.com/stepper-motor">Stepper Motor</a>.
- 1 x 100-470K resistor
- 1 x 47uF capacitor

