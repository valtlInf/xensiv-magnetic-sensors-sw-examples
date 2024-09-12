# MOTIX: TLE5012B Angle Sensor interfacing with TLE9879 Motix Controller and using angle sensor for steering angle measurement

This code example demonstrates how to interface [TLE5012B](https://www.infineon.com/cms/en/product/sensor/magnetic-sensors/magnetic-position-sensors/angle-sensors/tle5012b-e1000/) angle sensor with [TLE9879](https://www.infineon.com/cms/en/product/sensor/magnetic-sensors/magnetic-position-sensors/angle-sensors/tle5012b-e1000/) Motix Controller and also use the sensor for steering angle position measurement. The sensor is interfaced with the controller via SSC (3-wire SPI) interface. The controller is the master which initiates the communication using sending command to retrieve angle information. The sensor which the slave, upon receiving the appropriate command from the master sends the angle information on the data lines.

This setup is implemented using the Keil IDE and Tera Term for UART communication, providing real-time angle monitoring and accurate angle value being displayed on the terminal.

[View this README on GitHub.](replace_code_example_github_readme_url)


## Requirements

- Keil uVision5 IDE
- Programming language: C
- [TLE5012B](https://www.infineon.com/cms/en/product/sensor/magnetic-sensors/magnetic-position-sensors/angle-sensors/tle5012b-e1000/)
- [TLE9879](https://www.infineon.com/cms/en/product/sensor/magnetic-sensors/magnetic-position-sensors/angle-sensors/tle5012b-e1000/)

## Supported toolchains (make variable 'TOOLCHAIN')

- GNU Arm&reg; Embedded Compiler v11.3.1 (`GCC_ARM`) – Default value of `TOOLCHAIN`
- Arm&reg; Compiler v6.16 (`ARM`)
- IAR C/C++ Compiler v9.40.2 (`IAR`)


## Supported kits (make variable 'TARGET')

- [MOTORCONTROLKIT_12V](https://www.infineon.com/cms/en/product/evaluation-boards/motorcontrolkit_12v/)


## Hardware setup

This example uses the board's default configuration. See the kit user guide to ensure that the board is configured correctly.

Use jumper wires to establish a connection between TLE5012B Angle sensor and the MOTORCONTROL_12V kit as mentioned below.

1. Connect **VCC** of the sensor to the **3.3V** supply on the MOTORCONTROLKIT_12V kit.
2. Connect the **GND** pin of the sensor to the **GND** of the MOTORCONTROLKIT_12V kit.
3. Connect the Clock pin (SCK) **Pin 7** of the sensor to  **P0.3** of the MOTORCONTROLKIT_12V kit.
4. Connect the Chip select (CSQ) **Pin 5** of the sensor to  **P1.1**
5. Connect the SPI DATA pin (DATA) **Pin 3** of the sensor to 

Refer to the connection diagram below.

   **Figure 2. Connection Pin out of between MOTORCONTROLKIT_12V**
   ![alt text](image-1.png)

  

## Software setup

Install Keil uVision5 IDE.

Install a terminal emulator if you don't have one. Instructions in this document use [Tera Term](https://teratermproject.github.io/index-en.html).

This example requires no additional software or tools.

## Operation

1. Connect the board to your PC using the provided USB cable through the KitProg3 USB connector.

2. Supply 12 V to the MOTORCONTROLKIT board.

      ![alt text](image-2.png)

3. Using Config Wizard for Motix MCU configure the SSC and GPIO peripherals.

4. Configuring SSC:

   a) Select **SSC** 1 block.
  
   b) Select mode of SSC to **Master Mode**.

   c) Select Data Width as **16 bits**.

   d) Select  Transmission with **MSB First**.

   e) CLock Phase: **Shift data on the leading clock edge, latch on trailing edge**.

   f) Clock Polarity: **Idle clock line is low, leading clock edfe is low to high transmission** 

   g) Pins: Clock = **P0.3**, MOSI = **P0.2**, MISO = **P0.4**


5) Configuring GPIO for Chip Select.

   a) Configure PORT 1 Pin4 as output. This pins will be used as slave select.

6) Open the terminal and select baud rate to 115200.

7) Flash the code into the controller and the real time angle value will be visible on the terminal.

   
   ![alt text](<Screenshot 2024-09-12 190541.png>)




## Related resources

