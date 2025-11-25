# FLASHING-OF-LEDS-WITH-LPC-1768

# AIM: 
   To interface and toggle the led with ARM LPC 1768 microprocessor           
           
# COMPONENTS REQUIRED:
##  HARDWARE:
ARM LPC1768
LED
## SOFTWARE:
KEIL MICRO VISION 4.0 IDE

# PROCEDURE:


⮚	Open the Keil software and select the New uvision project from Project Menu as shown below.
⮚	Browse to your project folder and provide the project name and click on save.
⮚	Once the project is saved a new pop up “Select Device for Target” opens, Select the controller (NXP: LPC1768) from NXP (founded by philips) and click on OK.
⮚	Select the controller (NXP: LPC1768) and click on OK.
⮚	As LPC1768 needs the startup code, click on Yes option to include the LPC17xx Startup file.
⮚	Create a new file by file → new to write the program.
⮚	Type the code.
⮚	After typing the code save the file as main.c eg. (abc.c).
⮚	Right click target and Add the suitable files to source group1 and header for the project.
⮚	Add the main.c along with system_LPC17xx.c.
⮚	Build the project and fix the compiler errors/warnings if any.
⮚	Code is compiled with no errors. The .bin file is still not generated.
⮚	Right Click on Target Options to select the option for generating .bin file.
⮚	Set IROM1 start address as 0x2000. Bootloader will be stored from 0x0000- 0x2000 so application should start from 0x2000
⮚	Write	the	command	to	generate	the .bin file	from
.axf file
Command: fromelf --bin projectname.axf --output filename.bin
⮚	in c/c++ → include paths → desktop (00-libfiles).
⮚	.Bin file is generated after a rebuild.
⮚	Check the project folder for the generated .Bin file.

# ADD FILES:
Target1:
Source group1:
Startuplpc17xx.s, main.c (t), delay.c (t), systemlpc17xx.c (t), gpio.c (t)
Header:
Delay.h, stdutils.h, gpioi.h

# PIN DIAGRAM :
 <img width="897" height="587" alt="506455659-d42a4929-5250-48c4-b229-8b2c2923eb80" src="https://github.com/user-attachments/assets/bc3d9453-14da-42e9-98c2-6a7c7f375058" />


# CIRCUIT DIAGRAM:
 <img width="866" height="500" alt="506455776-07c659eb-737a-48c5-8f43-50d38170a5fe" src="https://github.com/user-attachments/assets/96e462be-2843-45fd-accc-a28532915baf" />

 
# PROGRAM:
```
#include <lpc17xx.h>
#include "delay.h"       //User defined library which contains the delay routines
#include "gpio.h"

#define LED P1_29        // Led is connected to P1.29

/* start the main program */
int main()
{
    SystemInit();                          //Clock and PLL configuration
    GPIO_PinFunction(LED,PINSEL_FUNC_0);   // Configure Pin for Gpio
    GPIO_PinDirection(LED,OUTPUT);         // Configure the pin as OUTPUT
    GPIO_PinWrite(LED,LOW);

    while(1)
    {
        /* Turn On all the leds and wait for 100ms */
        GPIO_PinWrite(LED,HIGH);           // Make all the Port pin as high
        DELAY_ms(100);

        GPIO_PinWrite(LED,LOW);            // Make all the Port pin as low
        DELAY_ms(100);
    }
}

 ```
# Output:

![506458700-9251f758-d853-4a50-85bd-1a57c5db6421](https://github.com/user-attachments/assets/a7e1a1a5-96c0-4aac-94f3-ef75a97667d1)
RESULT:
Thus, a LED is interfaced and toggled with ARM LPC1768 Microprocessor.

