---
Title: Component Selection
---


## **Introduction**

As defined by team 201, the purpose of this subsystem is to accurately and reliably manipulate a set of linear tracks in order to quickly and consistently sort colored spheres. It has been determined that this subsystem will thus focus on the implementation of an SPI-controlled stepper motor to manipulate the sorting mechanism. To satisfy these needs, both a *stepper motor* and a *stepper motor driver* have been benchmarked and researched (see Tables 1,2 below)

**The following document contains both *major component benchmarking* and *Microcontroller Selection*

## **Major Component Benchmarking**

Products in this category were selected based on usability and the perceivable ease which they will be integrated on a surface-mount PCB. The following devices were researched: **Stepper motors** and **Stepper motor drivers**.

### **Table 1: Stepper Motors**

| **Stepper Motor** | **Pros/Cons** |
|---|---|
| **Device 1**: MikroElektronika MIKROE-1530 5V tepper motor <br>![Image of IC](MIKROE-1530.png)<br>**Cost: $9.60/unit**<br>[DigiKey](https://www.digikey.com/en/products/detail/mikroelektronika/MIKROE-1530/5724295) - [*Datasheet*](https://download.mikroe.com/documents/datasheets/step-motor-5v-28byj48-datasheet.pdf) | **Pros:**<br> - Extremely common and well-documented by oustide sources <br> - Very fine resolution<br> **Cons:**<br> - Simplistic datasheet<br> - Wire come pre-connected to header (extra header or electric work needed to integrate).|
| **Device 2**: Pololu 1207 Bipolar stepper motor<br>![Image of IC](image.png)<br> **Cost: $19.40/unit** <br>[DigiKey](https://www.digikey.com/en/products/detail/pololu/1207/10449950) - [*Datasheet*](https://www.pololu.com/product-info-merged/1207) | **Pros:**<br> - Higher voltage motor <br> - Easy mounting profile <br> **Cons:**<br> - Datasheet does not contain safety information (absolute maximum ratings)<br> - Higher price point|
| **Device 3**: Pololu 1209<br>![Image of IC](image-1.png)<br>**Cost: $22.75/unit**<br>[DigiKey](https://www.digikey.com/en/products/detail/pololu/1209/10449952) - [*Datasheet*](https://www.pololu.com/product-info-merged/1209) | **Pros:**<br> - Higher running current takes advantage of barrel power supply (provides higher holding torque) <br> - Convenient mounting profile<br> **Cons:**<br> - Similar datasheet issues to the Pololu 1207 <br> - Lower rated voltage|

***Stepper motor decision:** Product #1: MikroElektronika MIKROE-1530 5V stepper motor*
This decision was made due to the reliability, low price point, and ubiquitous nature of this stepper motor.

### **Table 1: Stepper Motor Drivers**

| **Stepper Motor Driver** | **Pros/Cons** |
|---|---|
| **Device 1**: Onsemi NCV7708FDWR2G Double Hex Driver <br>![Image of IC](NCV7708FDWR2G.png)<br>**Cost: $5.83/unit**<br>[DigiKey](https://www.digikey.com/en/products/detail/onsemi/NCV7708FDWR2G/9829237) - [*Datasheet*](https://www.onsemi.com/pdf/datasheet/ncv7708f-d.pdf)   | **Pros:**<br> - Larger SOIC package size (easier assembly) <br> - Clear SPI datasheet<br> **Cons:**<br> - Large pin count (several unused pins)<br> - No express stepper motor drive functions (the device is not expressly designed for stepper motors).|
| **Device 2**: Analog Devices Inc./Maxim Integrated TMC249A-SA<br>![Image of IC](TMC249A-SA.png)<br>**Cost: $16.64/unit**<br>[DigiKey](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/TMC249A-SA/4399665) - [*Datasheet*](https://www.analog.com/media/en/technical-documentation/data-sheets/TMC249_datasheet_rev2.22.pdf) | **Pros:**<br> - Explicit and easy-to-read datasheet <br> - Serial control is a major design influence <br> **Cons:**<br> - High Unit Price (over 1/6 of budget)<br> - Large pin count (increases assembly time)|
| **Device 3**: Infineon BTM9011EPXUMA1<br>![Image of IC](BTM9011EPXUMA1.png)<br>**Cost: $1.95/unit**<br>[DigiKey](https://www.digikey.com/en/products/detail/infineon-technologies/BTM9011EPXUMA1/25702022) - [*Datasheet*](https://www.infineon.com/dgdl/Infineon-Infineon-BTM901xEP-DS-v01_00-EN-DataSheet-v01_00-EN.pdf?fileId=8ac78c8c90530b3a01912d365ee4326f) | **Pros:**<br> - Simple H-bridge layout <br> - Extremely cost effective <br> - Small pin count<br> **Cons:**<br> - Would require multiple units to drive a stepper motor <br> - Device not specifically designed for stepper motor control|

***Stepper motor driver decision:** Device 3: Infineon BTM9011EPXUMA1*
This device, though requiring multiple chips for full functionality, is more straightforward to implement. The low price point also allows the purchase of several extra units in case of design failure.

## **Microcontroller Selection**

Microcontrollers were researched based on given product requirements, such as a need for at least one SPI output and one UART RX/TX pair for communication with peripheral ICs and other controllers on the team daisy chain. See the table below for further details.

### **Table 3: PIC Info Table**

| **PIC Info** | **Answer** |
| --- | --- |
| Model | PIC18F27Q84 |
| Product Page URL | [Microchip](https://www.microchip.com/en-us/product/pic18f27q84) |
| Datasheet URL(s) | [Microchip](https://ww1.microchip.com/downloads/aemDocuments/documents/MCU08/ProductDocuments/DataSheets/PIC18F27-47-57Q84-Microcontroller-Data-Sheet-DS40002213.pdf) |
| Application Notes URL(s)| [Microchip](https://www.microchip.com/en-us/product/pic18f27q84#:~:text=Collapse-,Documentation,-Documents) |
| Vendor link | [DigiKey](https://www.digikey.com/en/products/detail/microchip-technology/PIC18F27Q84-I-SO/12807406) |
| Code Examples  | [Microchip](https://www.microchip.com/en-us/product/pic18f27q84#Design%20Resources:~:text=MPLAB%20Xpress%20IDE.-,Design%20Resources,-Code%20Examples) - [Github Collection](https://github.com/microchip-pic-avr-examples) - [CNC Example](https://github.com/microchip-pic-avr-examples/pic18f57q84-2-axis-cnc) |
| External Resources URL(s) | [YouTube.com](https://www.youtube.com/watch?v=8aYCZFFJLXI) - [Microchip (Example utilizes separate devBoard but appears useful)](https://www.microchip.com/en-us/about/media-center/videos/MfKy9SII6gM) |
| Unit cost | $2.10 |
| IC Absolute Maximum Current | **Vss Pin:** 350mA<br> **Vdd Pin:** 250mA<br> **I/O Pins:** 50mA |
| Supply Voltage Range | 1.8V <= *VDD* <= 5.5V |
| Maximum GPIO current | 50mA (See Above) |
| Supports External Interrupts | 3 Pins |
| Required Programming Info Hardware, Cost, URL| Device supports In-circuit Serial Programming (ICSP) with the use of 5 pins (ICSPCLK, ICSPDAT, MCLR/Vpp, Vdd, and Vss). An ICSP programmer such as the [MPLAB SNAP](https://www.microchip.com/en-us/development-tool/pg164100) would be necessary to use this function. (*Requires use of MPLAB X IDE*) |
| Works with MPLabX? | Yes, see [Microchip Site](https://www.microchip.com/en-us/product/pic18f27q84#Design%20Resources:~:text=T%C3%9CV%20S%C3%9CD%20certified-,MPLABX,-development%20tools%20are) |
| Works with Microchip Code Configurator? | Yes, see MPLAB X Screenshot![MPLAB X Screenshot](image-2.png) |

### **Table 4: PIC Peripherals Data**

| Module | # Available | Needed | Associated Pins (or * for any) |
| ---------- | ----------- | ------ | ------------------------------ |
| GPIO | 25 | 4+ | * |
| ADC | 24 | 0 | * |
| UART | 5 | 1 | *CTS/RX:* RA4-7, RB4-7, RC6-7, *DTR, RTS, TX:* *(any) |
| SPI | 2 | 1-2 (Indeterminate motor controller SPI configuration) | *SS, SCK, SDO:* *(any), *SDI,SCK:* RB2-3, RC3-4, *SS:* RA4-5 |
| I2C | 1 | 0 | *Logic:* RB1-2, *SCL,SDA:* RC3-4, *(Any) |
| PWM (Standalone) | 4 | 0 | *CCP:* RB*, *PWMERS, PWMIN, CCP:* RC*, *PWM1/2/3:* *(any)|
| ICSP | Yes (3 pins) | 3 | *MCLR:* RE3, *ICSPDAT:* RB7, *ICSPCLK:* RB6 |

###**Figure 1:** MPLAB X Screenshot featuring possible peripherals and pin layout

![MPLAB X Screenshot](image-2.png)

### *Microcontroller Rationale*

The Microchip PIC18F27Q84 comes from a line of tried and true microcontrollers used in a variety of application. Though marketed as "recommended for automotive applications", the device explicitly supports the perfect amount of functionality for the applications listed in the introduction to this page. The presence of an extra SPI module brings peace of mind in the event that it becomes difficult to control multiple motor drivers from the same SPI line. Additionally, the device currently boasts at least ten additional I/O pins that can be used to enable a variety of "bonus" functions, such as debugging LED indicators, extra motor drivers, or sphere-indexing servo motors. The low price point is another excellent feature of the PIC18F27Q84, lending itself well to a healthy, mistake-friendly development process.

-BP