Resources  | Links
-----------|----------------------------------
Device documentation | [TLE5012B Datasheet](https://www.infineon.com/dgdl/Infineon-TLE5012B_Exxxx-DataSheet-v02_01-EN.pdf?fileId=db3a304334fac4c601350f31c43c433f) <br> [TLE5012B UserManual](https://www.infineon.com/dgdl/Infineon-Angle_Sensor_TLE5012B-UM-v01_02-en-UserManual-v01_02-EN.pdf?fileId=5546d46146d18cb40146ec2eeae4633b&da=t)<br> [TLE5012B Product Page](https://www.infineon.com/cms/en/product/sensor/magnetic-sensors/magnetic-position-sensors/angle-sensors/tle5012b-e1000/) <br>[TLE9879 datasheet](https://www.infineon.com/dgdl/Infineon-TLE9879QXA40-DataSheet-v02_11-EN.pdf?fileId=8ac78c8c81ae03fc0181d840096a3c2f)
Development kits | Select your kits from the [Evaluation board finder](https://www.infineon.com/cms/en/design-support/finder-selection-tools/product-finder/evaluation-board).
Tools  | Keil uVision5

<br>



## Other resources

Infineon provides a wealth of data at [www.infineon.com](https://www.infineon.com) to help you select the right device, and quickly and effectively integrate it into your design.



## Document history

Document title: *PSoC6: Tooth Wheel Speed Measurement*

 Version | Description of change
 ------- | ---------------------
 1.0.0   | New community code example


All referenced product or service names and trademarks are the property of their respective owners.

The Bluetooth&reg; word mark and logos are registered trademarks owned by Bluetooth SIG, Inc., and any use of such marks by Infineon is under license.


---------------------------------------------------------

© Cypress Semiconductor Corporation, 2024. This document is the property of Cypress Semiconductor Corporation, an Infineon Technologies company, and its affiliates ("Cypress").  This document, including any software or firmware included or referenced in this document ("Software"), is owned by Cypress under the intellectual property laws and treaties of the United States and other countries worldwide.  Cypress reserves all rights under such laws and treaties and does not, except as specifically stated in this paragraph, grant any license under its patents, copyrights, trademarks, or other intellectual property rights.  If the Software is not accompanied by a license agreement and you do not otherwise have a written agreement with Cypress governing the use of the Software, then Cypress hereby grants you a personal, non-exclusive, nontransferable license (without the right to sublicense) (1) under its copyright rights in the Software (a) for Software provided in source code form, to modify and reproduce the Software solely for use with Cypress hardware products, only internally within your organization, and (b) to distribute the Software in binary code form externally to end users (either directly or indirectly through resellers and distributors), solely for use on Cypress hardware product units, and (2) under those claims of Cypress's patents that are infringed by the Software (as provided by Cypress, unmodified) to make, use, distribute, and import the Software solely for use with Cypress hardware products.  Any other use, reproduction, modification, translation, or compilation of the Software is prohibited.
<br>
TO THE EXTENT PERMITTED BY APPLICABLE LAW, CYPRESS MAKES NO WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, WITH REGARD TO THIS DOCUMENT OR ANY SOFTWARE OR ACCOMPANYING HARDWARE, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE.  No computing device can be absolutely secure.  Therefore, despite security measures implemented in Cypress hardware or software products, Cypress shall have no liability arising out of any security breach, such as unauthorized access to or use of a Cypress product. CYPRESS DOES NOT REPRESENT, WARRANT, OR GUARANTEE THAT CYPRESS PRODUCTS, OR SYSTEMS CREATED USING CYPRESS PRODUCTS, WILL BE FREE FROM CORRUPTION, ATTACK, VIRUSES, INTERFERENCE, HACKING, DATA LOSS OR THEFT, OR OTHER SECURITY INTRUSION (collectively, "Security Breach").  Cypress disclaims any liability relating to any Security Breach, and you shall and hereby do release Cypress from any claim, damage, or other liability arising from any Security Breach.  In addition, the products described in these materials may contain design defects or errors known as errata which may cause the product to deviate from published specifications. To the extent permitted by applicable law, Cypress reserves the right to make changes to this document without further notice. Cypress does not assume any liability arising out of the application or use of any product or circuit described in this document. Any information provided in this document, including any sample design information or programming code, is provided only for reference purposes.  It is the responsibility of the user of this document to properly design, program, and test the functionality and safety of any application made of this information and any resulting product.  "High-Risk Device" means any device or system whose failure could cause personal injury, death, or property damage.  Examples of High-Risk Devices are weapons, nuclear installations, surgical implants, and other medical devices.  "Critical Component" means any component of a High-Risk Device whose failure to perform can be reasonably expected to cause, directly or indirectly, the failure of the High-Risk Device, or to affect its safety or effectiveness.  Cypress is not liable, in whole or in part, and you shall and hereby do release Cypress from any claim, damage, or other liability arising from any use of a Cypress product as a Critical Component in a High-Risk Device. You shall indemnify and hold Cypress, including its affiliates, and its directors, officers, employees, agents, distributors, and assigns harmless from and against all claims, costs, damages, and expenses, arising out of any claim, including claims for product liability, personal injury or death, or property damage arising from any use of a Cypress product as a Critical Component in a High-Risk Device. Cypress products are not intended or authorized for use as a Critical Component in any High-Risk Device except to the limited extent that (i) Cypress's published data sheet for the product explicitly states Cypress has qualified the product for use in a specific High-Risk Device, or (ii) Cypress has given you advance written authorization to use the product as a Critical Component in the specific High-Risk Device and you have signed a separate indemnification agreement.
<br>
Cypress, the Cypress logo, and combinations thereof, ModusToolbox, PSoC, CAPSENSE, EZ-USB, F-RAM, and TRAVEO are trademarks or registered trademarks of Cypress or a subsidiary of Cypress in the United States or in other countries. For a more complete list of Cypress trademarks, visit www.infineon.com. Other names and brands may be claimed as property of their respective owners.
