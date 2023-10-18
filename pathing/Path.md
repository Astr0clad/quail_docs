---
label: Path
order: 2
icon: milestone
---

# Path - A Set of Points

## Class Summary
```java
path(ArrayList<double[]> points, double finalHeading)
```
If you don't know what a path is, swerve might not be for you.

## Usage
You make an ArrayList<double[]>, and you pass it into the class. It represents the points that the robot will pass through, in the form [[_x_<sub>1</sub>, _y_<sub>1</sub>], [_x_<sub>2</sub>, _y_<sub>2</sub>], ... [_x_<sub>:icon-infinity:</sub>, _y_<sub>:icon-infinity:</sub>]]. Have fun :D

FinalHeading is now **required**. Just pass in the current gyro angle if you don't want the robot to rotate. Its also in radians because I'm not a monster.

You can cycle through the points using a few things, like `getCurrentPoint()`, `getNextPoint()`, and `getPointRelativeToCurrent()`.

Because some users had difficulty with these, we added some builtin nearest point utils: `nearestPointIndex()` and `nearestPoint()`, pretty cool, huh?