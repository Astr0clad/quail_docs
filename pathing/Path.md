---
label: Path
order: 2
icon: milestone
---

# Path - A Set of Points

## Class Summary
```java
path(ArrayList<Pose2d> points)
```
If you don't know what a path is, swerve might not be for you.

## Usage
You make an ArrayList<Pose2d>, and you pass it into the class. It represents the points that the robot will pass through. If you don't like Pose2d and prefer to use lists for some reason, `Pose2d.fromList(double[])` exists. It takes 3 doubles: x, y, and theta.  Have fun :D

Just pass the current gyro angle into the `Pose2d`s if you don't want the robot to rotate. It's also in radians because I'm not a monster.

You can cycle through the points using a few things, like `getCurrentPoint()`, `getNextPoint()`, and `getPointRelativeToCurrent()`.

Because some users had difficulty with these, we added some builtin nearest point utils: `nearestPointIndex()` and `nearestPoint()`, pretty cool, huh?