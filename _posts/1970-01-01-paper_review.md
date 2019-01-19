---
layout: post
---

Problems-
setting up a calibrated system of multiple cameras and range sensors is a tedious task. its a tedious ask because it requires user intervention. Camera to camera and camera to range is done separately.

Hence, author presents a toolbox with webinterface which calibrates ( recovers intrinsic and extrnisic camera parameters ) as well as transformation between camera and range sensors in a minute. This proposal does not require user interventions, robust to vaying imaging conditions ( indoor and outdoor settings ), fully automatic and single shot image. Camera to camera and camera to range is done in a single method.

The proposed method detects checkerboard corners in a much more efficient way than the earlier methods for example by Bougat Additionally multiple solutions are discovered in case of ambiguities in the proposed camera to range registration method.

Experimental Setup - Kinect 3D, Velodyne HDL-64, grayscale and color cameras.

Calibration to represent sensed information in a common coordinate system. Calibration parameters are intrinsic ( shape of the lens ) and extrinsic parameters ( pose of the camera ).
