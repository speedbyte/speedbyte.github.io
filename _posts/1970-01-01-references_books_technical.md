---
layout: post
title: "references_books_technical"
date: 1970-01-01
---

Optics Light and Lasers, Dieter Meschede

Optics - Eugene Hecht -Great book

 ====== Embedded Linux O Reilly ======


 TARGET=arm-eabi
 PREFIX=/local/development/arm-project/tools
 TARGET_PREFIX=/local/development/arm-project/tools/arm-eabi
 CROSS_COMPILE=arm-eabi
 ARCH=arm-eabi

 1. kernel headers
 2. binutils ( binary utils setup )
 3. gcc ( bootstrap ) -  gcc-linux-headers
 4. C library set up
 5. gcc ( complete ) enable=c,c++

     make arm=arm64 TARGET=arm64-linux make menuconfig
     ./configure --without-headers --without- enable=c

 Imagining that we are the target now and how would the toolchain behave if it were on the target

     ./configure host=arm64 --without-headers --without- enable=c

     binutils 2.25 :  git clone git://sourceware.org/git/binutils-gdb
     ./configure --prefix=$CROSSDIRECTORY --target=m68k-coff

 gcc 4.9.2

     ../gcc-/configure --prefix=$CROSSDIRECTORY --target=m68k-coff --enable-languages=c

 EDIT: Success! Using GCC 4.9.2 (with GMP 5.1.3, MPFR 3.1.2, MPC 1.0.2, ISL 0.12.2, and CLooG 0.18.1) I succesfully
 built GCC. Tips to take from here:
 Make sure you use ISL and CLooG. Yes, they are optional, but they make a more optimised compiler and I had trouble
 building without them. Make sure you use ISL 0.12, not the latest version (0.14).
 If possible, use the standalone Developer Tools, not XCode. (XCode has some buggy headers, and while I didn't notice
 any issues building GCC I have had issues with other software (e.g. GPG)).
 I recommend putting all your sources in the gcc directory, rather than building and installing separately (it's faster
 this way)
 Make sure you invoke configure with CC=clang CXX=clang++ so GCC knows it isn't being compiled by GCC.
 Definitely, definitely, definitely, invoke make with -j8, or otherwise the build will take about 4 hours!

 ftp://gcc.gnu.org/pub/gcc/infrastructure/
 must: gmp. mpfr, mpc

 optional: , isl


 ====== Master Handbook of Acoustics Sixth Edition, F Alton Everest and Ken C Pohlmann ======

 Sound always needs a medium to travel and hence cannot travel in vacuum. Air, liquid, gases, solid all transfer sound
 from one point to another. The particles propagate the sound. The particles however do not have a large displacement and ofcourse the velocity at the max displacement is 0. One can imagine this as wheat crop swaying from one end to the another in a soft wind. The only difference with sound waves would be that preceeding wheat crop pushes the successive wheat crop and hence a chain of waves is built. The intensity of the preceeding wave rapidly diminishes and hence it looks like that the sound wave is propogating ie travellling from one end to the other.

 The faintest sound a ear can hear is 20µPa, that is around 5000 times smaller than the atmospheric pressure. The
 phrase, loud sound hence does not only depend on the intensity of the sound, but also the pressure between the sender and the receiver.

 Dense air would take the sound waves faster to the receiver. Thats why solids and liquids and dense gases have faster
 propagation of  the sound. Sound travels at around 350m/s in air at normal pressure and temperature and at around 1350m/s in fresh water.

 Normally the decibel level is always calculated by multiplying 20. However, when the power is compared, then the
 decibel level is multiplied by 10. This is because the relation between power and voltage is a square. The difference between octaves and frequency is that the next higher octave is double the base frequency. The harmonics can take any multiplication value. Theoretically, the second, fourth and eighth harmonics is equivalent to 1st, 2nd and 3rd Octave. Octave is a musician term, because our ears percieve the change in 100 to 200 Hz, in a different way as the change in 200 Hz to 300 Hz. Our ears, however percieve change in 100 Hz to 200 Hz same as 200 Hz to 400 Hz. From a engineers point of view, the change in 100 to 200 Hz is the same difference as change in 200 Hz to 300 Hz.

 Sound intensity in decibels differ from sound intensity in watts/m². The sound intensity ratio is without units ( the
 units cancel each other ) but to clarify the value, a unit is given and that is called a bel ( from Abraham Bell ) . Since the value is too small, we further express values in decibel. A decibel is 10 times the logarithm to base 10 of the ratio of two quantities of intensity. The decibel (dB) is a logarithmic unit used to express the ratio between two values of a physical quantity, often power or intensity".

 Sensitivity per Watt, Frequency Response with tolerance, Loudspeaker impedance, Output watt are some of the
 specifications one should look before buying speakers. Active speakers are speakers that has inbuilt amplifier and passive speakers are speakers that has no inbuilt amplifier. A speaker that has no inbuilt amplifier also does not have any current circuitry i.e it relies on an external amplifier to provide the power.


 ====== Comp TIA Meyer ======


 CPUID, Memory Specs, memtest86.com, SPD ( Serial presence detect ).
 VESA, HDMI, DVI, PS2, USB A, USB B, USB Mini B, Display Port, Jack, Plug, Port, DIMM, SATA, PATA, Anti-static bags.
 RJ45
 External  Data Bus is connected between the RAM module and the CPU. To fetch the  data, the RAM Module needs an extra
 address bus and this determines the  size of the RAM. The memory location that has been decided to be fetched  is kept on the EDB. All this job is taken over by the MCC ( Memory  controller chip ). The data that is fetched from the RAM is a  instruction and this instruction is stored in the register for further  processing. The fetching of data from the RAM takes a lot of time and  hence there is a L1 cache inside the CPU, which accelerates the  processing of the instruction. The wait time to fetch a RAM insturction  can take as many as 10 to 20 cycles. The processor has to be kept in the  wait state because it is waiting for the next insturction. P6 started  to scout for instructions in the pipeline which can still be executed at  this waiting time. Hence only that pipeline was put in the wait state  but the other pipelines continued working. The wait time was also  because, the RAM needs to refresh its transistors and it also had its  internal wait time. The motherboard manufacturers have also put another  cache called the L2 cache and it is a bigger cache than the L1 cache. if  data is not found in the L1 and in the L2, it is fetched from the RAM.  During the time the data is fetched, from the memory, the CPU does other  actions such as caching, calculations etc which has no dependancy on  the RAM module. However, for every step a clock is required and hence  the CPU clock has a multiplier which multiplies the clock cycle from the  crystal on the motherboard. This means that there are two  specifications,
 the motherboard clock which is typically 200 Mhz and
 the  CPU clock, which is typically 3 Ghz. The source of both the clocks is  the quartz. The multiplier is set by a
 jumper on the board or it is done  automatically by the CPU Id. the CPU iD consists of information with  what clock cycle the CPU can run and hence the technicians do not need  to change any jumpers on the motherboard.
 To accelerate the  processor, there are multiple pipelines. For example, one pipeline is  dedicated to the normal
 operations, and the other pipeline to the  arithmetic / floating point operation. During the time spent in the  fetch cycle from the RAM, the second pipeline can still go through the  calculation operations.
 The instructions fetched are either 32 bit  or 64 bit and that means the EDB and the Regsters in the CPU should  have
 the same length. However, both of them are made from different  manufacturers and hence they do not know about each other. If the CPU is  a 64 bit instruction, then it needs two cycles to fetch two 32 bit data  to make the 64 bit instruction. This ofcourse, takes double the time.
 8088  has was a 8 bit external data bus and the registers were Ax to Dx. The  clocks are like buzzers and signals that
 the computer is ready for the  new job. They had 20 bit address bus and 16 bit registers. RAM is called  random access because it is irrespective of the feched address. The  time taken to fetch that data is the same immaterial to where the data  is present.
 The processors were further accelerated by doing the  branch prediction and hence the prediction where the next data
 would be  coming from. This data set was then stored in the cache memory before  even the instruction was executed. Super scalar execution is a term used  when more than 1 process is executed at one time in one clock cycle.
 The  interface between the motherboard and the CPU is the socket. There were  various methods such as BGA, PGA,
 staggered PGA, micro PGA, lang grida  array. To make CPU insertion and removeal easier, these sockets are  called ZIF ( Zeor insertion force ) sockets using a small arm on the  side of the socket. Socket numbers are named accoridng to the number of  pins on fhe CPU, like Socket940, Socket720. Earlier sockets were called  Socket1, Socket7 etc.
 AMD ( Advanced Micro Design ) and Intel are  CPu manufacturers and after 1995, they are nomore pin compatible i.e AMD
 is no more a clone of the intel processors.
 The processors were  further optimized, when the voltage was changed from 5 V to 3.3V. But  that means, the motherboard
  must have a supply with 3.3V. This is done  by VMR ( Voltage Regulator Module ) and this module damped down modules  especially for the CPUs. The voltage reduction, reduced the size of the  transistors and cram more of them in the same space.
 Speculative  execution is a combination of branch prediction and out of the order  processing ( A processing where
 other instructions are worked upon )  during the time the next data is being fetched. Once the data is  fetched, the instructions are rearranged and then continued processings.  The L2 cache is not exactly in the CPU and hence the combination  between the CPU and the L2 cache is called backside bus. The L2 cache is  also connected to the MCC, the same way the CPU is connected to the  MCC. The connection between CPU, MCC and RAM is called the frontside  bus.
 The inclusion of MMX ( Multimedia extensions ) is especially  ofr graphic related tasks because vector maths was
 required to handle  graphical issues. The MMX was developed because engineers thought that  to do graphical tasks, they needed a special circuitry to develop such  programs. Overtime, the graphic community began to work with Intel to  improve MMX, eventually replacing it with better solutions.
 To Pentium P6, the answer was AMD K6. AMD also answered MMX or SIIME ( Steering SIMD Extension ) with 3DNow.
 The  power management was subsequenly done to reduce heat because the more  the voltage and the processing, the more
 the heat. Intel had Speedstep  and AMD had PowerNow technology to reduce the clock during the idle  phases. Also, the mobile computers, run atleat 4 times slower than their  desktop coutnerpart. System Management module in Intel processors  monitored the curent CPU state and hence did the power management.
 Photo  lithography technique used for etching circuits on silicon wafers (  using chemicals and UV rays ) . The thinner
  the process, the lesser heat  was evolved. Hence 165 nm is better than 3 mm ( from the 80286 days ).
 The  processors were still optimised using the hyperthreading ( more than  one thread execution on a single pipeline ).
  A single CPU with  hyperthreading would look like 2 CPUS to the operating system and  quadpumped technology. ( single clock cycle but 4 data transfers on the  EDB )
 Dual core : 2 CPUS on a single core, and having 2 exection units and 2 pipelines but shared caches.
 In  every motherboard, there is a jumper called CMOS clear, which brings  the settings of the motherboard to the
 default setting. This clears the  BIOS with the factory settings and hence, the computer can be hacked  through this process.
 To spread heat from the processor, there are  various methods and one of them is a heat dope ( thermal compound ) .
 The heat dope acculmulates all the heat and this can be circulated away  using a fan or a liquid cooling system.
 DRAM chips comes in width  greater than 1 bit. Earlier DRAM chips were 1 bit wide, which means only  1 bit can be
 extracted from a single chip at one time. 8 bits were  extracted when the MCC polled 8 DRAM chips simultaneously. If the chips  were put on a module, it s called a SIMM ( Single Inline Memory Module  ). There are various data width now a days like x8 or x16. So a module  with 1 Mbyte is 1M of rows and 8 columns ( 8 chips on the mdoule ). Back  in the old days, hence there were chips which were 64K x 1 dababit  wide. Hence there are two terms: Module width and the chip width. The  module width is the combination of individual chip widths. Synchronous  DRAM was invented by AMD which was tied to the system clock. The memory  worked only on clock cycles, just like all the peripherals and the CPU  on the motherboard. On laptops, microDIMM and SO( small outlile ) DIMMS  are used. SDRAMS since tied to the system clock were known from their  motherboard counterpart i.e PC33, PC166 etc. For the SDRAM to work  properly, the SDRAM must support equal to or greater than the  motherboard clock. Because EDB were getting wider, it was required to  have wider DRAM chips i.e x4 x16 etc. The modules were inserted into  banks with specific pin numbers and mechanical codings which means a  SDRAM wont fit into a RDRAM slot even if the pin numbers were identical.  To support AMDs double and quad pumped technology on front side buses,  there was a need to make faster DRAMs. The quad pumping made it possible  to send 64 bits of data two or four times for every clock cycle,  effectively doubling the frontside bus speed and hence doubling the  througput. RDRAM ( Rambus DRAM ) an initiative of Intel and Rambus used  the dual channel architecture later copied by AMD helped to create  faster reaction time of DRAMs. In this architecture basically two  processed are created for each clock cycle. This was known as DDR SDRAM (  Double data rate SDRAM ). They naming convention was double
 the FSB i.e  a 100 MHz FSB, leaded to a DDR speed rating of DDR200 and hence the PC  Speed rating of PC1600 ( 200*8 ) i
 .e 1600 Mbit per second. Later DDR2 (  with modifications on electrical circuits, including more cache etc )  came in and they double the speed yet making PC3200 for the same FSB i.e  3200 Mbit /s To be able to use the dual channel technology, the modules  also need to be inserted in pairs. A third module in a third slot which  was usually colored coded with black ( the normal ones are blue ) turns  off the dual channel technology and hence making the PC slower although  more RAM is available. DIMMs are memory modules that have chips on both  the sides of the memory modules. Latency rates ( the clicks of the  system clock before a RAM can respond ) . The latency can be set  manually and its better to start with something low and go up till the  system is not stable.
 BIOS is a program that is embedded into the  system ROM. The BIOS reads the CMOS which contains the configuration of
 the whole PC. The CMOS is powered by an extra battery and if the battery  goes down, the CMOS settings are set to the factory defaults. The BIOS  is not only present on the system ROM, but also on peripheral hardwares  such as ATA RAID drive controller, Grpahic cards etc. This is called  Options ROM or Bringy oyur own BIOS. BIOS : Basic Input Outuput System.
 The  bits in DRAMs are venerable and hence there are ECC ( Error code checks  ) or much before a parity check. An extra
  chip had to be used  especially for the parity check.
 The CDRom technology is based on  reflections and amorphous. If the area is reflecting its a 1 and if not  then its a 0
 . Many techniques, chemicals etc has been used for CD-R,  CD-RW etc. since then.
 The USB host controller contains USB root  hub and they can be a max of 127 in number. But not all the USB root hub  is
  routed further as a port on the motherboard. However, USB hubs can  be connected and this would make up for the unused USB Roothub. USB1.1  had two speeds : 1.5 Mbps and 12 Mbps. The USB2.0 has 480Mbps and USB3.0  has 1 Gbps. The optical scanners uses a generic driver called TWAIN (  Technology without any interesting name ). The scanners have grayscale  depth, color depth and optical resolution as the parameters. The color  depth 16 bit means 65535 various variations can be recorded. The optical  resolution says how many dots per inches one can record. The grayscale  is the various gray variations and normally 16 bit is enough.
 The  CDs filesystem is09660 was created because the CD makers wanted to make a  generic filesystem for every operating
 system and not especially for  ntfs, ett3 etc. The ISO image consists of the whole image of the CD  drive. Buffer underrun was a common problem during the CD burning  process as the buffer ( a RAM in the CD drive ) has to be constantly  available with data for the burn process to complete.
 MBR, basic  disks, dynamic disks are spread out within various physical hard drives  and hence there are no partitions,
  but there are volumes. These volumes  can extend to various physical hard drives and various paritions as  well. The hard disk needs file systems because otherwise, a hard drive  is just a cluster of sectors. The formatting process divides the sectors  into cylinders and ultimately partitions and also creates a container (  folder ) in which all the following files would be stored. At the  beginning of each parition, there is a volume boot sector. During the  time of creating the MBR, which is at the first sector of the hard disk (  also called the boot sector), two data structures are created - first  the MBR itself, and then the parition table with information about each  and every partition on the hard disk. The MBR is nothing, but a tinyy  bit of code that takes control of the boot process from the system ROM.  The job of the MBR ( ie the code in the MBR ) is to look into the  parition table for a valid OS. The paritions needs to be set as primary  and then bootable. Not only this, this partition needs to be set as  active. This information is also written in the partition table in the  boot sector.
 In a dynamic disk, MBR and parition tables are still  present due to backward compatibility. However, all the
 infornation are  stored in a hidden partition that takes up the last 1 MB of the hard  drive. EVery parition in a parition table holds a 2 byte value that  describes the parition. In case, the parition table entry read is 42  then it immediately jumps to the last 1 MB and ignores the default basic  disk booting process. In a dynamic disk, it is not required to create  paritions, but simply volumes and the volumes can be spread across  various hard drives for example, there is spammed colume, simple volume,  mirrored volume, RAID 5 volume, Raid 0 volume. The swap parition is  like pagefile which acts as a virutal RAM.
 The minimum file size  that can be stored in a sector is 512 bytes. A file with lesser than 512  bytes takes the entire
  sector. The FAT 16 has hence 65535 entries or  65535 sectors. If each sector is 512 byte, then total size FAT16 can  address would be 65535*512 = 32 MB. The maximum in FAT 16 is 2 GB which  could be achieved by 64 sectors per cluster. In the allocation table,  the sectors are marked either as bad ( FFF7 ) or good ( 0000 ). The  sector size in a hard disk is fixed to 512 bytes, but the clusters can  be made of more than 1 sectors and hence in the file allocation table,  the addressing was done for the clusters and not the sectors anymore.  This helped to address locations on hard disk which were more than 32  MB. Also, a 40 MB hard disk could be cut into varoius paritions and each  parition should be lesser than 32 MB. The end of the file code is FFFF.  Hence for files that spawn through more than one clusters, the FAT are  numbered accordingly till the file is completely stored and this last  bit has the entry in the FAT as FFFF.
 Any file if deleted, is  replaced by a hex code eq to sigma in the FAT. Hence the file is  actually not deleted, but is
  stored on the hard disk. Only the FAT has  been deleted. With FAT32, and the sector size of 512 byte and each  cluster consisting of 1 sector, 2 terabytes can be addressed i.e a FAT32  paritiontable supports upto a parition of 2 TB.
 With NTFS,  redundancy, security, compression, encyption, disk quotas, cluster  sizing was introduced. This is the
 choice currently of most of the file  systems in windows. Currently, we have NTFS3.1 NTFS utilizes an enhanced  FAT called the master file table ( NFT ). An NTFS parition keeps a back  up copy of the most critical parts of the MFTin the middle of the disk,  reducing the cance that a serious drive error can wipe out both the MFT  and the MFT copy. This MFT is immovable and not overwritable. NTFS  provides ACL to each object ( files and folders are treated as objects )  . NTFS also enables compression and encrypting. Only those users can  see the files and folders who have permission to view the files ( ACL )  and the key to decrypt the files and folders. NTFS also allows to adjus  tthe cluster size. By making 8 sectors ( 4096 byte or 4 KB )fit into a  cluster, One can address upto 16 exa bytes hard disk capacity on a  single parition. The NTFS also allows drives to be mounted as folders  during boot up. This means one can simply have another hard drive mount  that hard drive into a NTFS formatted folder. This however happens only  with NTFS5 or higher.
 Surge protection due to lightning. Auto  power factor correction due to harmonics. Power supplies are provided  from
 ATX and have 20-24 pin motherboard connector along with molex, mini  and sata connector. It supplies 5, 3.3 and 12 V. Warm air rises above  and hence in a casing one could pull air from below and exhaust from  above the case. There are tower, mini-tower, mid-tower, The temperature  specifications should not be 25 degrees for example for 500 W which  means the power supply is able to provide 500 W at 25 degrees. As the  temperature increases the performance of the power supply reduces.  almico.com/speedfan.php gives a good insight how the fans are working in  the computer. ATX Tester is a dummy motherboard, so that the power  supply can be tested.
 Motherboards are defined by 3 parameters:  form factor ( AT, ATX, BTX ), chipset ( northbridge, southbridge from  VIA,
 Nvidia, ATI ) and components. There is also another chip called  Super I/O which connects non standard peripherals such as InfraRed,  CardReader, Floppydrive etc. Companies such as Shuttle assemble the  whole casing, chipsets, motherboards etc. Using a POST card , one can  check the motherboard without using any keyboard, video etc.
 RAID: redundant array of independent devices.
 NIC  : network interface card consits of a definite 48 bit or 12 Hex number.  This is a unique number in the world.
 Computers communicate with each  other via frames or packets. The formation of a packet is REceipent MAC  Sender MAC data CRC. The cables connecting the NIC are connected in  various topologies like bus, star, meshed and ring. The cable connected  to the PC should share the same hardware protocol like Ethernet,  Tokenring ( developed by IBM ) , FDDI, ARCNet. The Ethernet cable came  in 3 forms: coaxial, twister pair and fiber optics.
 In the coaxial  cable type the cable type was called 10Base5 ( thick Ethernet ) or  10Base2 ( ThinEthernet ). The
 cables differentiated between the number  of PCs one can hold onto the network such as 100 Pcs or 30 Pcs, the  width of the cable, the Radio Grade such as RG8, RG58, The total length  of the segment such as 50m or 200m. Both thicknet and thinnet used the  Bus topology and hence proper termination was required to avoid voltage  reflections. But still if there was a break in the cable, the  reflections generated and hence with time, the whole network went down.  The ThinNet uses a T connector to connect further to the next PC. The  transciever is built into the network card unlike Thicknet where a  separate Transciever ( module responsible for transmitting and receiving  data and also detecting collision ) was put outside the network card.  The collision detection was required, becuse the packets should be  resent if the collision occured on the bus between two computers sending  packets at the same time.
 Finally UTP ( Unshielded Twisted Pair )  Ethernet, 10BaseT, 100BaseT or 1000BaseT is the cable connection of  modern
 days. The cable type is twisted pair The hardware protocol uses  star topology where all computers are connected to a central element  called hub or a switch. The hub divides the bandwidth, whereas a switch  solves this problem by making each port a separate Ethernet network. The  wires ( either 2 pair or 4 pair - CAT5 upwards ) are twisted with each  other in color coded parts. Even these twisted cables are put into  categories depending on the bandwidth they can survive. Data speed in  paranthesis. CAT1 ( Telephone ), CAT2 ( 4 Mbps ), CAT3 ( 16 Mbps ), CAT4  (20 Mbps ), CAT5 ( 100 Mbps ), CAT5e ( 1 Gbps ) , CAT6 ( 10 Gbps )  Incase the cables are to be connected between two hubs i.e point of a  star, then it has to be connected via a crossovercable. The cross over  cable crosses the 2 and the 3rd pin.
 The UTP is a cable and the  TIA is a standard how the UTP cables are connected to each other. The  connector to connect
  these wires to the NIC is either RJ45 or RJ11 made  by Ma Bell. The star topology with one switch in between and CAT5 cable  can serve 1024 computers and each distance between the point and the  computer to be 100m. The fibre optics technology, which has in total of 2  wires ( one for receive and for sent ) can extend the signal strength  upto 2000m. The fibre optics come in two variants: Mulitmode and  singlemode. In multimode, multiple light signals are emitted usind LEDs  with different angles and hence many signals can be sent. But the  signals disperse over long distances and this technology is better for  relatively short distances. Single mode uses laser lights and hence he  transfer rates are very high.
 In Token ring, the computer neeeds  to acquire a token before sending the data on the bus. This has an  advantage over
 the ethernet because there is no collision detection  scheme. Only that computer can send the data which has acquired the  token. The token ring technology from IBM is still in development and  hence not completely faded over by Ethernet.
 Parallel / Serial port, Firewire and USB connectors are other connections to exchange data between two computers.
 Peer  to peer network is a possiblity where every computer turns into a  server. Normally, there is one server and the
 workstations or nodes get  information from the server. In peer to peer network, all the nodes  behave as servers and exchange data with each other. This technology  however has limited nodes ( around 10 ) . In case one wants to go to a  larger number of nodes, a domain controller is ideal. The domain  controller takes up the task of authenticating once and all the other  services that are in this domain, can be accessed without logging in  explicitly to the servers which are serving the said service. The  authentication takes place over a database like LDAP, Active Directory  etc.
 Since the computers talk to each other via NIC that has a  unique MAC address, it is not advisable to hardcode the MAC
 address in  the application programs. It is better to use the hostname of the  computer where the data needs to be sent. This is because, the network  card can be replaced by a new at any time and then all the programs with  a hard coded mac address wont work. There are queries during the start  of the network where the hostname and mac address lookup table is  refreshed.
 Finally, we have NIC ( hardware ) , TCP/IP ( protocol )  and Client ( an application software ) Any network address
 must provide  two piece of information : first is the location of network where the  machine is present and the second is the location of the machine. In a  TCP/IP network, the systems done have names, but use IP addresses and is  the unique identification number to locate the node. Various classes,  Class A, Class B, Class C. In class A the first octet is used to  identify the network and the rest identifies the host. Class B has the  last two octets as hosts and class C has only the last i.e only 255  machines as hosts. IP address such as 127.0.0.1 to 127.255.255.255 is  used for network testing and is known as loopback. Normally only  127.0.0.1 is used. Each network class Class A, B and C has their own  private network range. Class A has a private network range from 10.0.0.1  to 10.255.255.254. Class B has a private network range from 172.16.0.1  to 172.16.255.254. Class C has the range from 192.168.0.0 to  192.168.255.254 for nmanually configured addresses and 169.254.0.1 to  169.254.255.254 to accomodate the automatic private IP addressing.
 The  above distinguish between network address and host addresses is done in  the software using subnet. The subnet and
  the ip address is logically  anded to get the network address. The rest is the host address.
 There  are various TCP IP services and one of the most famous is HTTP. Other  services such as telnet also fall under
 the umbrella of TCP/IP. The host  is not expected to know the routing of the destination and hence it  just sends the packets to the default gateway ( router ) which further  forwards it to another router till the packet reaches the router which  has the knowledge about the machine where the packet is intended to be  sent. However, it is difficult to remember the ip addresses all the time  and hence one tends to write all the ip addresses nd the hostnames in a  lookuptable called the DNS server.
 In case the computer is unable  to obtain an IP Address, the APIP ( automatic private ip ) assigns an  IP address in
 the range 169.254.0.0 to 169.254.255.254. However, this  computer with this IP 169.254 can only communicate with an similiar IP.  The IP address is confirmed by the network ( all the computers ) by not  responding to the broadcasts from this IP address which means, noone  else has this IP address automatically and randomly generated by the  APIP module. In case any other computer responds, then the APIP module  tries with a new IP address.
 A computer can either run in a  Wireless Access Point mode or a client mode. But recent drivers can  convert the
 wireless card into both using the software. The wireless use  radio waves and they are interfered because of other radio devices such  as walkie talkie, baby monitors, refrigerators aircons etc. The speed  of the wireless transfer depends on the distance and the objects between  the WAP and the wireless nodes. The wireless nodes negotiates with the  WAP by downtrodding the speeds till no packet loss is visible. The SSID (  Service Set identifier ) is the network name and this name is included  in the header of every data packet broadcast in the wireless networks  coverage area. The data packets that lacke the correct SSID name in the  eader ar erejected. The datapackets transfer is encrypted with WEP, WPA,  or WPA2 encryption. The WEP ( Wired Equivalent Privacy ) uses 40bit or  104 bit encryption to scramble the datapacket. However it is not end fo  end enryption and the mac address, username, password etc are  transferred in clear text. This issue was addressed and hence WPA ( Wifi  Protected Access ) was written. The WPA has ecnyption key integrity  feautres and user authentication through the industry standard EAP (  Extensible Authentication Protocol ). The WPA2 further has yet better  encyption algorithm AES.
 There are two modes: AdHoc mode and the  Infrastructure mode. In the adhoc mode all wireless nodes are connected  to
 each other and in the infrasturcutre mode the wireless nodes are  connected to a wired network segment. Hence the adhoc mode is alsot  called peer to peer mode with each wireless node in direct contact with  eacho other node in a decentralited free for all, best suited for  business meetings and study group.
 The data is sent over the  wireless protocol using the spread spectrum broadcasting methods. There  are two methods and
  one is DSSS and the other is FHSS. The direct  sequence spread spectrum sends data on different frequencies at the same  time and the FHSS sends data on one frequency at a time, constantly  shifting ( hopping ) frequencies. For example in Bluetooth, which uses  2.45 Ghz, there are 79 frequencies for the FHSS method to choose from.

 Printers
 Dot matrix printer, Dye-sublimation printer, Inkjet, laser, thermal, solid-ink.
 Inkjet: works be ejecting ink through tiny tubes.


 ====== Probability and Statistics: DeGroot, Schervish ======


 Sample Space

 Empty Set

 Finite and Infinte Set

 Unions, Intersections, Complements, Disjoint Events

 Permutation

 Number of samples without replacement. In this case the number of elements for subsequent sampling keeps decreasing.
 Hence if there were n elements in the beginning, there would be n-1 to choose from in the next.

 It is possible that only 3 samlings is done for 10 elements. That means, the number of possible events is n*(n-1)*(n-2)
 . To make it simpler, the equation is converted to n*(n-1)*(n-2)*.. *(n-k)..*1 / *(n-k)..*1. The above equation is written as n! / (n-k)! . The ! mark is called factorial.
 k
 In case all the elements are used for determining the sample set, then it is simply n!. Example if all the n books are
 to be arranged, then there are n! ways to do so.

 Sampling with replacement:

 In case, the elements are replaced back in the element set, then the number of elements for each event remains equal.
 And hence if there are  events, then there would be n^k possibilities to build the sample set.

 For eample, if a box contains n balls with unique numbers. And we have to determing the probability of picking k unique
  balls one by one. Ofcourse, since the ball picked up is put back again in the box, there is a possibility that we would pick up that ball again. Hence, in the event set, we will have (n-k)! ways to pick up unique balls in k trials.

 The probability hence becomes, (n-k)! / n^k.

 Sampling with replacements ( but this time not one but k balls are picked ) on one go. In the previous example, there
 was one ball picked, but k different events. In both the cases, the final number of balls that are picked in the end is equal. Only the way differs. For example, 6 balls picked up one by one with replacement or 6 balls in one shot. In both the cases, 6 balls are picked.

 The first case is called Permutation and the second case leads to Combination, because the order of the picking has
 vanished.

 In case the balls are picked up at once, then ofcourse the probability that all would be unique is 1 ( all of them are
 unique in the box ). This can be proved hence.

 The total number of samples for picking up k balls from the set of n balls is (n-k)!/k!
 The total number of samples for picking up k unique balls from the set of n unique balls is also (n-k)!/k!

 This leads to a new term "groups". The elements in the sample set can be grouped  in k identical elements and n-k
 identical elements for a bionomial problem

 For a multinomial problem, there can be k groups of identical elements, l groups of identical elements and m groups of
 identical elements. The sum of k,l, and ml is equal to n.

 In an bionomial problem, it is irrelevant if you select 4 balls or select 6 balls out of the set of 10 balls. The
 sample set for the first case would be 10C4 and the second case 10C6. They are mathematically equal. The sample sets can be also be written as ( 10 4 ) or ( 10 6 ).

 Similarly, if a coin is tossed 10 times, and the probability of obtaining exactly 3 heads is equal to the probabilty of
  obtaining exactly 7 tails. It has to be noted that the total number of samples in both the cases remains the same ie.2^10 ( with replacement )

 If we consider the total number of samples without replacement, then ofcourse the number of samples decreases
 tremendously, because we have lesser data to choose from.

 Example: 15  boys and 30 girls and 10 students are to be selected. The probability that exactly 3 boys would be
 selected would be:

 Total samples = ( 45 10 ) and

 Exactly 3 boys would be = ( 15 3 ) ( 30 7 )

 In the above example, we divided the finiet set into 2 disjoint subsets. i.e boy and girls.

 In the next section, we will divide the finite set into k disjoint subsets. i.e 4 black, 3 white, 5 blue boys, 10
 white, 4 black girls.

 The final formula is ( total number of elements, number of group elements one by one ) . This is just the total number
 of outcomes. To find out the probability that a rule would happen, one needs to determine the outcomes of a rule ( for example, two of the stuents would be white ) and then calculate the probability of the rule.

 Union of disjoint events

 In case the events are disjoint ( i.e they do not influence the hapenning of events in another set ) then the union of
 all the events is given by:

 A + B -AB

 Similarly

 A+B-C -(AB + AC + BC ) + ABC

 Generalizazion:

 €A(i) -€A(i)A(j) + €A(i)A(j)A(k) ..... -A(i)A(j)...A(n)

 Let A(i) be a set where a letter is put in the correct envelope. The sum of all the event sets would be 1 which means,
 the first event A(1) is to place the first letter in the correct envelope, the second event A(2) is to place the letter in the correct envelope. The sum of all the events means that the letter has been put in the correct envelope. The sum is 1 because it consists of all the events ( disjoint , overlapping etc ) . This needs to be subtracted subsequently from this value.

 Probability that two of the letters would go into the right envelopes is nC2*(1/n*(n-1))

 Three:
 nC3*(1/n*(n-1)*(n-2))


 Independent Events

 Conditional Probability

 Bayes Theorem

 Markov Chain






 ====== LPI Linux Certification, O'Reilly, Jeffrey Dean ======


 cut,  expand ( tabs to spaces ), fmt ( specify width, concatenate files ),  head ( -l lines ) , join ( -j field file1
 file2 ) ,nl ( number the lines  ) od ( dump files, -t x is hexaecimal ), paste ( column wise  concatenate two files ), pr ( hw the print would look like with page  number, date and time etc. ), split ( large files into smaller chunkes  row wise ), tac ( reverse cat ), tail ( -n lines ) , tr ( translates  char from string 1 to string 2 ), wc ( count of words , c character, l  line, w word), xargs ( -n 1 ), sed 'syd/pattern/replace/[g file1 tee,  ps, pstree, top, pa -l ( higher priority number, higher resources ),  nice ( positive number lowers prioirity ), nice --10 top, renice, bg,  fg, jobs,
 Directory is an object intended to contain other  objects. File is an object intended to contain informstion cp -p (
 preserve all information including date, time, owner, permission etx. )  *, ?, [charcters], [!characters], [range], [!range], {frag1, frag2,  frag3}
 Stdin : file descriptor 0; default is keyboard but csn be  overridden with < stdout: file descriptor 1; default is
 console, but  csn be overridden with > or 1> stderr : file descriptor 2; default  is console, but can be overridden with 2> one liner for both stderr  and stdout; cmd > file 2>&1
 kill 9 unconditional, 15  nice termination, kill -15, kill, kill -sigterm, kill -term etc. all  kills with the IPC
 sigterm ( case insensitive ) kill -l gives a list of  signals. File globs are wild cards such as *, ? etc. grep : global  regulsr expression print ( -v inverts, -i ignores, -c displays count )
 ->  character, ? -> pre regex, . -> single character, regexpr{m,n}, \  -> this shud be a word, s, 11,20s,
 /d->deleteline,  11,20y/abc/@@@/ primary partition minimum 1 and max 4 on a hard disk.  primary paritions have a fs. only 1 extended allowed on a physical disk.  extended do not have a fs, but contains logical parition. logical  partition can be 1 to 12, logical always stars from 5 because 1 to 4 is  reserved for primary/extended.
 mkfs -t ext2 -L label -cv /dev/hda3 mkswap /dev/hda5 df ., df -i, df -h, du -s, du -Ss, du -csh /local/, du -d0 -h
 /local/  mkfs and fsck is a front end to filesystems. Superblock contains  information which describes the filesystem. 1, 1+8192, 1+8192*2, and so  on. fsck -N shows the mounted paritions and also their fs. fack -A  checks all the filesystems in /etc/fstab. The last parameter is 0, 1 or 2  which says if the fs should be checked or not when fsck -A is invoked.  umount -a -> unmounts all in /etc/mtab mount -a, many options such as  async, defaults, nouser etc... quota -uv username
 /etc/inittab  umask -a ; file:0x2; dir: 0x22 SUI, GUI, sticky,rc.sysinit, rc.local,  shutdown -h now, shutdown -r now,
 apropos, locate, updatedb.conf ->  add and prune paths, init runlevel, lilo linux runlevel, slashdot.org  /usr/local/man, /etc/man.config, man -d mkfifo usermod -G sales agrawal  etc/shadow, etc/gshadow add, mod, del, pwconv, pwunconv, grpconv,  grpunconv, chage -l username etc/skel -> etmplate home dir.  /etc/syslog.conf -> local5.* /var/log/local5 is invoked by logger -p  local5.info "fffff" /etc/logrotate.conf
 pag 180 - cron tarballl  shared library ld.so has the list of directories which consits of shared  libraries. /etc/ld
 .so.cache, ld.so.conf contains all the paths which is  looked by ld.so. ofcourse ldconfig needs to be run to update th  eld.so.cache dpkg -s package dpkg -S file is very powerful, dselect,  alien
 modinfo -p -a -d
 modprobe -c
 modprobe -l -s -v
 /etc/modules.conf modules.dep file depmod -a recreates modules.dep file.

 make  defconfig ( make a config eith current architecture ) . one can also  simply copy .config to the current
 directory. .config, system.map and  vmlinuz naming . major.minor.patchlevel 3.13.0-74.114 : even minor  stable, odd minor development.

 ll /boot /lib/modules clean, make  xconfig, dep, all, bzImage, modules, modules-install, install bzip2 -dc  .bz2 |
 patch -p1 --dry-run alternate method is to make debian packages.

 fakeroot make-kpkg -j N --initrd --append-to-version=-WEIKAS  kernel-image kernel-headers

 When done, the kernel image and header files  will be ready as debs in the parent directory; you can simply install
 them with sudo dpkg -i, which will also take care of adding GRUB  entries, etc. sudo apt-get install kernel-packages man installkernel  grub uncompresses vmlinuz in memory.

 Step # 6: Create an initrd image
 Type the following command at a shell prompt:
 cd /boot
 mkinitrd -o initrd.img-2.6.25 2.6.25
 initrd images contains device driver which needed to  load rest of the operating system later on. Not all computer
 requires  initrd, but it is safe to create one.
 /etc/printcap consists of  all the printers supported by your computer. Raw input data is  transöated by a filter
 program into a standard Page Descriptor Language  which is a form of a PS for linux. PS data is not printed itself but
 is  interpreted as a program to be executed by a post script interpreter.  Conversion of various formats into PS is
 called as filtering.  magicfilter, APSfilter are two programs which does this.
 id -un, id -Gn
 protocols: TCP, UDP, IP and ICMP. IANA decides the port number. The port numbers known by my system is in /etc/services
 1-1023 privilige, 1024-65535 is unpriviliged.
 dig  ( name servers ), ping, ftp, telnet ( establish connection to host with  port number defaults to 23 ), traceroute
 ( till hostname ), whois ( the  host name and fnd the information from the database defautls to  InterNIC .. rs
 .internic.net )
 /etc/hosts : contains simple mappings betweeen IP addreses and names and is used for name resolutsion )
 /etc/resolv.conf contains IP addresses of nameservers.
 /etc/nsswitch.conf
 netstat  -i, netstat -pant, netstat -r or route, 0.0.0.0 is the default route.  genmask 255.255.255.255 for the host (
 for example if eth1 has to send  data to a particular host like raspberry ) - here the flags should be  UH. Route to
 local subnet / network address has a GENmask of  255.255.255.0 or something else. When no other matches in routing
 table,  the default route is taken. This is shown by a genmask of 0.0.0.0
 ifconfig eth1 192.168.242.161 up
 route add -net 192.168.242.0 netmask 255.255.255.0 gw 192.168.242.1 eth1/eth0 in both raspberry and my machine.
 route add -host 192.168.242.161 eth1,
 Delete previous default gw sudo route del default
 Add route to the router. route add -net 192.168.1.0 netmask 255.255.255.0 dev wlan0
 Add  default gw. route add default gw 192.168.1.1 dev wlan0, sudo route add  -net 0.0.0.0 gw 192.168.1.1 netmask 0.0.0
 .0 dev wlan0 -> for default  gw

 dhclient sends broadcast to the netwrok to discover the dhcp  server. The dhcp server responds by offering an ip
 address. The client  chooses one fo the servers and broadcasts the ack. The selected server  logs the connection with
 the client and responds again with an ack. the  other servers are declined by the client. The broadcast is done in the
 subnet. If the subnet does nto have its own dhcp server, then the client  message needs to be relayed through routers.
 This is called a DHCP  relay system. This method of relaying can centralize DHCP management in a  large routed
 environment for example eduroam. The dhcp server stats  dhcpd process at boot time and listens for incoming DHCP
 request broadcats. On the server side this is present in /etc/dhcpd.conf.

 In  order to reduce the nmber od daemons for each port, inetd was created (  internet superdaemon ). The inetd starts
 for example telnetd, and the  telnetd terminate when there is no more connection with the client. This  saves a lot of
 CPU resources. Not everything is served by inetd. For  example, apache webserver deals the connection on its own,
 because it  needs to run all the time. The conf is present in /etc/inetd.conf.  hosts.allow and hosts.deny have rules,
 where the TCP knows to whom  should the access be given.
 NFS - /etc/exports and write the  directories you want to share. On the client side, mount -t nfs  server1:/home
 /mnt/server1. This could be automount by putting the entry  in /etc/fstab. Similarly SMB is a file sharing protocol.
 DNS  servers run a program called resolver. The prio is /etc/hosts, NIS, and  then the DNS database ( /etc/resolv.conf.
 localised database with local  authorities like universities etc. ). named is another daemon, which  caches the
 mapping in the local database and it grows with time. This  speeds up the resolution. Non authoratitve answer means
 that the  resolution was found from the local cache.
 host, nslookup, whois, dig

 Interrupts can be seen using cat /proc/interrupts


 ====== Signals and Linear Systems - Gabel, Roberts ======


 ====== Advanced Engineering Mathemtics - Mc Graw Hills. ======




 ====== History of technology ======


 ====== Multi-Sensor datafusion with Matlab,  Jitendra R Raol ======


 ====== Models of data fusion process and architecture. ======



