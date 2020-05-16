---
# required metadata

title: Network peripheral support overview
description: This topic provides an overview network peripherals supported in the store.
author: rubendel
manager: AnnBe
ms.date: 05/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-03-31
ms.dyn365.ops.version: AX 7.0.1

---

# Network peripheral support overview

[!include [banner](includes/banner.md)]

This topic describes network peripheral support within the store.

## Overview

The Modern POS application includes support for certain network peripheral devices within the store. This topic describes the setup for those devices.

## Key terms

| Term | Description |
|---|---|
| Register | The entity which is used to configure an instance of a point of sale register. |
| Device | Represents the physical instance of a point of sale register and the Modern POS application that is assigned to that register. |
| Dedicated hardware station | The hardware station business logic that is built into the Modern POS for Windows and Android applications. |
| d/k port | The d/k (drawer kick) port is a traditional method for connecting a cash drawer to a receipt printer. |
| Network peripherals | Built-in support for network enabled payment terminals, receipt printers, and cash drawers. |

## Supported POS clients and devices

This feature is supported with the **Modern POS for Windows** and **Modern POS for Android** point of sale clients. 

This feature supports network enabled payment terminals and receipt printers. Cash drawer support is provided by connecting the cash drawer via d/k port to the network enabled receipt printer.

Out of box, this feature is supported by the [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3), but other payment connectors may be supported via the SDK. Receipt printers supported by this feature include Star Micronics network enabled receipt printers. 

Out of box, network protocols for **Epson** and **Star Micronics** receipt printers are supported. Cash drawer connected to those printers via d/k port are supported via ESC/POS protocols.

## Set up

### Adyen payment terminal

For details related to Adyen payment terminal setup, visit the [payment terminal setup section](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3#pos-payment-terminal) on the Adyen connector page.

### Epson or Star Micronics receipt printer with cash drawer

#### Epson prerequisite

If your printer supports **Epson ePOS-Print**,  refer to the Epson's product manuals for directions on how to access **Epson Printers Configuration Website** and enable **ePOS-Print**. When **ePOS-Print** is configured, the printer will print a chit that shows its IP address after a power cycle. 

#### Star Micronics prerequisite 

Network enabled Star Micronics printers that support ethernet can be configured to use network protocols using the **Star Micronics Printer Utility**. Refer to documentation provided by Star Micronics for details around setting their devices up to support network printing. When the device is configured correctly, the IP address for the printer can be obtained through the UI for the printer utility. 
  
#### Hardware profile setup

1. In Dynamics 365 Commerce, search for **Hardware profiles**.
2. Click **New**
3. Assign a hardware profile number, then provide a description. 
4. In the device type fasttabs, set up the following:

| Device | Type | Device name | Additional details |
| --- | --- | --- | ---|
| Printer | Network | **Epson** or **Star** (This is case sensitive) | Assign a printing profile |
| Cash drawer | Network | **Epson** or **Star** (This is case sensitive)| **Use shared shift** = **Yes** if the cash drawer will be shared among different POS devices. |

5. Click **Save**
 
#### Modern POS for Windows or Android clients with built-in hardware station logic

1. In Dynamics 365 Commerce, search for **Registers**
2. Select a register by clicking the register number and click **Edit**
3. Assign the previously created hardware profile to the register that will be using a dedicated payment terminal. The device mapped to this register must be use either the Modern POS for Windows or Android applications.
4. Click **Save**.
5. In the ribbon, click **Registers** > **Configure IP addresses**.
6. Select the printer fasttab and enter the IP address for the printer. Leave the port number blank.
7. Select the cash drawer fasttab and enter the IP address for the printer. Leave the port number blank.
8. Click **Save**.
9. Search for **All stores**.
2. Select a store by clicking on its **Retail Channel Id**.
3. Click **Edit**.
4. Scroll down to the **Hardware stations** fasttab and click to expand.
5. Click **Add**.
2. Set **Hardware station type** to **Dedicated**.
3. Provide a description. 
4. Do not specify a hardware profile or any other properties. 
5. Click **Save**.
9. Search for **Distribution schedules**.
10. Select distribution schedule **1090** and click **Run now**.
11. Select distribution schedule **1070** and click **Run now**.

 
If using a Modern POS for iOS or Cloud, which do not have built-in hardware station logic, do the following:

1. Search for **All stores**.
2. Select a store by clicking on its **Retail Channel Id**.
3. Click **Edit**.
4. Scroll down to the **Hardware stations** fasttab and click to expand.
5. Click **Add**.
6. Set **Hardware station type** to **Shared**.
7. Provide a description. This hardware station may be shared among POS clients including those with built-in hardware station logic. 
8. Assign the hardware profile for network peripherals to this hardware station using the dropdown.
9. Click **Save**.
9. With the hardware station for receipt printer and cash drawer selected, click **Configure IP addresses**.
10. Select the printer fasttab and enter the IP address for the printer. Leave the port number blank.
11. Select the cash drawer fasttab and enter the IP address for the printer. Leave the port number blank.

> [!NOTE]
> For full instructions related to setting up shared hardware stations, visit the topic [Configure and install Retail hardware station] (https://docs.microsoft.com/en-us/dynamics365/commerce/retail-hardware-station-configuration-installation).

12. Click **Save**
13. Search for **Distribution schedules**.
14. Select distribution schedule **1090** and click **Run now**.
15. Select distribution schedule **1070** and click **Run now**.


### Sharing peripherals network peripherals

Network receipt printers and cash drawers may be shared among POS devices. This sharing can be accomplished by using a shared hardware station to broker the connection to the devices. Devices may also be shared by configuring the same devices directly on the register properties when MPOS for Windows or Android are used. 

Payment terminals may only be shared when a shared hardware station is deployed to broker the connection to the payment terminal. Setting the same payment terminal IP address directly at the register level in order to share the payment terminal is not supported and will cause issues when individual POS clients attempt to lock and claim the device. 


## Related articles

[Set up POS hybrid app on Android and iOS](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/hybridApp)
[Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
[Dedicated payment terminal with prompt for printer and cash drawer](https://go.microsoft.com/fwlink/?linkid=2129966)
