## Overview

This repository covers the design of my custom take on the Teensy 4.1 from PJRC. (Link Teensy 4.1). I took inspiration from (insert inspired board) who incorporated usb-c rather than the intended USB-Micro, but lacked the SD slot, expandable RAM and flash memory, and PHY Ethernet IC and RJ45 Connection Like the original. 


<img src="https://github.com/Wierdwizard2587/Custom-Teensy-4.1-PCB-Design/blob/main/Images/IMG_0804.jpg" data-canonical-src="https://github.com/Wierdwizard2587/Custom-Teensy-4.1-PCB-Design/blob/main/Images/IMG_0804.jpg" width="275" height="400"/><img src="https://github.com/Wierdwizard2587/Custom-Teensy-4.1-PCB-Design/blob/main/Images/IMG_0723.jpg" data-canonical-src="https://github.com/Wierdwizard2587/Custom-Teensy-4.1-PCB-Design/blob/main/Images/IMG_0723.jpg" width="275" height="400"/><img src="https://github.com/Wierdwizard2587/Custom-Teensy-4.1-PCB-Design/blob/main/Images/IMG_0728.jpg" data-canonical-src="https://github.com/Wierdwizard2587/Custom-Teensy-4.1-PCB-Design/blob/main/Images/IMG_0728.jpg" width="275" height="400"/>



This Design, following the Teensy 4.1 official Schematic Features a 6 layer design with dedicated GND and 3.3V plane’s, and possesses the same RAM, Flash, Boot loader and MCU components as the original Teensy 4.1, but the 3.3V regulator was swapped for a NCP692 regulator providing essentially the same specs. 



The Following are notable features in the Boards design:

- 2x USB-C connections, one for serial programming and power, and the other a host port for communication with serial to other devices
- Expandable IC footprints for a combination of either 2x additional 16mb PSRAM or 1x 16mb PSRAM and 1x 64mb FLASH
- DP83825L Ethernet PHY IC for interfacing with the MCU and the RJ45 Ethernet connector attached to the board for 10/100mbps internet
- micro SD slot


After assembling the first prototype with the supplied stencil from JLCPCB and a hot plate, and resolving a short issue from a solder bridge, The bootloader flashed the blink script to the memory and the board was able to achieve it, however serial communication wouldn’t work and windows device manager gave a error code 43. After a week of researching and forum questioning, I was able to locate the root problem to the ESD protection Diodes on the USB-C that I had used were rated for USB 2.0 and not 3.0, which was ruining the serial communication between my PC and the board. After desoldering these the board managed to show up on my PC and was finally able to communicate with it, albeit without ESD protection which can be replaced with a more suitable diode.



The Designing and assembly of this board taught myself more trace design concepts such as:

- differential pairs and length matching design
- separation of analog and digital traces and components
- EMI ground shielding techniques
- positioning and selection of decoupling capacitors for electronic noise protection
- common via practices
- practice soldering SMD components with a hot plate and stencil effectively without overheating the temperature sensitive IC’s 
- more practical experience isolating faults in a circuit, such as isolating shorts, identifying faulty components
- examining signals with an oscilloscope to ensure Ethernet signal integrity.


all while managing to keep the design cost effective. This board is the most complex I have designed and successfully assembled to date and I am eager to take these skills learnt to the next level with the next project the future brings.
