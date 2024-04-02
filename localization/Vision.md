---
label: Vision
order: -1
icon: device-camera-video
---
# Vision

For help with vision, Quail provides a Kalman filter, implemented as a mostly drop-in replacement for the other `Localizer` classes.

## Background

Many robots have multiple methods of getting a field pose, including vision and wheel odometry. The Kalman Filter is a method for fusing the two sensors.

The Kalman Filter is particularly useful in situations where the robot's environment is noisy or uncertain. Vision data is typically quite noisy and can jump wildly, deteriorating pathplanning attempts. By fusing data from multiple sources, it can provide a more precise and stable estimate of the robot's position. 

## Usage

First, one must create a `KalmanFilterLocalizer` with the robot starting
position and robot looptime (50ms default for FTC, 20ms default in FRC)

!!!primary
The initial position does not matter if the vision reports a position on startup
!!!

After the localizer has been created, simply call the
KalmanFilterLocalizer.update() with the vision pose, the field-relative
velocity, how much to trust the vision, and the current timestamp in milliseconds.

## Math

---

At any given time/tick ($t$) we are trying to estimate our position, we do this through a weighted average of a kalman estimate and pose data from our vision system. Because the pose that the limelight sends us can be four ticks behind the current pose, we compensate for this by applying basic dead reckoning given the last n recorded velocities since we last got a limelight update

| $\hat v$ | Velocity vector |
| --- | --- |
| $P_k(t)$ | Kalman estimate at a given tick $t$ |
| $P_v(t)$ | Vision position estimate at given tick $(t)$ |
| $\hat P(t)$  | Combined estimate postition |
| $w$ | How much weight we “trust” the vision estimate |
| $\dot t$ | How many ticks since we last got a limelight update |

### Update Rule

$$
P_k(t) = P_k(t-1) + v(t) \\
$$

$$
P_v(t) = \hat P + \int_{t-\dot t}^t v(t)dt \\
$$

$$
\hat P (t) = \frac{wP_v(t) + (1-w)P_k(t)}{2}
$$

!!!primary
Because we cannot do an actual integral in our periodic function, we will keep a  buffer of the last n velocity values and take the sum of those when calculating the position from the limelight.

In in this case is the maximum number of ticks between limelight updates
!!!

### Pseudocode

```python
position_estimate = ...
last_velocities = [...]

def calculate_vision_trust(...):
  # calculate how much we trust the vision
  # either return a constant or calculate it based on vision state

def update():
	velocity = get....

	# This should update off of the estimate otherwise you'll have compounding drift
	position_kimenatics = position_estimate + (velocity * deltaTime)
	w = calculate_vision_trust()
	# Do we have a new "vision pose" from the limelight, if so treat that as our vision position
	if limelight_ready:
			position_vision = limelight_position
	# Otherwise don't trust vision at all
	else:
			w = 0

	position_estimate = (w * position_kinematics + (1-w) * posiiton_vision ) / 2
```
