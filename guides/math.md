---
label: Math
order: -1
icon: code-square
---

# Math

Explanations for how the math works.
You don't need to know this to use the library, but it might help you understand what's going on.

## Terminology:

- Forwards kinematics: determining the robot's position based on the module angles and speeds
- Reverse kinematics: determining the module angles and speeds based on a desired robot movement
- Module state: the module's angle and speed (vector)
- Module position: the module's position relative to the robot's center of rotation
- Robot position: the robot's position relative to the field

## Reverse Kinematics (drivetrain)

From a desired robot movement (Δ position), we can calculate the module state for each module.

To do so, we begin with the translation component of the desired robot movement, vector _R<sub>G</sub>_ (movement of robot relative to the ground).

For translation, each module state, _m<sub>i</sub>_, is equal to the robot's movement relative to the ground (_m<sub>i<sub>G</sub></sub>_) plus the module's movement relative to the robot of rotation (_m<sub>i<sub>R</sub></sub>_).

_m<sub>i</sub>_ = _m<sub>i<sub>G</sub></sub>_ + _m<sub>i<sub>R</sub></sub>_

It should then follow that _m<sub>i<sub>R</sub></sub>_ can be calculated easily:

- its angle must be perpendicular to the module's position vector
- its magnitude is equal to the robot's rotation speed times the module's distance from the center of rotation

### Reverse Kinematics (differential swerve)

**_Please note that in some differential swerve setups one motor's rotation is reversed, which will require inversion of its veocity and position_**

With differential swerve, the module's angular velocity is equal to the sum of the two motor velocities, and the module's linear velocity is equal to the difference of the two motor velocities.

- _V<sub>A</sub>_ = _V<sub>m1</sub>_ + _V<sub>m2</sub>_

- _V<sub>L</sub>_ = _V<sub>m1</sub>_ - _V<sub>m2</sub>_

However, this does not account for gear ratios. Accounting for gear ratios, we get:

- _R<sub>A</sub>_ _V<sub>A</sub>_ = _V<sub>m1</sub>_ + _V<sub>m2</sub>_

- _R<sub>L</sub></sub>_ _V<sub>L</sub>_ = _V<sub>m1</sub>_ - _V<sub>m2</sub>_

Where _R<sub>A</sub>_ and _R<sub>L</sub>_ are the angular and linear gear ratios, respectively.

A simple manipulation gives:

- _V<sub>m1</sub>_ = (_R<sub>A</sub>_ _V<sub>A</sub>_ + _R<sub>L</sub>_ _V<sub>L</sub>_) / 2
- _V<sub>m2</sub>_ = (_R<sub>A</sub>_ _V<sub>A</sub>_ - _R<sub>L</sub>_ _V<sub>L</sub>_) / 2

## Forwards Kinematics (drivetrain)

This method involves taking velocity vectors from each module, and combining that information with the module positions to obtain the robot velocity, which can then be integrated to find a delta position.

### The fast way

If your modules are in a shape such that their average position is the center of the robot, then you can use this method.

"average modules position in center of robot" means one of the following:

- your modules are in a geometric regular shape (square, regular pentagon, equilateral triangle, straight line with robot center bisecting it)
- the sum of the module position vectors is zero (rectangle and some other shapes meet this requirement)

Because the rotation vector of each module will cancel out, the robot
velocity will be equal to the average of the module velocities.

### The slow (but more flexible) way

What happens if your modules do not meet the above requirements?
This code has been implemented into quail, but the math behind it is
rather complex.

coming soon™

## Forwards Kinematics (sifferential swerve per-module)

**_Please note that in some differential swerve setups one motor's rotation is reversed, which will require inversion of its veocity and position_**

Knowing the distance that a module has traveled is not very useful. If you find a use for it, it can be calculated in a similar method as follows.

The _angular_ distance that a module has traveled--its angle relative to its starting position--_is_ useful.

To calculate angular distance, we can begin with the equation for differential swerve module angular velocity:

- _R<sub>A</sub>_ _V<sub>A</sub>_ = _V<sub>m1</sub>_ + _V<sub>m2</sub>_

_R<sub>A</sub>_ is a constant, so we can integrate both sides with respect to time to get:

- _R<sub>A</sub>_ _θ<sub>A</sub>_ = _θ<sub>m1</sub>_ + _θ<sub>m2</sub>_ + _C_

Where _Δ<sub>A</sub>_ is the angule of the module, _θ<sub>m1</sub>_ and _θ<sub>m2</sub>_ are the angles of the motors, and C is the initial position of the module.

This calculation is usually not as precise as using an absolute encoder (due to backlash) but is generally good enough.
