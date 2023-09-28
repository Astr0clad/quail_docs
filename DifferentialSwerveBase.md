---
label: Differential Swerve Module Base
order: 2
icon: mirror
---

# Differential Swerve Module Base - Swerve Module, But Differential

## Class Summary
```java
differentialSwerveModuleBase(Vec2d position, double steeringRatio, double driveRatio);
differentialSwerveModuleBase(Vec2d position, double steeringRatio, double driveRatio, boolean optimized);
```
Crazy

## Usage
**ABSTRACT FOR A GOOD REASON FOR ONCE**

**Suggested Usage:**
Create a method to set the motor powers/module that takes in a `Vec2d`. This method should use `calculateMotorSpeeds`, some PID magic, normalizing powers to your maximum allowable motor power, and actually setting your motor powers. 

It is highly recommended that you feed your motors and encoders into this class. Absolute encoders are great, but your motor's relative encoders can work if you rub your braincells and do some math. You will need your drive and steering ratios if you decide to go the math route. Using a PID controller for getting the *rotation* speed is recommended, but not required. Getting the wheel speed is just `Vec2d.getLength()`. You should also probably do some form of "wheel flipping" to optimize turns, eg., instead of turning the module 180 degrees, just invert the drive speed. Recommendations, not requirements.