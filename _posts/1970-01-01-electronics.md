---
layout: post
---

Mrs Anasuya Kalavar
Electronics - Principles and Applications


64 bit machine does not mean it will have 64 bits of data lines. It can have, but at the current architecture it is just 48 bits.

The 32 bit and 64 bit architecture means that 32 and 64 bit is the register  size. Or basically the ALU can handle 64 bit in one cycle.
In case the byte needs to be addresse, then a logical and is done on the whole register to extract the byte.

SATA and PATA ( IDE ) 
The older OS do not have drivers for AHCI mode whule communicating with the SATA interface of the hard drives, hence it is important to fool the OS by making the interface look like a PATA ( IDE ). 
This can be done by changing the SATA mode to Legacy / Compatibility ( IDE ) . 
Once the installation is done, the OS drivers can be updated and then it is possible to change the BIOS settings to AHCI mode


32 bit machine has DDR2 and the data bus width is 32 bit.
64 bit machine has DDR3 and the data bus width is 64 bit.
Also the form factor can be different. 32 bit can be SODIMM and the 64 bit is Chip.
