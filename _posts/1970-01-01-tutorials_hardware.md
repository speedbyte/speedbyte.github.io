---
layout: post
title: "tutorials_hardware"
date: 1970-01-01
---






====== SDRAM ======


synchronous dynamic RAM. ( waits for the clock signal before reacting to control inputs. ). This is also a difference with DRAM. The DRAM does not have a syncronising control hardware circuit. The important parameter to look in SDRAM is latency time ( no. of clock pulses SDRAM waits before it reads the data from the memory ) . Hence SDRAM are rated according to their maximum clock rate and their read cycle time.
Thus CAS Latency (CL) -- same as latency ....is the time (in number of clock cycles) that elapses after the memory controller sends a request to read a memory location and before the data is sent to the module's output pins.
CAS Latency only specifies the delay between the request and the first bit
Achtung! - must see that the CAS affects only the first incoming bit, the rest of the bits are guided by clock speed.
CL3 = 5.0 ns, CL2.5 = 6.0 ns
CL ( clock latency ) = (on this clock speed only) .. when there is another clock speed, the CL can be different.

DIMM and SIMM are the way the memory modules ( xxRAM integrated circuts ) are loaded on a single chip as an array of RAMS
SODIMM is a smaller DIMM which is used in laptops. The class of xxRAM can be identified by looking at the notch.

When a computer tries to access data in the SDRAM, the CPU being quite faster than the memeory, has to wait, till the SDRAM finishes its process. SDRAM latency is often measured in front side bus clock cycles.
The bottleneck between the CPU and the memory is continuously increasing, because CPU speed is increasing and the memory sizes are also increasing. Cache has reduced this load a little bit though.

latency values given as 2.5-3-3-5  ( all are always mentioned in clock cycles ) would indicate tCAS=2.5, tRCD=3, tRP=3, tRAS=5. (Note that .5 values of latency (such as 2.5) are only possible in Double data rate RAM, where two parts of each clock cycle are used)


Pin 2 = CAN_L ( Can Low )  - color is normally yellow.
Pin 3 = CAN_GND
Pin 7 = CAN_H ( Can High ) color is normally green.
Pin 9 = CAN_V+(Optional)




BaudPrescaler, BRP = 00001110
1 + 1*0 + 2*1 + 4*1 + 8*1 + 0 + 0 + 0 + 0 = 15
BRP = 15Mbit / second
RES = 00000
Edge Rescynchronisation Mode: This bit selects the sync mode with the received data stream on the CAN bus.
ERM = 0 , Resync on falling edge only
Synchronisation Jump Width SJW, This determines how many units of TQ a bit is allowed to be lengthend or shortened when resncy with the received data stream on the CAN Bus.
= 01 = 1 + 1 + 2*0 = 2 TQ

Sample Point Setting SAM = 0 = Only 1 Sample at the sampling point. ( There is a definite sample point )
Time Segment 1, TSEG1 = PROP_SEG + PHASE_SEG_1
0101, 1 + 1+ 2*0 + 4*1 + 0 = 6 TQ

Time Segment 2, TSEG2 = PHASE_SEG_2
010 , 1 + 0 + 2*1 + 0 = 3 TQ

Bit Time = TSEG1 + TSEG2 + 1 = 10

Bit rate = ICLK / ( BRP * Bit Time ) = 15 / ( 15 * 10 )

TQ = BRP / ICLK
= 15 / 60 Mhz = 

Microcontrollers (MCU) are complete computer systems on a chip. They combine an arithmetic logic unit (ALU), memory, timer/counters, serial port, input/output (I/O) ports and a clock oscillator. Most microcontrollers include a 4-bit, 8-bit, 16-bit, 32-bit, 64-bit, or 128-bit data bus. The number of serial channels and I/O ports varies among devices. Serial interfaces include controller area network (CAN), inter-integrated circuit (I2C), serial peripheral interface (SPI), serial communications interface (SCI), universal serial bus (USB), universal asynchronous receiver transmitter (UART), and universal synchronous/asynchronous receiver transmitter (USART). Common features include watchdog timers, direct memory access (DMA) channels, pulse width modulation (PWM) channels, power saving modes, oscillator safeguards (OSG), low frequency auxiliary oscillators (LFAO), low voltage detectors (LVD), readout protection, and liquid crystal display (LCD) drivers. Converters with an 8-bit, 16-bit, 24-bit, or 32-bit resolution are commonly available. Some microcontrollers include analog-to-digital converters (ADC). Others provide digital-to-analog converters (DAC). 

