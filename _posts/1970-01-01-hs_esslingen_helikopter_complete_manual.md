---
layout: post
title: "hs_esslingen_helikopter_complete_manual"
date: 1970-01-01
---



====== Compiler Linux ======

CROSS_COMPILE
ARCH
INSTALL_MOD_PATH

clean
menuconfig, xconfig, oldconfig, config
dep
zImage
modules_install
distclean

zImage, bzImage. Both are uncompressed Image and has nothing to do with gzip and  bzImages.

depmod

-F System.map

-b / ( base directory where the modules are stored for this architecture ).

    apt-get install build-essential fakeroot 
    apt-get build-dep linux 
    apt-get source linux
    git clone git://kernel.ubuntu.com/ubuntu/ubuntu-precise.git
    apt-get build-dep linux-image-(uname−r)
    apt−get install linux−image−(uname -r)
    chmod a+x debian/scripts/*
    chmod a+x debian/scripts/misc/*
    fakeroot debian/rules clean
    fakeroot debian/rules editconfigs
    fakeroot debian/rules binary-headers binary-generic

This takes the current configuration for each architecture/flavour supported and 
calls menuconfig to edit its config file. The chmod is needed because the way the source package is created, it loses the executable bits on the scripts.
In order to make your kernel “newer” than the stock  Ubuntu kernel from which you are based you should add a local version  modifier. Add something like “+test1” to the end of the first version  number in the debian.master/changelog file, before building.

If the build is successful, a set of three .deb binary package files will be produced in the directory above the build root directory. For example after building a kernel with version “2.6.38-7.37” on an amd64 system, these three (or four) .deb packages would be produced:

    cd ..
    ls *.deb
    linux-headers-2.6.38-7_2.6.38-7.37_all.deb
    linux-headers-2.6.38-7-generic_2.6.38-7.37_amd64.deb
    linux-image-2.6.38-7-generic_2.6.38-7.37_amd64.deb


Testing the new  kernel
Install the three-package set (on your build system, or on a different target system) with dpkg -i and then reboot:

    sudo dpkg -i linux*2.6.38-7.37*.deb
    sudo reboot

====== Patching a kernel ======


    cd /usr/src 
    wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.19-rc4.bz2  
    cd /usr/src/linux 
    bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1  –dry-run 
    bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1


Purging  a PPA means, downgrading the packages in the selected PPA to the  version in the official Ubuntu repositories and disabling that PPA. PPA  Purge does exactly that. 
To install PPA Purge run the following command:  

    sudo apt-get install ppa-purge


====== Debug Symbols ======


Sometimes it is useful to have debug  symbols built as well. Two additional steps are needed. First  pkg-config-dbgsym needs to be installed. Second when executing the  binary-* targets you need to add ‘skipdbg=false’.

    sudo apt-get install pkg-config-dbgsym
    fakeroot debian/rules clean
    fakeroot debian/rules binary-headers binary-generic skipdbg=false
    
    sudo  apt-get -o Debug::pkgProblemResolver=yes dist-upgrade 
    sudo apt-get -u  dist-upgrade sudo apt-get -f install
    sudo apt-get clean
    fakeroot, kernel-wedge, gawk

Alternatively,  before compiling, use the kernel config option “LOCALVERSION” to append  a unique suffix to the regular kernel version. LOCALVERSION can be set  in the “General Setup” menu.

– In order to boot your new kernel,  you’ll need to copy the kernel image (e.g.  …/linux/arch/i386/boot/bzImage after compilation) to the place where  your regular bootable kernel is found.

Command to install linux source Command to download is 
    
    apt-get source linux-image-$(uname -r)
    svn checkout svn://developer.berlios.de/socketcan/trunk
    Git clone git://kernel.ubuntu.com/ubuntu/ubuntu-maverick.git
    Fakeroot debian/rules clean Dh_testdir
    apt-get source kernel-source-2-4-27
    apt-get install kernel-source-2-4-27
    apt-get source linux-headers-$(uname -r)

====== ELDK ======


for running for eldk on 64 bit hosts

    Sudo apt-get install ia32-libs
    Ncftp  ftp.sunet.se 
    Wget ftp://ftp.sunet.se/pub/linux...
    patch -p0 <  u-boot-1.1.3.at91rm9200_mmc.patch
    sudo add-apt-repository  ppa:kivy-team/kivy
    configure –enable-win64 make make install

Traditionally,  UNIX platforms called the kernel image /unix. With the development of  virtual memory, kernels that supported this feature were given the vm-  prefix to differentiate them. The name vmlinux is a mutation of vmunix,  while in vmlinuz the letter z at the end denotes that it is compressed.


====== TODO ======


The basis of the PPM measurement is provided via a Kernel module. The analysis of the measured time differences needs to be done to get the separated control signals. The orientation fusion delivers perfect representation of all three angles around the X,Y and Z axis of the system. Because of the usage of Euler angles there can be a gimbal lock when due to rotations two of the three axis fall together. Then one degree of freedom is lost. To solve this problem the system should not use Euler angles, instead Quaternion needs to be used. Autonomous flying with just the orientation is not possible. Also the position of the Quadrocopter needs to be known. For this, additional sensor fusion focusing the velocity and position in all directions has to be calculated. Last step is the implementation of the controller for the orientation and the position which finally controls the complete system. To switch between flying with the remote control and the autonomous flying a switch of the remote control needs to be used.



====== Quadrocopter Hardware ======

    BLMotor282734
    BL-Ctrl V1.2
    Brushless DC Motoren "Robbe ROXXY BL-Outrunner 2824-34

The motors are controlled over the I2C bus. And the values must be refreshed every 10 ms otherwise, the values are reset to 0 on the motor side.

The parameters to send the data is first the Motor address and then the PWM value. Both the parameters are 1 byte long.

The motors have a minumum and a maximum PWM value.

====== Remote control ======


Graupner radio remote control system. The PPM signal needs to be decoded at the receiver end. The Graupner remote control is a multi-channel system that comprises the transmission of up to 12 channels. Each individual channel is encoded by a PWM signal with a period time of 20ms (resulting in a update rate of 50Hz). According to the transmitted value of each channel, the on-time varies between 1ms (min. value) and 2ms (max. value). That means, only 1 -2 ms is on time within 20 ms. In order to communicate on all the 12 channels, a PPM encoder is used, that encodes the channel duration. The PPM decoder assumes, that all the channels are sending some value and hence the decoder regenerates sequentially the PWM signals for each channel after reading the PPM stream. The end of the transmission ( the last 20 msecs ) is always a silence, because otherwise it would be difficult to know when the new PPM signal has started. Hence the length of the PWM signals for each channel is encoded into the duration between the two PPM pulses. Some Graupner systems have the reverse logic i.e the new PWM channel starts at the falling edge instead of the rising edge of the PPM pulse. The 12 channel controller sends a frame with 13 peaks and 12 pauses. A 8 channel controller sends a frame with 9 peaks and 8 pauses.

GR-16 ( Remote receiver ) - with three pins ( 3-8.4V DC, Ground and Data ) . The documentation is in 33508_Kurzanleitung_de.pdf. The Voltage and Ground can be taken from the RAspberry. However for the data pin, one of the GPIO pins can be used as an input. That means, the GR-16 data goes into the Raspberry GPIO and hence the RAspberry GPIO has to be declared as input.

MX-20 is the remote controller. The communication between the Remote controller and the remote receiver has to be established first. For that the button on the remote receiver has to be pressed till the red light turns to green. Ofcourse, the remote controller should be switched on before. To do it for the first time, the remote controller would ask if the receiver is switced on or off. To calibrate newly, select it to be switched off.  After that manually look for the point Module in the Menu. This triggers a search and the remote receiver should turn green. Once it turns green, confirm by pressing the SEt button. The display should say connected.

Normally, the incoming PPM ( pulse pause modulation or pulse position modulation ) should be decoded by a dedicated hardware, to free the operating system with any resource. However, since we are using RT linux, it is also possible to use this instead of a dedicated hardware.


====== Hardware Design ======


The hardware design is done in EAGLE Freeware, that has a limit to the maximum number of components per layout. But the number of components can be divided into many layout and hence EAgle freeware can be used without any problems. Alternative was Fritzing.

====== Motherboard ======


  * Unordered List ItemRaspberry Pi B+ board with BCM2708 SoC
  * BCM2708 or BCM2835 is a SoC  which includes VideoCore GPU from Broadcom, ARM11, Level 1 and 2 Cache,  and RAM and the SoC is assembled on the Raspberry.
Kernel:
  * For Raspberry 2, there has been no stable real time  kernel for the multi core CPU BCM2709. Hence Raspberry Pi B+ ( also  known as Raspberry Pi 1 ) was chosen. The PREEMPT_RT is available for  Raspberry Pi B + ( ARM 11 ) Nevertheless, due to 40 pin compatibility, the entire  project / software can be ported onto the 
Raspberry Pi 2. 

  *    Broadcom BCM2835 Mainboard
  *    ARM1176JZF-S Prozessor 700 MHz
  *    Braodcom VideoCore 4 Grafikkarte mit OpenGL ES 2.0, 1080p30 h.264/MPEG-4 AVC high-profile decoder
  *    512 MB Arbeitsspeicher
  *    Audio Ausgänge: 3.5 mm Jack
  *    Onboard microSD Speicherkartenslot
  *    10/100 Ethernet RJ45 onBoard
  *    Speichermöglichkeit über microSD Speicherkartenslot
  *    4x USB 2.0.


Um das Ansteuern der Rotoren zu ermöglichen muss das braun blaue Kabel an den SCL Pin und das braun-rote Kabel an den SDA Pin der kleinen Platine angeschlossen werden!
===== Adafruit GPS =====


Additionally,  the expansion board Adafruit GPS Hat including a Global Top GPS receiver with built in Chip Antenna.  The GPS uses the UART lines and  hence blocked for any further usage. 

===== Polulu AltiIMU v4 ( 10 DOF Version ) =====
 
  *    ST LSM 303D
  *    Three different chips mounted on the IMU and hence has a different I2C  address. 
  *    Accelerometer Component:
  *    Magnetometer Component:
  *    e-Compass
    
===== Gyroscope =====


  *  3D MEMS Gyroscope ST L3GD20H

    X-axis angular rate data. The value is expressed as two’s complement.
    OUT_Y_L (2Ah), OUT_Y_H (2Bh)
    Y-axis angular rate data. The value is expressed as two’s complement.
    OUT_Z_L (2Ch), OUT_Z_H (2Dh)
    Z-axis angular rate data. The value is expressed as two’s complement.


===== Barometer =====

  *  ST LPS331AP
    
===== AdaFruit ADS1015 =====


  *  4 channel A/D Convertor from TI. The ADC chip used is from TI ADS1015. New mappings has been done in the 40 pin connector at pin 27 and 28 to generate SCL and SDA for I2C between the Raspberry main board and the ADC board. https://www.adafruit.com/datasheets/ads1015.pdf. 3300 conversions in a second and the standard I2C address is 0x47.


===== Polulu D15V70F5S3 =====


  *  DC-DC converter ensuring a stable supply of 5V DC  and a continuous draw up to 3.5 A is used. Nevertheless, USB 5 V can also be used during testing.

I2C Bus:

  *  Communication between the ADC chip and  the controller
  *  Communication from the sensors to the ADC
  *  Communication from the controller to the  motors travel


====== Software Functions and Drivers ======



===== Soft landing =====



By flipping a switch on remote control, user may instruct the quadrocopter to perform an autonomous landing. In order to achieve this, an ultrasonic sensor will be integrated to estimate the height from ground.

===== Hovering =====


By flipping a switch on remote control, user may instruct the quadrocopter to stay in that position, until further instruction. Any external disturbance will be compensated automatically. In order to achieve this, a GPS sensor will be integrated to record the position. To improve the accuracy, the integrated accelerometers and Gyro sensors would be used in control.

====== Visualisation ======


Remote visualisation on PC will be developed as well as it will be helpful during the function development and future autonomous flying. Through zigBee connection, parameters on microcontroller can be transmitted wirelessly to PC and be further processed.

====== Sensor Integration ======

  *  GPS
  *  Barometer
  *  Gyroscope
  *  Accelerometer
  *  Magnetometer

I2C Bus: 
     Motor 1: 0x29 
          2: 0x2A 
          3: 0x2B 
          4: 0x2C
          5: 0x5A
          6: 0x5C
          7: 0x5E
          8: 0x60
          
    IMU ACC 0x1E oder 0x1F 0x28
    ADC : 0x47
    IMU Gyro 0x6A
    IMU Pressure 0x5C
    Laser Sensor 0x62

   
====== Sensor Fusion ======

  * generic library for fast matrix operation
  * Kalman filter
  * sensor fusion for IMU ( AHRS - Attitude and Heading Reference System ) 
  * Tilt comensation for IMU
  * complementary filter
  * Extended Kalman Filter ( non linear )

The major difference between IMU and AHRS is that IMU just provides the data, but AHRS is an onboard software which uses the  IMU data to provide the attitude ( orientation ) and heading information. The critical flight dynamics parameters roll, pitch and yaw ( angle of rotation ) is around the vehicle center of mass.

In the past, gyroscopic flight instruments were used to calculate the vehicle orientation that was not very reliable.

AHRS can be combined with air data computers to form an "air data, attitude and heading reference system" (ADAHRS), which provide additional information such as airspeed, altitude and outside air temperature.
====== Challenges ======


wind from the quadrocopter itself / drift. Solution is to compensate the drift by correcting the position everytime. The correction can happen either using Indoor localisation or odometry.

Obstacles during landing. Solution is to remember the path, circling and tilting.

====== Toolchain ======


We need tools that would build programs or a kernel  that is capable of running on the SoC ( BCM2708 from Broadcom ). The tool chain  is called gcc-linaro-arm-linux-gnueabihf-raspbian-x64 ( arch-vendor-(os-)abi ) and can be  obtained via the github.com/raspbian/tools.git 
  *  arm-bcm2708-linux-gnueabi
  *  arm-bcm2708hardfp-linux-gnueabi
  *  gcc-linaro-arm-linux-gnueabihf-raspbian
  *  gcc-linaro-arm-linux-gnueabihf-raspbian-x64

    
====== Building the kernel ======

  * Git  clone –-depth=1 https://github.com/raspberrypi/linux
  *  Please note that for the below two commands, the major, mior and the development version must match. This can be verified by typing make kernelversion after the repository has been downloaded.
  *  Git clone –-depth=1 https://github.com/raspberrypi/linux.git -b rpi-3.18.y 
  *  Wget https://www.kernel.org/pub/linux/kernel/projects/rt/3.18/older/patch-3.18.16-rt13.patch.xz
  *  Git clone –depth=1 https://github.com/emlid/linux-rt-rpi.git
  *      Since some Kernel module driver has been developed during this project, it was also necessary to compile the custom Kernel drivers for the EMLID-distribution. Therefore, get slightly modified Kernel sources of the EMLID-distribution can be found at \url{https://github.com/emlid/linux-rt-rpi}. To download the sources to the Development Environment VM, the following commands can be used:
    
  * Raspbian distribution: Wget http://downloads.raspberrypi.org/raspbian_latest
  * xcat “patchname” | patch –p 1 –dry-run
  * Xcat “patchname” | patch –p 1
  * Directly on the Raspberry : https://www.raspberrypi.org/documentation/linux/kernel/building.md
  * Make variables:    
  * KERNEL=kernel 
  * ARCH=arm
  * CROSS_COMPILE=arm-linux-gnueabihf- ( arch-vendor-(os-)abi )
  * INSTALL_MOD_PATH=path-where-you-want-to-output 
  * EXTRA_VERSION=
  * make Help
  * make kernelversion  
  * make kernelconfig 
  * make bcmrpi_defconfig ( using this is preferred, because most required adaption is already available for the raspberry pi, otherwise the user needs to configure a lot of options if he uses make menuconfig )
  * make zImage
  * make modules
  * make dtbs
  * make modules_install  
  * sudo dd  if=”firmwareimage” of=/dev/sdb
  * raspi-config
        Under Advanced Options: 
        Enable I2C
        Enable SSH
        Disable  Kernel Debug to UART
        Configure Hostname Change

I2C baud rate for the  option i2c_bcm2708 baudrate in /etc/modprobe.d/i2c.conf to 400000. options i2c_bcm2708 baudrate=400000. This step would not be needed if the pre configured EMLID image is used. In the pre configured EMLID image, the UART port is configured to the required setup by default. No Kernel debugging messages are put to the serial port. But the default I2C baudrate is set to 1Mhz which is to much. The highest common frequency of the sensors participating on the I2C bus is 400kHz.

        If no  i2c.conf exists, create one. Reboot for the changes to take place.
        (1) 8 Advanced Options => A4 SSH => <Enable> => <OK>
        (2) 8 Advanced Options => A7 I2C => <YES> => <OK> => <YES> => <OK>
        (3) 8 Advanced Options => A8 Serial => <NO> => <OK> ( Dont use Kernel debugging on UART ) 
        (4) 8 Advanced Options => A2 Hostname => <OK> => "HElikopterPi" => <OK>
        (5) <FINISH> => <YES>

====== Kernel Boot ======

  * scp zImage root@192.168.22.169:/boot/zImage
  * rsync –av modules-folder pi@192.168.22.161:/lib/
  * edit /boot/config.txt and write kernel=”yourimage” 
  * sudo reboot
  * uname –a should have the new host name
  * Linux HElikopterPi 3.18.14-rt10+ #1 PREEMPT RT Mon Jun 15 21:21:16 CEST 2015 armv6l GNU/Linux

====== Pre-configured Image ======

wget http://www.emlid.com/new-raspbian-with-real-time-kernel-jan-2015/

For a convenient and easy start with the Raspberry Pi, a pre-configured Raspberry Pi Firmware can be found at the SVN repository folder \texttt{/sys/RPi/}. The pre-configured Firmware Image is based on the EMLID-distribution. The EMLID-distribution originates from a open source project for a different Raspberry Pi based Quadcopter. It comprises the RT-Kernel patch as well as several optimizations regarding the system configuration to access peripherals that fit to the needs of this project.

For this project, pick the archive file EMLID\_Preempt\_IP192.168.2.1.zip from the SVN repository. Unzip the file to get the extracted 8GB Firmware Image.



====== Debugging ======


The debugging  happens on the SSH channel i.e the user logs into the raspberry pi via  another computer.
    

====== I2C ======
 

  * sudo  i2cdetect –y 1 will give the list of connected I2C addresses.
  * sudo apt-get install i2c-tools
  * lsmod | grep i2c_ # should show i2c_bcm2708
  * Der I2C-Bus (braunes rot/blaues Kabel) wird mit den I2C Pins des Raspberry PI B+ verbunden. Pin2 ist Serial Data und Pin5 ist Serial Clock. Braun-blaues Kabel ist für das Clocksignal , braun-rotes Kabel ist für das Datensignal. 
    
====== Algorithms ======

Quaternion based pose estimation

  * Landing:
        Circling
        Remebering
        Lateral Buckling


====== S Function ======

  * Matlab R2013a
  * Create S Function Builder under User-Defined Functino
  * Choose an appropriate S-Function name (in this example myUdpSource is used) and type it in the textbox in top area of the configuration window. Next click on Initialization on the tab menu. You will see four properties S-function settings in the middle of the window. In case you are creating a signal source, as shown in this document, ensure that all state numbers are set to zero!
  * Output in S Function is what would be converted from outside to Matlab Data types. Hence, all inputs should be 0, because we dont have any Matlab Data types to be converted into C Types. All dimesions are 1D, some of the variables have 3 rows ( for example accx, accy, accz ) and all the variables have real values.
  * Automatically generate TLC function such as STart and Terminate under BuildInfo, because the network needs to be initialised and closed, otherwise it will block the port.
  * SEt sample time to 0.01 by adding a ( double )  variable sampleTime in the parameter field under DataProperties.
  * Build and two files myUdpSource.c and myUdpSource_wrapper.c is created.
  * Edit myUdpSource.c to include the udpImuLib header file and define the remote IP ( in format {x,x,x,x } and the remote port number from where the data is expected.
  * To store the socket number declare a variable static int m_simSocketNumber = 0
  * Create a socket in the mdlStart() and close the socket in mdlTerminate()
  * Adapt myUdpSource.c and myUpdSource_wrapper.c with the socketNumber variable. This is not generated automatically ofcourse, because the variable was not input in the S function builder model. 
  * The user-defined sample time has to be extracted out of the parameter list in the function sampleTime()
  * mex sourcefiles ( including the udpImuLib.c )
  * Create Simulink --> Userdefined -> matlabfunction block and write the graphical code ( drawBox.m )


Matlab: Simulation model-> Tools ->  Library -> User defined functions -> S Function Builder – 
  * All  input ports needs to be deleted
  * All outports need to be deleted  and new ones to be put according to the number of outputs from the model
  * in the parameter section add sampleTime with the default value of  1
  * in the BuildInfo section, add Additional Methods and click on  the Start and Terminate. The Start is called when the simulation is started and the Terminate is called when the simulation is closed.  Sample time is discrete with sample time with 0.1. The file to be edited  should be the wrapper because the function calls the wrapper function.  This is used to avoid overwriting used defined code. 
  * Use simstruct, do not generate TLC. 
  * However, once the files are generated, we would simply  use the main file by modifying the generated functions i.e the wrapper  function is left untouched. Since the default parameter type is double  in Matlab, avoid unit8, otherwise one has to type unit8(100) everytime  this value is accessed. 
  * The generated file has to be modified and edit  mdlStart and mdlTerminate. 
  * The Simulink engine and S Function exchange  information, initialize and terminate and this is possible thru the  generated built in functions – mdlStart, mdlInitialize, mdlTerminate.  
  * Mex udpSigSocket.c ../.c. 
  * To see the underlying compiler, type mex  –setup. 
  * In my case [1] Microsoft Software Development Kit (SDK) 7.1 in  C:\Program Files (x86)\Microsoft Visual Studio 10.0 is selected.  
  * Simulation model-> Tools -> Library -> User defined functions
  * Matlab function Mex –g “c files” to compile with debugging  information. 
  * This generates a pdb file. To debug files, one has to start  Visual Studio and attach the process Matlab.exe to the Visual Studio.  
  * mex.getCompilerConfigurations(‘C’,’Selected’).Name should be Microsoft  
 
====== Visual Studio ======


Copyfile(fullfile(matlabroot,’extern’,’examples’,’mex’,’yprime.c’),’.’,’f’)  yprime(1,1:4) 

Complete model 

The model oli*.slx contains the  entire model i.e S-Func Builder as well as the scopes and the draw Box. So, this is the file which needs to be run. 

    While true; do echo -n “hello” | nc -u -w1 localhost 5000; done 
    nc -u localhost 48772 
    nc –zz  localhost 8888 –u mex –Dhost -D_WIN32

Important eclipse  settings Project-Properties-C/C++ Build->Settings-Cross Settings

  * Prefix is arm-linux-gnueabihf and Path is the location to the binaries (  as, ld, cc etc. ). In the raspberry case it is  /usr/local/bin/gcc-…./arm-linux-gnueabihf/bin 
  * Project-Properties-C/C++ Build->Settings- Tool chain editor : Cross GCC Run -> Debug  Configuration -> C/C++ Remote Application
  * Under Main: Name of the  project, The path of the application which needs to be run or debugged,  connection settings and the path where the application needs to be  copied on the remote computer. After the application has been copied via  eclipse to the remote computer it is run on the target machine. To be  able to debug the code, it is needed to Use GDB ( DSF ) Automatic Remote  Debugging Launcher. We need to start the GDB server with root privileges  using sudo. This is required in case the program requires  user-restricted resources such as GPIO. 
  * The Under Debugger: change the  default debugger from gdb to arm-linux-gnueabihf-gdb. 


====== GDB over the console ======


  * First start a server on the target machine; 
  * sudo gdbserver host:port binaryname; 
  * From a terminal, start the  arm-linux-gneueabihf-gdb and type target remote host:port 
  * Load the  symbol table again by loading: file file_with_symboltable  configuration: set verbose on List, break linenumber, continue,  backtrace, info registers, disas, disconnect, info break p &a[0]@10,  directory source-file-dir 


To  be able to debug successfully on the host machine, you need the  libcurses library. This basically means that the GDB client  "arm-linux-gnueabihf-gdb" requires the libncurses.so.5 shared library to  run. If your arm-linux-gnueabhihf- is a 32 bit toolchain, you need a 32  bit library as well.

    sudo  apt-get install libncurses5:i386 libncurses5 
    dpkg –add-architecture  i386 
    sudo apt-get update
    sudo apt−getsourcelinux−image−2.6.32−25−generic
    sudo apt-get install linux-image-2.6.32-25-generic-dbgsym 
    gdb  /usr/lib/debug/boot/vmlinux-2.6.32-25-generic
    (gdb) list schedule 5519  /build/buildd/linux-2.6.32/kernel/sched.c
    (gdb) set substitute-path  /build/buildd/linux-2.6.32 
    (gdb) list  schedule
    apt−getsourcecoreutils
    sudo apt-get install coreutils-dbgsym
    gdb/bin


====== Raspberry Software ======


The layers are 
Application layer. Example GPS Position Hold functionality
Signal Processing layer: Example sensor fusion
Post processing GPS data
Post processing IMU data ( acceleration, rotational speed and pressure data to calculate roll, yaw and pitch )
Sensor fusion of sensor signals of the IMU 
Hardware Abstraction Layer: Example GPS data from the sensor
Low Level Driver: Example peripherals integrated in the kernel.
Datastructures : rtSigAllStatePayload ( includes time stamp + all imu + kalman and complementary orientation data ), rtSigPayload ( time stamp + normal orientation data ), rtImuPayload ( timestamp + all imu data )

====== Visualisation Software ======

The Helikopter-Oscilloscope is a JAVA based program and is run to visualise the incoming data. To run the software, it is important that the build path contains all the necessary libraries. This is done by adding the libraries to the Reference Library such as jfreechart, jcommon etc. 
Also exclude RXTXComm.src from the Source files.


====== Kalman Filter ======


[[http://www.convict.lu/htm/rob/imperfect_data_in_a_noisy_world2.htm]]
[[https://www.codeproject.com/Articles/865935/Object-Tracking-Kalman-Filter-with-Ease]]


====== Simulations ======

  * 01_Control_one_angle:     Vereinfachtes Modell eines Winkels des Quadrocopters:  
  * 01_PID_Control_one_angle:    Wie Control_one_angle mit der Erweiterung, dass die verwendeten Motoren einen ungleichen Schub erzeugen, und dass dieser mit einer PID Regler Kaskade geregelt wird.
  * 02_Control_two_angles:    Vereinfachtes Modell bei dem Roll und Pitch geregelt mit einer P-Regler-kaskade geregelt werden.
  * 03_control_2_angles_and_yawrate:    Wie 02_Control_two_angles mit dem Unterschied, dass zusätzlich die Winkelgeschwindigkeit des YAW geregelt wird.
  * 04_discrete_control_phi_theta_rpsi:    Die diskretisierte Regelung des Modells 03_control_2_angles_and_yawrate
  * 05_discrete_control_with_noise:    Wie 04_discrete_control_phi_theta_rpsi mit dem Unterschied, dass den Regelgrößen ein Rauschen überlagert wird.
  * 06_discrete_noise_Quantified:    Wie 05_discrete_control_with_noise mit dem Unterschied, dass die Regelgrößen zusätzich quantifiziert werden, um die Abtastung eines Milrcontrollers zu simulieren
  * 07_discrete_control_angle_from_acc:    Wie 06_discrete_noise_Quantified mit dem Unterschied, dass die Winkel-information zuerst in eine Beschleunigung und anschließend wieder in  einen Winkel zurückgerechnet wird.
  * 07_PID_Discrete:    Vollständiges Modell der Quadrocopterregelung unter Verwendung einer PID-Reglerkaskade.
  * 08_HIL:   Vollständiges Modell der Quadrocopterregelung Regelung mit dem Block für den Modell in Loop test. Verwendet zusätzlich den Embedded MATLAB Block für die P-Reglerkaskade.
  * 08_PID_HIL:    Wie 08_HIL mit dem Unterschied, dass der Embedded MATLAB Block die Regelung per PID-Regler beinhaltet.
  * Final_System:      Enhält das Gesamtsystem für die P-Reglerkaskade/Zustandsregler. Finales System ist jedoch im Ordner 08_PID_HIL !!!
  * scratch:     Enthält MATLAB-Dateien für Versuche.

Matlab Files
  * calc_stability.m:    Dieses M-File wertet das Modell Quadrocopter_control bezüglich der Eigenwerte(Polstellen der Regelstrecke) aus.
  * Control_lib.mdl:    Dieses M-File wertet das Modell Quadrocopter_control bezüglich der Eigenwerte(Polstellen der Regelstrecke) aus.
  * Control_lib.mdl:    Diese Bibliothek beinhaltet Simulink Blöcke, welche für die Regelung verwendet wurden.
  * Copter_Library.mdl:    Diese Bibliothek beinhaltet Simulink Blöcke welche für die Regelstrecke, Animation und Sensoren verwendet wurden.
  * Copter_Animation.m:    Level 1 S-Function welche die Animation des Quadrocopters beinhaltet, wird von einem S-Function Block verwendet( siehe Copter_Library.mdl).
  * crc16.c:    Mex-Function zum Berechnen der CRC16-Prüfsumme für das Quadrocopter ZigBee Modell.
  * crc16.mexw32:    Compilierte Mex-Funktion aus crc16.c.
  * double2uint8.c:    Mex-Function zum konvertieren von double zu unsigned int8.
  * double2uint8.mexw32:    Compilierte Mex-Funktion aus double2uint8.mexw32.
  * quadrocopter_param.m:    Diese Datei erzeugt die Parameter für den Quadrocopter im Workspace
  * _sfun.mexw32: Diese Dateien beinhalten die Compilierten Embedded MATLAB teile der Modelle mit dem Namen *.mdl.  !!! Anmerkung:  Auf Grund von Pfadtiefen kann es erforderlich werden Modelle zuerst in diesem Pfad auszuführen und dort die *_sfunc.mexw32 Dateien erstellen zu lassen. Anschließend können diese in den entsprechenden Ordner kopiert/verschoben werden.

