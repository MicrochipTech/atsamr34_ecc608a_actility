# ATSAMR34_ECC608A_ACTILITY
<img src="Doc/IoT-Made-Easy-Logo.png" width=100>

> “Wireless Made Easy!" - Develop with the SAM R34 LoRa SiP and WLR089U0 Module with Microchip LoRaWAN stack on Actility join server

<p>
<a href="https://www.microchip.com/design-centers/security-ics/trust-platform/trust-go/trust-go-lora-secure-authentication-with-join-servers" target="_blank">
<img border="0" alt="Microchip_logo" src="Doc/Microchip_logo.png" width="150">

<a href="https://www.actility.com" target="_blank">
<img border="0" alt="Actility_logo" src="Doc/Actility_logo.png" width="200">
</p>
</a>

## ⚠ Disclaimer

<p><span style="color:red"><b>
THE SOFTWARE ARE PROVIDED "AS IS" AND GIVE A PATH FOR SELF-SUPPORT AND SELF-MAINTENANCE.</br></br>
This repository contains unsupported example code intended to help accelerate client product development. It is not validated for production nor audited for security best-practices.</br></br>
Note that while this repository is unsupported, Microchip welcome community contributions, and all pull-requests will be considered for inclusion into the repository.
</span></p></b>

> Interact with peers in the community at [LoRa Forum](https://www.microchip.com/forums/f512.aspx).

## Abstract

**This guide will direct you through the process of getting started with developing a Secure LoRa End Device product using Microchip Technology's Pre-provisioned ATECC608 secure element along with Actility Join server.**

## Sample Applications

[Clone/Download](https://docs.github.com/en/free-pro-team@latest/github/creating-cloning-and-archiving-repositories/cloning-a-repository) the current repo to get the software.

## A la carte

1. [Material required](#step1)
2. [Software](#step2)
3. [Hardware setup](#step3)
4. [Sample Application Code](#step4)
5. [Actility ThingPark Activation](#step5)
6. [Running the demo](#step6)

## Material required <a name="step1"></a>

Purchase samples of the <a href="https://www.microchipdirect.com/product/search/all/ATECC08A-TNGACT" target="_blank">ATECC608A-TNGACT</a>
secure element 
and the <a href="https://www.microchipdirect.com/product/search/all/AT88CKSCKTUDFN-XPRO" target="_blank">CryptoAuthentication UDFN Socket Kit</a>
</br>
![](Doc/CryptoAuthenticationUDFN.png)
</br>

Purchase the <a href="https://www.microchip.com/Developmenttools/ProductDetails/DM320111" target="_blank">SAM R34 Xplained Pro Evaluation Kit</a>
</br>
![](Doc/ATSAMR34Xpro.png)
</br>

Purchase the <a href="https://www.microchip.com/DevelopmentTools/ProductDetails/PartNO/EV23M25A" target="_blank">WLR089U0 Xplained Pro Evaluation Kit</a>
</br>
![](Doc/WLR089U0Xpro.png)
</br>

Purchase a LoRa(r) Gateway from <a href="https://market.thingpark.com/gateways.html?ship_to=all" target="_blank">ThingPark Market</a>
</br>
![](Doc/Gateways_ThingPark_Market.png)
</br>


## Software <a name="step2"></a>

- Download and install [Microchip Studio 7.0 IDE](https://www.microchip.com/mplab/microchip-studio).
- Open Microchip Studio 7.0 IDE.
- From **Tools - > Extensions and updates**, install Advanced Software Framework (ASFv3) v3.49.0 release or upper release.
- Restart Microchip Studio
- Download and install a serial terminal program like Tera Term. </br>
https://osdn.net/projects/ttssh2/releases/

## Hardware setup <a name="step3"></a>

Configure the DIP switch of the CryptoAuthenticationUDFN Socket kit for I2C communication with the host microcontroller.
</br>
**1, 3 and 6 must be placed to ON position**
</br>
![](Doc/DIP_Switch.png)
</br>

Open the socket board
</br>
![](Doc/OpenSocketBoard.png)
</br>

Make sure the ATECC608A device is ready to be inserted in the right direction.
Make sure the pin 1 of the component (represented by a point) is located at the bottom left.
</br>
![](Doc/SecureElement.png)
</br>

Place the Secure Element in the UDFN socket
</br>
![](Doc/SecureElementPlacement.png)
</br>

Make sure the Secure Element is properly seated and the pin 1 is located at the bottom left.
</br>
![](Doc/SecureElementPlaced.png)
</br>
Close the clam shell lid.
</br>

Attach the CryptoAuthenticationUDFN Socket kit to the SAM R34 Xplained Pro board on the **EXT3 header.** (same setup is valid for WLR089U0 Xplained Pro as well)
</br>
Plug the antenna.
Attach a USB cable to SAM R34 Xplained Pro board's EDBG micro-B port on the right.</br>
The USB ports powers the board and enables the user to communicate with the kits.
</br>
![](Doc/FullSetup.png)

>  Same setup is valid for WLR089U0 Xplained Pro as well

- Wait for USB driver installation and COM ports mounting. </br>
- Launch Tera Term program and configure the serial ports mounted with: **115200 bps, 8/N/1**

## Sample Application Code <a name="step4"></a>

Open the "APPS_ENDDEVICE_DEMO" project with Microchip Studio 7 IDE</br>
From the top menu, go to Project -> APPS_ENDDEVICE_DEMO Properties</br>
From Tool settings, select your board as EDBG debugger with SWD interface
</br>
![](Doc/EDBG.png)
</br>
Build and download the project by clicking the empty green "Run without debugging" triangle
</br>
![](Doc/AtmelStudio.png)
</br>
Open the Tera Term UART console previously configured at 115200 bps, 8-data bits/No parity/1-stop bit
</br>
Press the "Reset" button on the SAM R34 Xplained Pro board to see output printed to the console
</br>
Observe the following identifiers coming from the ATECC608A Secure Element
</br>
![](Doc/UART_Console1.png)
</br>


In order to pre-commission a device using ATECC608A secure element in ThingPark Activation, the following idenfiers are required:

- DevEUI: LoRaWAN device 64-bit unique identifier assigned by the Device manufacturer (or using Secure Element default value)
- JoinEUI: LoRaWAN JS 64-bit unique identifier of the Join Server on which AppKey of the device is stored
- TKM Info: ATECC608A secure element identifier allowing ThingPark Activation to retrieve secure element AppKey


## Actility ThingPark Activation <a name="step5"></a>

Activating the device within Actility ThingPark is the next step.</br>

Go here: <a href="https://github.com/actility/Microchip-Getting-Started" target="_blank">https://github.com/actility/Microchip-Getting-Started</a>


This guide will direct you through the process of getting started with developing a secure LoRa end device product using Microchip Technology's Pre-provisioned ATECC608A secure element along with ThingPark Activation service from Actility.


## Running the demo <a name="step6"></a>

Go back to the Tera Term UART console
</br>
![](Doc/UART_Console2.png)
</br>
Press "1" to start the Demo Application
</br>
Select the band where your device is operating
</br>
![](Doc/UART_Console3.png)
</br>
Then, the end device application transmits a Join Request message. If a Join Accept message was received and validated, the SAM R34 Xplained Pro board will be joined to the Join Server.
</br>
![](Doc/UART_Console4.png)
</br>
Press "2" to send a packet consisting of a temperature sensor reading
</br>
![](Doc/UART_Console5.png)
</br>
Connect to ThingPark Wireless Logger to monitor the activity of your device
</br>
![](Doc/WirelessLogger.png)
</br>
