---
layout: post
title: "tutorials_opencl"
date: 1970-01-01
---

====== History ======


The law of physics govern the universe. Every movement on the planet earth can be predicted using the law of physics. Due to the research and development in the field of computer science, it is now also possible to simulate the law of physics in computers. For example, it is possible to simulate a collision between two objects and depending on  the impact of the collision, the objects rebound as if they had done when they would have in the real world.

The simulation of law of physics has been made possible by creating libraries that has been initiatives of big companies like Apple, Intel etc. Most of the electronic games use these libraries to create games, so that the effects in the games are close to the real world. These libraries are developed under the banner of OpenCL ( Open Programming Language Libraries ).

APIs ( Application Programmers Interface ) are provided so that these libraries can be called from other programs. Normally, the APIs are provided for different languages and primarily for some of the main programming languages such as C, Python, Lua, Java, Matlab, Octave and Urbi ).

The main idea is to use these APIs and create a scene. The scene can be a collision between two cars or a robot picking up a device from the assembly line etc. VREP ( Virtual Robot Experimentation Platform )  freely downloadable from http://www.coppeliarobotics.com/ is one such software that specializes in simulation environment for robots.

A single compute device consists of several compute units and each compute units consits of several processing elements. The functions that execute on an
OpenCL device or CUDA enabled Devices or OpenGL enabled devices or OpenACC enabled devices are called compute kernels. 

Development on Hetrogeneous architecture

====== CUDA ======

sudo /usr/local/cuda-10.0/bin/uninstall_cuda_10.0.pl
sudo /usr/bin/nvidia-uninstall  

update-grub
update-pci
update-initramfs

CUDA enabled graphics card
FLOPS/Watt

training a machine learning system on a large dataset


CUDA is a parallel computing platform and provides APIs to do parallel computing on the NVIDIA GPU Cores.
The prerequisite is that the GPU should be CUDA enabled for general purpose processing  - an approach termied GPGPU.
The CUDA platform is a software layer that gives direct access to the GPUs virtual instruction set and parallel computational elements for the
execution of the compute kernels. There is a CUDA compiler called NVCC and also CUDA libraries  such as Cuda core library and CUDA run time library.
Other widely used libraries are CuBLAS ( numerical calculations ) , CuFFT, CuDPP ( scan, sort data etc. ) . The NVCC compiler separates CUDA code and
general code with the help of file extensions. The files with .cu will be compiled by nvcc.


====== OpenACC ======

CUDA supports programming frameworks such as OpenACC ( Open Accelerator ). OpenACC is a programming standard or specification for parallel computing.
It is designed to simplify parallel programming of hetrogenous CPU/GPU systems.
For example, the programmer can annotate C++ code to identify the areas that should be accelerated using compiler directive and additional functions. These
annotations are done by specific keywords such as data, kernels, loop and cache. If CUDA has inbuilt support for OpenACC, then that means, it would 
understand these annotations. GCC supports OpenACC / PTX code in the meanwhile. The primary mode of programming according to OpenACC standard is
directives ( pragmas ). The compiler which supports OpenACC such as gcc, nvcc ( nvidia cuda compiler ) must understand the OpenACC annotations.
 #pragma acc parallel
 #pragma acc kernels
 #pragma acc data
 #pragma acc loop
 #pragma acc cache
 #pragma acc update
 #pragma acc declare
 #pragma acc wait
Run time APIs are defined too. As said, OpenACC is just a standard. It is the job of the compiler to implement them. And the function calls should remain standard, such as
acc_get_device_type, acc_set_device_type, acc_get_device_num, acc_set_device_num, acc_init, acc_shutdown, acc_malloc, acc_free etc.
The whole principle is based on gangs and workers.

Support for non contigous memory segments
handling of unstructured data
seperate compilation for creation and reusage of libraries of accelerated code

The steps are Analyze -> Parallize -> Optimize.
The code is analyzed using profiling tools.

====== OpenCL ======

