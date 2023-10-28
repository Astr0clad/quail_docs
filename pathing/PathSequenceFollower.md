---
label: Path Sequence Follower
order: 0
icon: list-ordered
---

# PathSequenceFollower - Following Sequences of Paths

## Class Summary
```java
PathSequenceFollower(PathFollower pathFollower);
```
Neat

## Usage
This class strings together a mix of paths and "markers". These two things are consdered "segments". Think of markers as a point where an action should occur. Currently they are synchronous only, meaning the robot will wait until the previous segment has completed before running the next segment. If you can't understand that, then you shuoldn't be using this class.

When initialized your sequence follower, you will need to give it a sequence to follow, these can be added onto at any time. To add segments to your sequence any of these methods can be used:
```java
PathSequenceFollower.addPath(Path path);
PathSequenceFollower.addDisplacementMarker(Runnable action);
PathSequenceFollower.addLocalTemporalMarker(double delay, Runnable action) // delay in seconds
```
It is important to understand what these do. 
- Using `.addPath()` will add the specified path to the sequence. 
- Using `.addDisplacementMarker()` run the specified action when the marker is reached.
- Using `.addLocalTemporalMarker()` will run the specified action after the specified time has passed since the start of THIS segment (since the end of the previous segment).

#### **DO NOT RUN BLOCKING METHODS IN MARKERS**.
###### When using markers, it is super important to not use `sleep()` or any other blocking methods, it will pause everything under the sun.

You should use `.addLocalTemporalMarker()` to wait. An example use could be when you want to instruct a servo to go to a position, but wait 1 second before moving to the next segment after commanding the servo (grabbing something). You don't have to do this per say, but if you want a working autonomous, you should.

To run this follower, you should probably call `followPathSequence()` in your loop and feed the `robotMovement` it returns into your drivetrain. You can also use `isFinished()` to check if the sequence is finished. Again, all of this is optional, I just think it's a good idea to use it.

*This class is still kinda goofy, report any issues you find*