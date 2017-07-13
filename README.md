# DL533N Tamashell testing scripts

Example script for basic testing of DL533N D-Logic NFC reader based on NXP's PN533 chip. Provides example of usage GPIO pins to control LEDs and buzzer specific to this device.

## Getting Started

Download and install libnfc https://github.com/nfc-tools/libnfc following instructions.
Should be used with libNFC "pn53x-tamashell" executable. 

### Prerequisites

LibNFC https://github.com/nfc-tools/libnfc and DL533N NFC reader. Visit https://www.d-logic.net/nfc-rfid-reader-sdk/ for more information. 
Obtain technical documentation for PN533 chip from NXP's website to get better knowledge of register manipulation.

### Installing

No installation needed. After successfully installed libnfc run "pn53x-tamashell" with
'''
./pn53x-tamashell testGPIO_dl533_short
'''
where "testGPIO_dl533_short" is the script's filename.

## Running the test script

Script is commented so you can interactively follow what happens.
After each performed step, script is paused for 500 msec. 

Script will do the following steps:
1.	issue GET_FIRMWARE command
2.	Get status registers P3CFGA P3CFGB of GPIO pin P3
3.	Write Register of P3 to zero
4.	Get status registers P7CFGA P7CFGB of GPIO pin P7
5.	Write Register of P3 to zero
6.	Get status register 6106 which is needed to obtain control of P34 GPIO
7.	Turn on Green LED by issuing WriteRegister P7 with value 0x01
8.	Turn off Green LED by issuing WriteRegister P7 with value 0x00
9.	Turn on Red LED by issuing WriteRegister P3 with value 0x20 - bit 5 GPIO P35 up
10.	Turn off Green LED by issuing WriteRegister P3 with value 0x00 - bit 5 GPIO P35 down
11.	Play sound on Buzzer by issuing WriteRegister P3 with value 0x10 - bit 4 GPIO P34 up
12.	Turn off sound on Buzzer by issuing WriteRegister P3 with value 0x00 - bit 4 GPIO P34 up
13.	Turn on both LEDs and play sound
14.	Change the state of GPIO pins from QUASI BI-DIRECTIONAL (default) to PUSH PULL OUTPUT 
15.	Reset registers to default values.

## License

This project is licensed under the ..... License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Purpose of this demo script is to provide additional info about usage of hardware specific features like user controllable LEDs and buzzer.
* It is specific to mentioned hardware ONLY and some other hardware might have different approach, please bear in mind that.  