OpenCL is a framework for writing programs  that execute across hetrogenous platforms consisting of CPUs, GPUs, DSPs, FPGAs and other processors
or hardware accelerators. OpenCL specifies programming languages ( based on C99 and C++11 ) for programming these devices and application program interfaces
to compute and control the devices. OpenCL has its own set of function calls that are implemented in the libOpenCL.so. These functions can be called from the development programs
such as clReleaseKernel etc.  Currently, boost, opencv, nvidia and many more have implemented the OpenCL functions according to the reference. This makes the 
function calls interoperable because the public API remains the same and two independent vendors can communicate with each other.
The specification is divided into a core specification that any OpenCL compliant implementation must support; a handheld/embedded profile which relaxes the OpenCL compliance requirements for handheld and embedded devices; and a set of optional extensions that are likely to move into the core specification in later revisions of the OpenCL specification.     
For example, the most common usage of interoperability is the data transfer between two independent vendors on the same computer such as host cpu from amd and gpu from nvidia.
If Nvidia is  OpenCL compliant, then the host cpu can simply call an openCL compliant function without even possessing the actual GPU.
OpenCL lets  any application tap into the vast gigaflops of GPU computing power previously available only to graphics applications. OpenCL is based on the C programming language and has been proposed as an open standard. One such example is FFT for a numerical calculation.
OpenCL runtime ( also called the ICD ( Installable Client Drivers ) loader ) loads the vendor specific ICD for example Nvidia ICD and then redirects the consumer call appropriately. This way the game programmer does not need to know the underlying GPU and can simply include the OpenCL header, that further redirects the calls to the GPU. It is important that each GPU must implement all the OpenCL functions in order to be forward the consumer calls to the underlying hardware.


To be able to compile Nvidia OpenCL SDK Files.
sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev

====== OpenGL ======

Renders 3D graphics.
                            
====== Mesa ======



====== XWindow ======

    dpkg-reconfigure xserver-xfree86

    xserver-xorg-driver-nouveau has to be deleted
    you can do this using additional drivers.
    Select nvidia.

    modprobe -v module
    modprobe -r module

    list of all modules integrated in the kernel lsmod
    list of all modules ; ls /lib/modules/$(uname -r)/kernel/drivers/; ls /lib/modules/$(uname -r)

    dpkg-reconfigure kdm
    DISPLAY=:0 compiz --replace

    Alt PrntScreen K kills your Display manager.

    dconf reset -f /org/compiz/
    nohup setssid unity

    nohup compiz --reset
    nohup unity --replace

    Alt PrntScreen K kills your Display manager.
    dconf reset -f /org/compiz/nohup setssid unity

    /etc/X11/default-display-manager
    /usr/bin/\*session

    XDG_CURRENT_DESKTOP
    wmctrl -m
    echo $DESKTOP_SESSION
    import os
    os.get.environment('​CURRENT_DESKTOP')

    exo-preferred-applications
    initctl restart unity-panel-service
    xdg-mime under .local/share/applications
    desktop-file-install \*.desktop

    command line tool for querying information about file type handling and adding descriptions for new file types

    XDG_CURRENT_DESKTOP : current desktop environment.

    DISPLAY-MANAGER:

    cat /etc/X11/default-display-manager
    ls /usr/share/xsessions/
    Alt F2 – Open a program
    gnome-do gconf_editor&
    rdesktop -g 1680\*1050 -u agrawal ork-win
    sudo apt-get install gnome-tweak-tool
    import os; print os.environment.get('DESKTOP_SESSION')

Graphics Driver
    blacklist nouveau in /etc/modprobe.d to avoid nouveau to be loaded.

Gpu test
 
    lshw -class video
    watch -d nvidia-smi

Download GpuTest : \url{http://www.geeks3d.com/20140304/gputest-0-7-0-opengl-benchmark-win-linux-osx-new-fp64-opengl-4-test-and-online-gpu-database/#download}
    
    ./GpuTest /test=fur /width=1024 /height=640
 
Switching between graphic cards:

There is only one graphic card in the VIRES PC. Hence there is no chance of switching between graphic cards. The only thing one can do is switch between drivers. One is the nouveau provided by xfreedesktop.org and the other is directly from nvidia. Both of them use different OpenGL drivers.
 
    sudo prime-select nvidia
    sudo prime-select intel



                                                                   