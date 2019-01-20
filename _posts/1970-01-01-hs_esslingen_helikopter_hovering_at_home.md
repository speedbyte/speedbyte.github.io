---
layout: post
title: "hs_esslingen_helikopter_hovering_at_home"
date: 1970-01-01
---



====== Hovering@Home ======


The project is divided into 4 teams:

====== Teams ======

  * Control Application Team
  * Embedded Software Team
  * Virtual Reality Team
  * Android Team


====== Interfaces ======

  * Interface between Control Application and Embedded Software
  * Interface between Embedded Software and Android Application
  * Interface between Control Application and Virtual Reality



===== Control Application team: =====

The job of the control application team is to make a model through which the
HElikopter can hover. Therefore the team should make a Hovering@Home
Model in Matlab.
The Core Quadrocopter Model has the information about the weight, length
of the arms and the number of rotors and hence can emulate the Quadro-
copter dynamics. The inputs to the main Quadrocopter model are the initial
values of angles, acceleration and the rotor speed. Through these initial val-
ues, the Core Quadrocopter model, calculates the subsequent raw, pitch
and yaw angles and also the linear acceleration in all the vectors.
The angles and accelerations are then fed to the Hovering model. The job
of this models is to maintain the final set point of all angles ( raw, pitch
and yaw = 0 i.e hover ), and thereby calculate the rotor angular speed to
be fedback to the Quadrocopter model again.
This process is done iteratively for the entire time the simulation is running.
Additionally, the control team should generate the Hovering Model using
the Real time code generator and verify the software by means of Software
in Loop Tests.

{{hs_esslingen:helikopter:images:control1.png }}  {{hs_esslingen:helikopter:images:control2.png }} 

===== Embedded Software Team =====

The goal is to build a raspberry image from scratch. The main goal of this
team is to make a stable Real time kernel. Hence a real time linux image
needs to be ported to the raspberry hardware. Before the linux image (
kernel.img ) is ported, it is required to also install a bootloader that will
boot the kernel.img during the start up process.
Once the kernel is running, the embedded software team should be able to
debug the kernel through GDB. That means the kernel should be compiled
with the -ggdb3 ( debug option switched on ).
To be able procure acceleration, magenetic and gyroscope values on the
raspberry hardware, IMU, Gyroscope and Magnetic sensor are embedded
onto the main raspberry motherboard. The communication between the
main raspberry motherboard and the additional board ( consisting of the
sensors ) happens over the I2C bus.
The team should be able to hence build a kernel called HochschuleEsslin-
genRaspbian.img that already has all the inbuilt packets including the I2C
packages.
The application software HElikopter.bin is already provided to you. This
application software is already provided to you. The application software
can already read the acceleration, magnetic and Gyroscope values. The
team should be able to set a breakpoint anytime in the software during the
execution of the application software on the hardware to read the internal
variables.

Three subgoals:

  * Linux Kernel
  * ROSBerry
  * Packet Management, GDB and running the application

{{hs_esslingen:helikopter:images:embedded.png }}
===== Virtual Reality Team =====

Simulink-based quadrocopter model visualized with Google Cardboard VR 


**Description:**

The quadrocopter-model based on MATLAB/Simulink will be used to show the behaviour of the quadrocopter in a virtual reality environment. The object will be controlled with head movement. The virtual reality device is a android smartphone with google cardboard. A google cardboard app will be developed with Unreal Engine 4 and the Google VR Plugin. This can be adapted to an Oculus Rift or HTC Vive device later. The communication between the smartphone and the Simulink simulation is realized with UDP. 

Sub-goals:

  * UDP Connection with the MATLAB Team
  * Running Unreal Engine with Google Cardboard / HTC Hive
  * Verification of the Matlab code
  * Application should be able to guide the HElikopter with head movements 

**Proposal architecture:**

{{:hs_esslingen:helikopter:architecture1.png?400|}}

<del>==== First Proposal ====


A native software similiar to the Matlab needs to be built in VREP. Here,
the specifications are the same as for the Matlab Team. The only difference
is that in VREP, the Quadrocopter Dynamics Model is readily available (
drag and drop ), whereas in MATLAB, a Quadrocopter Dynamics Model
had to be built from scratch. Also, in V-REP one can attach the sensors
( drag and drop ) on the Virtual Quadrocopter and simply start acquiring
the values, once the system is run.
</del>

{{hs_esslingen:helikopter:images:virtualreality.png }}


===== Interface between Control Application and Embedded Software =====


Ofcourse, even if raspberry and the control simulations are available, the
quadrocopter body ( or basically the whole car ) is not available for tests.
In our case, yes, but if you would have been a Tier II supplier, it would
not have been available immediately to you. So, lets assume that we do not
have any Quadrocopter body as of now.
The following method to test the embedded software even if the real car is
not available is called Hardware in the Loop Tests. We need a hardware in
the Loop simulation which is everything from the Control Team except the
Hovering Model. This is self explanatory, because the developed Hovering
Model under MATLAB is already ported to the Embedded hardware.

{{hs_esslingen:helikopter:images:interface-control-embedded.png }}

===== Interface between Control Application and Virtual Reality =====





The MATLAB software already runs the Hovering@Home model. In this
model, the quadrocopter will be guided by the head movements from the Virtual Reality Team. The new hovering position would be the new location provided by the virtual reality team. <del>always has to return at 0,0,0 and hover at an alti-
tude of 1 m. Any kind of disturbances for example pushing the quadrocopter
with the hand or due to wind, must bring the Quadrocopter back to 0,0,0.</del>
The VR team should prepare a verification software. One of the use cases
in the verification software is for example, to change the (x,y,z) position of
the quadrocopter and compare the calculation with its own calculations <del>returns to its original position
0,0,0.</del> The changes should be ofcourse visible graphically in a 3D environ-
ment.

{{hs_esslingen:helikopter:images:interface-control-vr.png }}



