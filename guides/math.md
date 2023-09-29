---
label: Math
order: -1
icon: code-square
---

# Math

## Terminology:
- Forwards kinematics: determining the robot's position based on the module angles and speeds
- Reverse kinematics: determining the module angles and speeds based on a desired robot movement
- Module state: the module's angle and speed (vector)
- Module position: the module's position relative to the robot's center of rotation
- Robot position: the robot's position relative to the field

## Reverse Kinematics (general)
From a desired robot movement (Δ position), we can calculate the module states for each module.

To do so, we begin with the translation component of the desired robot movement, vector *R<sub>G</sub>* (movement of robot relative to the ground).

Translation, each module vector, *m<sub>i</sub>* is equal to the robot's movement relative to the ground (*m<sub>i<sub>G</sub></sub>*) plus the module's movement relative to the robot of rotation (*m<sub>i<sub>R</sub></sub>*).

*m<sub>i</sub>* = *m<sub>i<sub>G</sub></sub>* + *m<sub>i<sub>R</sub></sub>*

It should then follow that *m<sub>i<sub>R</sub></sub>* can be calculated easily:
- its angle must be perpendicular to the module's position vector
- its magnitude is equal to the robot's rotation speed times the module's distance from the center of rotation

### Reverse Kinematics (Differential Swerve)

With differential swerve, the module's angular velocity is equal to the sum of the two motor velocities, and the module's linear velocity is equal to the difference of the two motor velocities.

- *V<sub>A</sub>* = *V<sub>m1</sub>* + *V<sub>m2</sub>*

- *V<sub>L</sub>* = *V<sub>m1</sub>* - *V<sub>m2</sub>*

However, this does not account for gear ratios. Accounting for gear ratios, we get:

- *R<sub>A</sub>* *V<sub>A</sub>* = *V<sub>m1</sub>* + *V<sub>m2</sub>* 

- *R<sub>L</sub></sub>* *V<sub>L</sub>* = *V<sub>m1</sub>* - *V<sub>m2</sub>*

Where *R<sub>A</sub>* and *R<sub>L</sub>* are the angular and linear gear ratios, respectively.

A simple manipulation gives:

- *V<sub>m1</sub>* = (*R<sub>A</sub>* *V<sub>A</sub>* + *R<sub>L</sub>* *V<sub>L</sub>*) / 2
- *V<sub>m2</sub>* = (*R<sub>A</sub>* *V<sub>A</sub>* - *R<sub>L</sub>* *V<sub>L</sub>*) / 2

## Forwards Kinematics (general)

## Forwards Kinematics (Differential Swerve)