RAM size, ROM size, and ROM type are important specifications to consider when selecting microcontrollers (MCU). Random access memory (RAM) can be read from or written to in a non-linear manner, but does not retain data when power is removed. Read-only memory (ROM) contains pre-programmed data, is either unchangeable or requires a special operation to overwrite, and retains data in memory when power is removed. There are several types of ROM. Mask ROM is a static form of memory that is programmed during fabrication with a special mask that contains the customer code. Erasable programmable read-only memory (EPROM) can be erased through exposure to ultraviolet light and then reprogrammed. Similarly, electrically erasable programmable read-only memory (EEPROM) can be erased electrically and then reprogrammed. Flash, a popular form of EEPROM, can be erased and reprogrammed in blocks instead of one byte at a time. Other types of ROM include factory advanced service technique read-only memory (FASTROM) and one-time programmed memory (OTP).

General specifications for microcontrollers (MCU) include clock speed, interrupts, power characteristics, operating range, operating temperature, and life cycle stage. Clock speed, the maximum frequency, is measured in megahertz (MHz). Interrupts are asynchronous electrical signals that are transmitted from peripherals to a microprocessor. Power characteristics include supply voltage, supply current, and power dissipation. Some microcontrollers are suitable for commercial, industrial, or automotive applications. Others are designed for military specifications (MIL-SPEC). Operating temperature is a full-required range that is typically measured in degrees Celsius (C).  Life cycle stages for microcontrollers (MCU) range from introduction, rapid growth, and maturity to saturation, decline, phase out and removal. 

Microcontrollers (MCU) are available in a variety of integrated circuit (IC) package types and with different numbers of pins. Basic IC package types include ball grid array (BGA), pin grid array (PGA), land-grid array (LGA), chip-scale package (CSP), quad flat package (QFP), single in-line package (SIP), and dual in-line package (DIP). Many packaging variants are available. For example, BGA variants include plastic-ball grid array (PBGA), tape-ball grid array (TBGA), and multi-chip module plastic ball-grid array (MCM-PBGA). PGA variants include ceramic pin-grid array (CPGA) and plastic pin-grid array (PPGA). Common chip-scale packages are flip-chip chip scale package (FCCSP), stacked chip-scale package (SCSP), and ultra chip-scale package (UCSP). QFP variants include low-profile quad flat package (LQFP) and thin quad flat package (TQFP). DIPs are available in either ceramic (CDIP) or plastic (PDIP). Other IC package types for microcontrollers (MCU) include small outline package (SOP), thin small outline package (TSOP), and shrink small outline package (SSOP).


UART:

The TTL logic differes from Rs232 logic in the following way.
The bits are completely inverted and has a wider range to transfer data on a longer range.
The power to the wider range is provided by the Rs232 chip or the computer which is ofcourse not possible in the case of TTL.

0 to 5 V TTL corresponds to -13 to 13 V in Rs232. The baudrate is always bits per second ( bps )
Also, the 5 V or 3.3 V corresponds to the Vcc of the microcontroller.

  
Tcp ip
SPI
SPI is a bus like I2C, but it's only really usable with a single master. The bus has three lines - two data lines and a clock - but each slave needs a seperate enable line from the master, making it costly on pins compared to I2C.
However, it tends to support higher data rates. So a typical design might have an I2C interface for the pushbuttons and LEDs and configuration EEPROM, but an SPI interface to a mass storage device and an MP3 decoder.
SSH

Flash Memory :

At49BV64616

Parameter             Value
Density                  64M
Organization         4M x 16
Speed                     70 ns
Vcc (V)    2.7-3.6


Serial Protocol:

TTL Logic
3.3 V to 0 V
Start bit = 0
Data
And Stop Bit = 1
After this the voltage remains high till the next start bit.


Rs232 from the computer:
+9V to -7V.
The values are inversed here.

At Chromoflex the following voltage levels were measured:
9.7V to -8.8V

Even if the Serial communication between the two computers are of different baud rate the communication would occur , but the sending and receiving text would be garbage.
How to setup a communication between the two computers :
Open hyperterminal , configure the relevant port and pass text values.


Working Constellation

I send data over the serial connector on the PC side. The serial driver sends the data on Pin 3. On the embedded side, this pin should be connected to the Rx Pin of the serial chip.
For the communication to take place both the PC and the embedded side should have a common ground.

In my constellation, there is no Tx Pin from the embedded side.
So, to sniff the data, I use another Db9 connector and connect the Pin 3 to the Pin2 ( Rx ) with a cross cable.
That means, whatever is being send on the

on the PC side,
Pin 2 = 0V ( Rev Data )
Pin 3 = 10V ( Tx from the computer )

