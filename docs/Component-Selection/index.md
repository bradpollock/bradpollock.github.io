---
Title: Component Selection
---

## Selection Process

Products were selected based on usability and the perceivable ease which they will be integrated on a surface-mount PCB.

The following devices were researched: **Stepper motors** and **Stepper motor drivers**.

## Stepper Motors

| **Stepper Motor** | **Pros/Cons** |
|---|---|
| **Device 1**: MikroElektronika MIKROE-1530 5V tepper motor <br>![Image of IC](MIKROE-1530.png)<br>[DigiKey](https://www.digikey.com/en/products/detail/mikroelektronika/MIKROE-1530/5724295) [*Datasheet*](https://download.mikroe.com/documents/datasheets/step-motor-5v-28byj48-datasheet.pdf) **Cost: $9.60/unit**  | **Pros:**<br> - Extremely common and well-documented by oustide sources <br> - Very fine resolution<br> **Cons:**<br> - Simplistic datasheet<br> - Wire come pre-connected to header (extra header or electric work needed to integrate).|
| **Device 2**: Pololu 1207 Bipolar stepper motor<br>![Image of IC](image.png)<br>[DigiKey](https://www.digikey.com/en/products/detail/pololu/1207/10449950) [*Datasheet*](https://www.pololu.com/product-info-merged/1207) **Cost: $19.40/unit**   | **Pros:**<br> - Higher voltage motor <br> - Easy mounting profile <br> **Cons:**<br> - Datasheet does not contain safety information (absolute maximum ratings)<br> - Higher price point|
| **Device 3**: Pololu 1209<br>![Image of IC](image-1.png)<br>[DigiKey](https://www.digikey.com/en/products/detail/pololu/1209/10449952) [*Datasheet*](https://www.pololu.com/product-info-merged/1209) **Cost: $22.75/unit**   | **Pros:**<br> - Higher running current takes advantage of barrel power supply (provides higher holding torque) <br> - Convenient mounting profile<br> **Cons:**<br> - Similar datasheet issues to the Pololu 1207 <br> - Lower rated voltage|

### Decision: Product #1: MikroElektronika MIKROE-1530 5V tepper motor
This decision was made due to the reliability, low price point, and ubiquitous nature of this stepper motor.

## Stepper Motor Drivers

| **Stepper Motor Driver** | **Pros/Cons** |
|---|---|
| **Device 1**: Onsemi NCV7708FDWR2G Double Hex Driver <br>![Image of IC](NCV7708FDWR2G.png)<br>[DigiKey](https://www.digikey.com/en/products/detail/onsemi/NCV7708FDWR2G/9829237) [*Datasheet*](https://www.onsemi.com/pdf/datasheet/ncv7708f-d.pdf) **Cost: $5.83/unit**  | **Pros:**<br> - Larger SOIC package size (easier assembly) <br> - Clear SPI datasheet<br> **Cons:**<br> - Large pin count (several unused pins)<br> - No express stepper motor drive functions (the device is not expressly designed for stepper motors).|
| **Device 2**: Analog Devices Inc./Maxim Integrated TMC249A-SA<br>![Image of IC](TMC249A-SA.png)<br>[DigiKey](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/TMC249A-SA/4399665) [*Datasheet*](https://www.analog.com/media/en/technical-documentation/data-sheets/TMC249_datasheet_rev2.22.pdf) **Cost: $16.64/unit**   | **Pros:**<br> - Explicit and easy-to-read datasheet <br> - Serial control is a major design influence <br> **Cons:**<br> - High Unit Price (over 1/6 of budget)<br> - Large pin count (difficult to solder)|
| **Device 3**: Infineon BTM9011EPXUMA1<br>![Image of IC](BTM9011EPXUMA1.png)<br>[DigiKey](https://www.digikey.com/en/products/detail/infineon-technologies/BTM9011EPXUMA1/25702022) [*Datasheet*](https://www.infineon.com/dgdl/Infineon-Infineon-BTM901xEP-DS-v01_00-EN-DataSheet-v01_00-EN.pdf?fileId=8ac78c8c90530b3a01912d365ee4326f) **Cost: $1.95/unit**   | **Pros:**<br> - Simple H-bridge layout <br> - Extremely cost effective <br> - Small pin count<br> **Cons:**<br> - Would require multiple units to drive a stepper motor <br> - Large pin count (difficult to solder)|

### Decision: Device 3: Infineon BTM9011EPXUMA1
This device, though requiring multiple chips for full functionality, is more straightforward to implement. The low price point also allows the purchase of several extra units in case of design failure.