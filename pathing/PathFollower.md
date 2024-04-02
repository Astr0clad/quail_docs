---
label: Path Follower
order: 1
icon: goal
---

# PathFollower - It Follows Paths

## Class Summary
```java
PathFollower(Localizer localizer, Path path, double speed, double maxTurnSpeed, double maxTurnAcceleration, double maxAcceleration, MiniPID turnController, double precision);

PathFollower(Localizer localizer, double speed, double maxTurnSpeed, double maxTurnAcceleration double maxAcceleration, MiniPID turnController, double precision);
```
Follows paths.

## Usage
Make sure you aren't trying to turn right at 999deg/s unless your drivetrain supports it. PID is also really cool but needs to be tuned.

To set a new path, use `setPath()`. You can calculate the next movement each loop cycle using `calculateNextDriveMovement()`, it returns a robotMovement that you can feed into `swerveDrive.move()`. The path is (hopefully) completed when the `isFinished()` method returns true. We do try to make your life easier sometimes. You could also go off the rails and do something else with it if you want, but that's not recommended. The method also deals with getting the pose from your localizer of choice, so that's nice.
