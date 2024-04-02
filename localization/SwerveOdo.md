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

Instantiate a new `swerveOdometry` object with the module positions of your swerve drive. You can also pass in a `swerveDrive` object to get the position vectors from that.

### Usage

Use `calculateOdometry()` and `calculateFastOdometry()` with the module vectors (obtained from the encoders on the modules). Use this to `updateOdometryDelta()` after scaling by your looptime and rotates.

### Example

```java
swerveOdometry odometry = new swerveOdometry(new Vec2d[] {
    new Vec2d(0.5, 0.5),
    new Vec2d(-0.5, 0.5),
    new Vec2d(-0.5, -0.5),
    new Vec2d(0.5, -0.5)
});

// ...

void loop() {
    Vec2d velocity = odometry.calculateFastOdometry(new Vec2d[] {
        new Vec2d(module1.getVelocity(), module1.getAngle()),
        new Vec2d(module2.getVelocity(), module2.getAngle()),
        new Vec2d(module3.getVelocity(), module3.getAngle()),
        new Vec2d(module4.getVelocity(), module4.getAngle())
    });
    newVelocity = velocity.scale(looptime).rotate(gyroAngle);
    odometry.upddateDelta(newVelocity);
}
```
!!!warning
`calculateFastOdometry()` only works if your modules are in a regular geometric shape. If they are, it is much faster than `calculateOdometry()`.
!!!
