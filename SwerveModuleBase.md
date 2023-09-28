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

Don't be stupid, use this class. It's a good class. It's a class that does things. It's a class that does things that you need to do. It's a class that does things that you need to do to make your robot move. It's a class that does things that you need to do to make your robot move with a swerve drive. It's a class that does things that you need to do to make your robot move with a swerve drive with a swerve module.

This class is designed to be inhertied from. You should probably override the `setAngle()` and `setRawSpeed` methods to do things. You could also probably include an `X-Lock` to prevent things from happening (TODO in the library), a method to reset your module position (absolute encoders are amazing, use them).

You should also probably use `set()` to specify the modules specified vector. Try to do as much as you can in your extension of this class, it'll make your life easier. Deal with your motors and/or servos from here (FTC moment) and make sure that you're accounting for your drive and steering ratios. PID is also useful for pod heading, but you can do whatever you want. Writing walls of text is fun, but continuing on, you should really consider using `swerveDrive` to deal with calling `set()` on all of your modules.