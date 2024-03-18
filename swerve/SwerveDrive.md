---
label: Swerve Drive
order: 5
icon: squirrel
---

# Swerve Drive - Class For Your Swerve Drive

## Class Summary

```java
SwerveDrive(List<T> swerveModules);
```

## Usage

This class represents a swerve drive. It is designed to be **inherited from**; it will _technically_ work when not inherited from, but it is not recommended.

**You might want a few methods:**

- Reset gyro, both from controller and potentially vision
- Reset module positions (absolute encoders are amazing)
- Acceleration limiting (while walls are fun to hit, it is not recommended. May come soon to quail)

**Typical Usage:**

- Create a list of swerve modules that inherit from (`differentialSwerveModuleBase` or `swerveModuleBase`)
- Create a `swerveDrive` object with the list of the swerve modules
- every time you want to move, call `move()` with your desired movement vector and rotation speed
- Get the module vectors from the swerve module sensors and pass them into `swerveOdometry` or just use `TwoWheelLocalizer` if you like deadwheels

If for some reason you don't want to use `move()`, you can use `calculateMoveAngles` (see javadoc) and then normalize those vectors and pass them into the modules.
