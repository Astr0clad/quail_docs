---
label: Swerve Odometry
order: 0
icon: issue-draft
---

# Swerve Odometry - A Swerve Drive Odometry Class

### Class Summary
```java
swerveOdometry(Vec2d[] moduleVectors)
swerveOdometry(List<Vec2d> moduleVectors)
swerveOdometry(swerveDrive drivetrain)
```
You should probably give it what it wants. Using the swerveDrive constructor is recommended.

### Usage
Just do it™ - Nike. Use `calculateOdometry()` and `calculateFastOdometry` with the module vectors (current angle and current velocity). Use this to `updateOdometryDelta()`.

`calculateFastOdometry` only works if your modules are in a regular geometric shape

If you want to, you can get module vectors using `extractModuleVectors()` and pass in the `swerveDrive`.
