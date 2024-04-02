---
label: Two Wheel Localizer
order: 1
icon: goal
description: Abstract class for two wheel odometry
---

# TwoWheelLocalizer - Abstract Class For Two Wheel Odometry

## Class Details
```java
TwoWheelLocalizer(List<Pose2d> wheelPoses>);
```
I could be useful with this message, but that's a lot of work.

## Usage
***ABSTRACT FOP A REASON!***

I recommend creating some form of interface on top of this class to make it easier to use. Have a `periodic()` or `update()`, a `getPos()` or `getPose()`, and a `setPos()` or `setPose()` method.

**Required Methods:**
- Override `getHeading()`
- Override `getWheelPositions()`
- A 'periodic' method to call `TwoWheelLocalizer.update()`, eg., `super.update()`

**Recommended Methods:**
- Convert encoder ticks to unit of measurement
- A method to return the Pose2d of the bot, utilize `TwoWheelLocalizer.getPoseEstimate()`, eg., `super.getPoseEstimate()`
- A method to set the Pose2d of the bot, utilize `TwoWheelLocalizer.setPoseEstimate()`, eg., `super.setPoseEstimate()`
