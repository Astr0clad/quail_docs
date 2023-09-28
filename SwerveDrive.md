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
Where swerveModules is a list of swerve modules. Crazy, right?

## Usage
**This one is fun**

Obviously, this class represents a swerve drive. It is designed to be **inherited from**, it will *technically* when not inherited from, but it is not recommended.

**You might want a few methods:**
- Reset gyro, both from controller and potentially vision (not recommended)
- Reset module positions (absolute encoders are amazing)
- Acceleration limiting (while walls are fun to hit, it is not recommended. May come soon to quail)

**Typical Usage:**
- Create a list of swerve modules that inherit from (`differentialSwerveModuleBase` or `swerveModuleBase`)
- Create a `swerveDrive` object with the list of the swerve modules
- every time you want to move, call `move()` with your desired movement vector and rotation speed
- Get the module vectors from the swerve module sensors and pass them into `swerveOdometry` or just use `TwoWheelLocalizer` if you like deadwheels

You should be able to skip the last step if using `move()`, it will normalize the vectors for you.

If for some reason you don't want to use `move()`, you can make your life harder and use `calculateMoveAngles` (see javadoc) and then normalize those vectors and pass them into the modules.