On the Level Convertor
Rx - 3,3V
Tx - 3,3 V

Connected to the PC, the voltage is 9 V ( on the Tx pin of the ) if I am sending 0xFF. If no informtion is there, then it is -7V.





Schematics for the SparkFun ( level shifter )

Ok help!!!! EE 101 help needed. how in blazes does this thing convert the TTL tx signal to 12V??? If VCC is 5V, I can’t see how it creates the 12V from the 5V VCC from the schematic.
It doesn’t really convert VCC to 12v. It simply pulls the output (pin 2 on the DB9) up to the level of VCC for “mark”. To get the lower negative voltage for “space” it uses a clever little trick of stealing and storing the negative voltage from the connected host coming in on pin 3. This is done with the diode D1 and the capacitor C1 (note how the capacitor is installed with the + side connected to ground). This negative level is then just allowed to feed back out pin 2 via R1 to the connected device when not pulled up by Q1 for a “mark”. If the connected devices does not supply a negative “space” signal then it probably doesn’t require a negative “space” just a voltage level around 0v or below for “space” and above 3v (even as low as 1.5v will work, from my experience) for “mark” as per EIA-232 specification rather than the old RS232 spec of +/- 12v.
BTW. I could be totally wrong on this too.


It uses the transmitted signal input from the PC on the DE-9 connector (“RS-In” signal on the schematic) to charge a 10 uF capacitor (C1) through a diode (D1). The way it is connected, the capacitor will be charged produce a negative voltage with respect to ground. This voltage is made visible on the DE-9 transmit line (“RS-Out”) through a weak (10 K ohm) pull up resistor. The PNP transistor in U1 (the transistor with its base connected to the TTL side RX-I line) overwhelms the weak pull up when RX-I is low, pulling the RS-Out line up to Vcc (+5 V, +3.3 V, or whatever the TTL side device provides).
Therefore the “RS-232” outputs will range from, for a mark (1) bit, approximately 0.7 V above the negative voltage provided by the PC’s output signal (0.7 V drop due to the diode forward voltage drop); and for a space (0) bit, the signal will be Vcc (5 V, 3.3 V, or whatever).






CAN

http://microcontroller.com/learn-embedded/CAN1_sie/CAN1big.htm

 ••An Error Frame is generated by any node that detects a bus error. The Error Frame consists of 2 fields, an Error Flag field followed by an Error Delimiter field. The Error Delimiter consists of 8 recessive bits and allows the bus nodes to restart bus communications cleanly after an error. There are, however, two forms of Error Flag fields. The form of the Error Flag field depends on the “error status” of the node that detects the error.
                ••If an “error-active” node detects a bus error then the node interrupts transmission of the current message by generating an “active error flag”. The “active error flag” is composed of six consecutive dominant bits. This bit sequence actively violates the bit stuffing rule. All other stations recognize the resulting bit stuffing error and in turn generate Error Frames themselves. The Error Flag field therefore consists of  between six and twelve consecutive dominant bits (generated by one or more nodes). The Error Delimiter field  completes the Error Frame. After completion of the Error Frame bus activity returns to normal and the interrupted node attempts to resend the aborted message.
                ••If an “error passive” node detects a bus error then the node transmits an “passive Error Flag” followed, again, by the Error Delimiter field. The “passive Error Flag” consists of six consecutive recessive bits, and therefore the Error Frame (for an “error passive” node) consists of 14 recessive bits (i.e. no dominant bits). From this it follows that, unless the bus error is detected by the node that is actually transmitting (i.e. is the bus master), the transmission of an Error Frame by an “error passive” node will not affect any other node on the network. If the bus master node generates an “error passive flag” then this may cause other nodes to generate error frames due to the resulting bit stuffing violation.
-next-


PLL
A microcontroller has a 14.756 MHz crystal but we want it to run at a higher MHz
The formula is given in the manual.

The particular register is given a name in the memory mapped header definition file.
Hence PLLCFG = 0x23
To load the PLLCFG register, we must use the 0xAA and 0x55 write sequence.
PLLFEED      = 0xAA
PLLFEED      = 0x55



USB:


In computer hardware, a host adapter or host bus adapter (HBA) connects a host system (the computer) to other network and storage devices. The terms are primarily used to refer to devices for connecting Fibre Channel and SCSI devices (see SCSI host adapter), but devices for connecting to ESCON, Ethernet, and other systems may also be called host adapters. Recently, the advent of iSCSI has brought about Ethernet HBAs, some including TCP Offload Engines.





