---
layout: post
title: "tutorials_scientific_tools"
date: 1970-01-01
---

====== ROS ======

roslaunch ros_robotics ddrobot_rviz.launch model:=dd_robot2.urdf

==== Initial Set Up ====

export ROS_MASTER_URI=http://localhost:11311

roslaunch gazebo_ros empty_world.launch

roslaunch turtlebot_gazebo turtlebot_world.launch

rosservice call gazebo/get_model_state '{model_name: mobile_base}'

in a loop topic type, also a set would work, but it would run only once. 
Pub is publish until it is stopped.
     
rostopic pub -r 10 /mobile_base/commands/velocity \geometry_msgs/Twist '{linear: {x: 0.2}}'

==== Complete Setup: ====

Turtle Bot hardware: roslaunch turtlebot_bringup minimal.launch

Remote computer 1 or another terminal window : 

roslaunch turtlebot_dashboard turtlebot_dashboard.launch

Remote computer 2 or another terminal window : 

roslaunch turtlebot_teleop keyboard_teleop.launch

rostopic pub -r 10 /mobile_base/commands/velocity \geometry_msgs/Twist '{linear: {x: 0.2}, angular: {x: 0, y: 0, z: 1.0}}'

OR 

rostopic pub -r 10 /cmd_vel_mux/input/teleop \geometry_msgs/Twist '{linear: {x: 0.1, y: 0, z: 0}, angular: {x: 0, y: 0, z: -0.5}}'


==== Miscallenous ====

rqt_graph ( just the graph ) 

rqt ( everyting )

python ControlTurtleBot.py # does the above with the python script


==== More Examples ====


roslaunch turtlebot_rviz_launchers view_robot.launch

roslaunch kobuki_auto_docking minimal.launch

roslaunch kobuki_auto_docking activate.launch


==== Kinetic with ROS ====

export KINECT_DRIVER=freenect

export TURTLEBOT_3D_SENSOR=kinect

libfreenect-dev

ros-indigo-freenect*

git clone https://github.com/avin2/SensorKinect

The camera driver software ( freenect_camera ) publishes the depth_image message streams. 

Kinect sensors, ASUS Xtion sensors, and Carmine sensors instead of LIDAR


====== MATLAB ======
imshow
imread()
imadd(image, 20 ) ; addding contrast to the image.
.* : Array multiplication. If we use this in matrices, the each element would be multiplied. A normal matrix multipilcation has equal number of rows and columns.
‘ transpose
.’ non conjugated transpose
helpwin
getenv
! ; execute operating system command
help funfun
help elfun ; elementaary math functions
help specfun  ;specialized math functions
array is addressed by ()
eyes, ones, zeros, diag, triu, tril, rand, hilb, magic, toeplitz, hankel,
conv, deconv ( multiply and divide polynomials )
help format

====== MATLAB INSTALLATIOM ======

Installation key:
R2013b:    42023-36922-18882-06643-33417-26687-54188-41497-37121-22095-23528-34718-57326-51832

You need a open vpn for mitarbeiter.

Installation folder:
C:\InstalledPrograms\MATLAB\R2013b

Products:
MATLAB 8.2
Simulink 8.2
Bioinformatics Toolbox 4.3.1
Communications System Toolbox 5.5
Computer Vision System Toolbox 5.3
Control System Toolbox 9.6
Curve Fitting Toolbox 3.4
Data Acquisition Toolbox 3.4
Database Toolbox 5.0
DSP System Toolbox 8.5
Embedded Coder 6.5
Filter Design HDL Coder 2.9.4
Fixed-Point Designer 4.1
Fuzzy Logic Toolbox 2.2.18
Image Acquisition Toolbox 4.6
Image Processing Toolbox 8.3
MATLAB Coder 2.5
MATLAB Compiler 5.0
Model-Based Calibration Toolbox 4.6.1
Neural Network Toolbox 8.1
OPC Toolbox 3.3
Optimization Toolbox 6.4
Signal Processing Toolbox 6.20
SimDriveline 2.5
SimElectronics 2.4
SimHydraulics 1.13
SimMechanics 4.3
SimPowerSystems 6.0
Simscape 3.10
Simulink 3D Animation 7.0
Simulink Coder 8.5
Simulink Control Design 3.8
Stateflow 8.2
Statistics Toolbox 8.3
Symbolic Math Toolbox 5.11
System Identification Toolbox 8.3
Wavelet Toolbox 4.12

