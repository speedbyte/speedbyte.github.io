---
layout: post
---

Future Slides

Compiler
Abstraction level
abstraction breaking by direct memory pointers, link scripts.

Difference between Computer networks and distributed systems.
A distributed system does a particular task. The user sees only one device and thinks it is doing the same thing which in actually is distributed.
A computer network does not especially need to do a single task. It is a backbone for the application to do the tasks it wants.


A processor-in-the-loop (PIL) simulation cross-compiles generated source code, and then downloads and runs object
code on your target hardware. By comparing normal and PIL simulation results, you can test the numerical
equivalence of your model and the generated code. During a PIL simulation, you can collect code coverage metrics
and execution time measurements for the generated code.


MIL, PIL, HIL and SIL, DIL

MIL Model in Loop : The environment ( for example, the controller, the network, and the car itself ) are not ready when a software is written for a specific task
PIL Processor in Loop : Generate software code and then run the verification process on the target processor.
HIL Hardware in Loop
SIL Software in Loop : Generate software code for example from matlab and then run the verification process on the host computer.
DIL : Driver in loop

The hardware in loop comes at a later stage.


The software running in the hardware must be developed as a control system application and tested.

For example, the ACC get values from the Vehicle Speed Module and the Tilt Module and thereby has a control
application to increase or decrease the throttle - thereby maintaining the vehicle speed.

Similarly, the Hovering Module gets the angular / linear acceleration from the Quadrocopter Speed Module, and the Tilt Module running in MATLAB. The speed and the tilt is then transferred to the Hovering Module that should increase or decrease the throttle, thereby maintaining the Hovering.

If the control application works completely fine, then the control application is converted into a specification to be programmed
in the embedded hardware by embedded engineers.



Bandwidth - range of frequencies that pass through without getting attenuated
Baud - noumber os samples per second
Symbol rate - number of symbols in one baud
Modulation technique - number of bits per symbol

Bit rate - Symbol rate * Modulation technique - ( symbols / second ) * ( Number of bits / symbol )
Simplex, Half Duplex and Full Duplex

Splitter ( an analog filter )  separates POTS ( plain old telephone service ) and Data.
QAM - Quadratuer Amplitude Modulatoin - both frequenc shift key and amplitude shift key is used.

Frequency Division Multiplexing - using different frequencies to construct the end signal. Typical example is radio stations. FM stands for frequency modulation and eaach
stattion is given a specific frequency. Only a specific frequency can be used , but for the entire time.

Wavelenght Division Multipliexing
Time Divisin Multiplexing - the whole spectrum can be used only at a specific time.

Teledesic, Globalstar, Iridium are low earth orbit satellites.
