

Determining the height of the earth pile. 

For local map use ego motion to determine the position and orientation.
For global map use GPS to determine the position.

Devices that provide tilt angles (with respect to the gravity) are known as tilt sensors/inclinometers/Neigungsensor. The inclinometers measuere the slope (elevation or depression) of an object where the tilt sensor is mounted upon. Inclinometers must be hence mounted upon the device whose tilt needs to be determined. Accelerometer is a type of inclinometer. 

One of the implementation of inclinometers is accelerometers. To get an accurate acceleration value, the object needs to be on a plane surface, otherwise the device cannot differentiate between a real incline and acceleration.
Two-axis inclinometers that are built with MEMS tilt sensors provides simultaneous two-dimensional angle readings of a surface plane tangent to earth datum. 

Usage of accelerometers to determine the tilt:
As inclinometers measure the angle of an object with respect to the force of gravity, external accelerations like rapid motions, vibrations or shocks will introduce errors in the tilt measurements. To overcome this problem, it is possible to use a gyroscope in addition to an accelerometer. Any of the abovementioned accelerations have a huge impact on the accelerometer, but a limited effect on the measured rotation rates of the gyroscope. An algorithm can combine both signals to get the best value out of each sensor. This way it is possible to separate the actual tilt angle from the errors introduced by external accelerations


Calibration of the tilt sensor on 0,0,0. Recalibration 
The WCET is more than seconds. 
In case of Quadrocopters, the decision for the throttle needs to be taken in milliseconds. But here the speed of the dozer is relatively small and hence even a dual axis tilt sensor will do the work