In a network, the master scheduler controls the data traffic. If data is to be transferred the requesting computer sends a message to the scheduler, which puts the request into a queue. The message contains an identification code which is broadcast to all nodes of the network. The scheduler works out priorities and notifies the receiver as soon as the bus is available.

The identified node takes the message and performs the data transfer between the two computers. Having completed the data transfer the bus becomes free for the next request in the scheduler's queue.

Bus benefit: any computer can be accessed directly and message can be sent in a relatively simple and fast way. Disadvantage: needs a scheduler to assign frequencies and priorities to organize the traffic.


Examples of internal computer buses
                
Parallel

    * CAMAC for instrumentation systems
    * Extended ISA or EISA
    * Industry Standard Architecture or ISA
    * Low Pin Count or LPC
    * MicroChannel or MCA
    * MBus
    * Multibus for industrial systems
    * NuBus or IEEE 1196
    * OPTi local bus used on early Intel 80486 motherboards.
    * Peripheral Component Interconnect or PCI
    * S-100 bus or IEEE 696, used in the Altair and similar microcomputers
    * SBus or IEEE 1496
    * VESA Local Bus or VLB or VL-bus
    * VMEbus, the VERSAmodule Eurocard bus
    * STD Bus for 8- and 16-bit microprocessor systems

Serial

    * 1-Wire
    * HyperTransport
    * I²C
    * PCI Express or PCIe
    * Serial Peripheral Interface Bus or SPI bus
    * USB Universal Serial Bus
    * FireWire i.Link or IEEE 1394

Examples of external computer buses
Parallel

    * Advanced Technology Attachment or ATA (aka PATA, IDE, EIDE, ATAPI, etc.) disk/tape peripheral attachment bus
      (the original ATA is parallel, but see also the recent development Serial ATA, below)
    * Centronics parallel (generally connects single device, occasionally 2 daisy-chained)
    * HIPPI HIgh Performance Parallel Interface
    * IEEE-488 (aka GPIB, General-Purpose Instrumentation Bus, and HPIB, Hewlett-Packard Instrumentation Bus)
    * PCMCIA, now known as PC card, much used in laptop computers and other portables, but fading with the introduction of USB and built-in network and modem connections.
    * SCSI Small Computer System Interface, disk/tape peripheral attachment bus

Proprietary

    * Floppy drive connector

Examples of internal/external computer buses

    * Futurebus
    * InfiniBand
    * QuickRing
    * SCI

    * Bus contention
    * Front side bus
    * Address bus

ISA = used to transfer data between the memory and the device and controlled by the DMA controller.
SCSI

  


====== I2C ======

The  I2C bus is used to send data from one peripheral to another usually  within the motherboard. It operates only with two data lines that are  bidirectional. One is the clock ( SCL ) and the other is the data ( SDA  with 7 bit addressing ) . The modes are master and slave. However there  can be multimaster or multislave. The master and slaves can even  exchange roles. The bandwidth of the I2C bus ranges from 10 to 100 KHz.  I.e it takes 1 second to send 100000 bits or 10000 bytes. This is a  round off because there are also start / stop bits and other protocol  headers that eat up the bandwidth.
The start of the communication  takes place when the master sends a start bit followed by 7 bit slave  address and either a 0 to write and 1 to read from the slave. The slave  sends an ACK after every byte is has received. The master does the same  thing, in case it wants to read data from the slave. During reading, it  sends ACK after every byte recieved, but it can also end the reading and  become a transmitter by sending a stop bit instead of a ACK. This stop  bit is the same as NACK i.e SDA Low to High during the clock latchings.



Hardware

Difference between a battery and a capacitor:

The battery and the capacitor have similiar functions. They give away energy and can store energy. The only difference is that the battery has a constant voltage and the capacitor can 
only give away energy when there is a change in the voltage i.e if the voltage remains constant, then the accumulated charges on the capacitor does not move.

Transisitors:

The essential usefulness of a transistor comes from its ability to use a small signal applied between one pair of its terminals to control a much larger signal at another pair of terminals.
Alternatively, the transistor can be used to turn current on or off in a circuit as an electrically controlled switch, where the amount of current is determined by other circuit elements.
The amount of the voltage drop between the base and the emitter depends on the material the transistor uses and is a constant. 
By controlling the number of electrons that can leave the base, the number of electrons entering the collector can be controlled. The transistor can be hence thought of a water dam, where one the water between
base and emitter is blocked, it has no other choice but to force itself out from the base collector in a reverse biased mode.

CAN Controller:

Differential CANH and CANL. i
Switch = Data Link Layer
Router = Network Layer     





