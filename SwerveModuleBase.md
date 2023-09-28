---
label: Swerve Module Base
order: 3
icon: package
---

# SwerveModuleBase - Represents a Swerve Module

## Class Summary
```java
SwerveModuleBase(Vec2d position, double steeringRatio, double driveRatio);
SwerveModuleBase(Vec2d position, double steeringRatio, double driveRatio, boolean optimized);
```
Self explanatory

## Usage
The base of everything quail (almost).

This class is designed to be inherited from. You need to override the `setAngle()` and `setRawSpeed` methods to set the module's angle and wheel velocity, respectively. You could also probably include a method to reset your module position (preferably using absolute encoders geared 1:1 with the module heading).

Make sure that you're accounting for your gear ratios. It is recommended that you configure `swerveDrive` call `set()` on all of your modules.
