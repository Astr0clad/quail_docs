---
label: Path Follower
order: 1
icon: goal
---

# PathFollower - It Follows Paths

## Class Summary
```java
SwerveModuleBase(Localizer localizer, path path, double speed, double maxTurnSpeed, double maxTurnAcceleration, double maxAcceleration, MiniPID turnController, double precision);
```
Self explanatory

## Usage
This one is simple for once. Give the class what it needs. Make sure you aren't trying to turn right at 999deg/s unless your drivetrain supports it. PID is also really cool, it allows you to actually turn accurately, you should tune that. Precision is kinda important, decide how precise you want to be :D

To set a new path, use `setPath()`. You can calculate the next movement each loop cycle using `calculateNextDriveMovement()`, it returns a robotMovement that you can feed into `swerveDrive.move()`. The path is (hopefully) completed when the `isFinished()` method returns true. We do try to make your life easier sometimes. You could also go off the rails and do something else with it if you want, but that's not recommended. The method also deals with getting the pose from your localizer of choice, so that's nice.