mex --setup
mex --setup cpp


I had the same issue.
So, I took solutions from the above and tried it. 
I selected one from Bogdan which matched my environment the most, but however implementing was not a cake walk.
So, I would write whatever problems I faced and how I solved it.

First of all mexopts.bat is taken by default even if your matlab version is 64 bit.
You can find out which version your matlab is running on by clicking on Help-About.

In your Roaming/MathWork/R2013a you will find two files - mexopts.bat and mexopts_64.bat.

If you want to take the mexopts_64.bat file you have to do
mex -v -f  mex -f 'c:\Users\EDITME\AppData\Roaming\MathWorks\MATLAB\R2013a\mexopts.bat' 'c:\Program Files\MATLAB\R2013a\extern\examples\mex\yprime.c'

The -v is for verbose and -f is to force the matlab to use another option file as the default.

Please note that you have to change two options: 
1. Compiler ( please write the name only, without the extension ) : x86_64-w64-mingw32-g++
2. Linker: x86_64-w64-mingw32-ld

Once everything goes smoothly, a file called yprime.mexw64 would be generated. The extension of the file is dependant on the architecture and is mentioned here:
http://www-rohan.sdsu.edu/doc/matlab/toolbox/compiler/ch02ins5.html

The file would be generated in this folder.

I got confused when I saw two different compilers i.e c++ and g++ and found out actually its just a copy of one another. G++ just denotes that it is from GNU and c++ is a name of a generic compiler.

The generated file yprime.mexw64 would be preset in the folder from where you are executing the commands. The input may be from other directories, but the binary file i.e executing file would be present in the pwd.

mexext would tell you which platform you are using.
mexw64 is a compiled binary and function calls can be made from this compiled file. A slx file is a simulink model whihc is a zipped folder and contains xml and png etc.
sim('drawBox') - run the .slx file-
open('drawBox') - open the .slx file


-Inf, Inf, NaN, ans, pi, default is 64 bit double, 'vikas', disp('Hello'), to supress output end the line with semicolon, 
rowww = [ 1,2,2,-6.6]
colmn = [1;2;2;-6.6]
Its always rows, column which can be found out by size(rowww)
to find the number of elements  length(rowww) or length(colmn)
clear var, clear all, 
save myFile, save myEnv, load...


S Function Builder generates the template C Files depending on the configurations in the S funciton builder. The generation is the input and outputs in the file. The intelligence ofocurse has to be coded once the template C files are generated.
The C files that are generated are then compiled with the mex compiler which in turn uses the Visual Studio C compiler.
This generates the mex464 file which is a library of the compiled files.
This library can be supplied to the vendor including the function definitions.
In our case, the udpImuSocket_Example.mexw64 provides functions such as init, read and send. To see what functions are implemented in the  
mexw64 or a exe or any other executable, run the DependancyWalter on the file. It is like a readelf.

start path is in startup.m in programfiles/matlab/toolbox/local/

Simulink: Simulation and model-based system design.
Simulink Coder: Generate C and C++ code from simulink and stateflow model.
Embedded Coder: Generate optimized embedded C and C++ code.
Simulink Verification and Validation: Use for simulink models and generated
codes verification.
Simulink Code Inspector: Source code review according to DO-178 safety stan-
dards.
Simulink Design Verifier: Verify design according to requirements and generate
test vectors.
Real-Time Workshop: Generate simplified, optimized, portable, and customiz-
able C code from Simulink model-based design.
Real-Time Windows Target: Execute Simulink models in real time on Win OS
based PC.
xPC Target: Use for real-time rapid prototyping and HIL simulation on PC
hardware.
xPC TargetBox: Embedded industrial PC for real-time rapid prototyping.
Real-Time Workshop Embedded Coder: Embedded real-time code generator for
product deploymen


====== POWERPOINT ======

p (%theta divides %phi, I ) = exp - (sum from{m=1} to{m=M} ({1} over {2%sigma_{m}^{2}  }))   