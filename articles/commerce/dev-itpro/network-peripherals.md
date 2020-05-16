---
# required metadata

title: Network peripheral support overview
description: This topic provides an overview network peripherals supported in the store.
author: rubendel
manager: AnnBe
ms.date: 05/15/2020
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

This feature is supported with the Modern POS for Windows and Modern POS for Android point of sale clients. 

This feature supports network enabled payment terminals and receipt printers. Cash drawer support is provided by connecting the cash drawer via d/k port to the network enabled receipt printer.

Out of box, this feature is supported by the [Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3), but other payment connectors may be supported via the SDK. Receipt printers supported by this feature include Star Micronics network enabled receipt printers. 

To set up Star receipt printers, use the Star Micronics Printer Utility to configure the device for use over the network. This utility will also provide the IP address of the device. 

To set up Epson receipt printers, use the Epson e-POS Print utility to set up the device to use network protocols. 

For more information on setting up network peripherals, visit the [Network peripherals setup topic](https://go.microsoft.com/fwlink/?linkid=2129965).

## Set up

### Hardware profiles

This feature requires two types of hardware profiles. The first is assigned to the register and the second is assigned to a hardware station at the store level and used to logically group network receipt printers and cash drawers. 

#### Register hardware profile

The hardware profile assigned to the register should be set up as follows:

1. In Dynamics 365 Commerce, search for **Hardware profile**
2. Click **New**
3. Assign a hardware profile number, then provide a description. This is the hardware profile that will be assigned to the register itself, so a description such as "Dedicated with fallback" would suffice.
4. In the device type fasttabs, set up the following:

| Device | Type | Device name | Additional details |
| --- | --- | --- | ---|
| Printer | Fallback | **Epson** or **Star** | Print profile should be the same as the print profile mapped to the network printer set up in the hardware profile assigned to the hardware station at the channel level. |
| Cash drawer | Fallback | **Epson** or **Star** | **Use shared shift** = **Yes** |
| EFT service | Adyen | N/A | To set up the out of box Adyen connector, visit [this article](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3). Other payment connectors can be supported through the [payments SDK](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/end-to-end-payment-extension). 
| PIN pad | Network | **MicrosoftAdyenDeviceV001** | |

5. In Dynamics 365 Commerce, search for **Registers**
6. Select a register by clicking the register number and click **Edit**
7. Assign the previously created hardware profile to the register that will be using a dedicated payment terminal. The device mapped to this register must be use either the Modern POS for Windows or Android applications.
8. Click **Save**.
9. In the ribbon, click **Registers**>** Configure IP addresses.
10. In the **PIN pad** fasttab, provide the IP address for the payment terminal. Visit [this article](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3) for information on obtaining the payment terminal IP address using the Adyen connector. 
11. Click 'Save'.

#### Receipt printer and cash drawer hardware profile

The hardware profile used to group network receipt printer and cash drawer should be set up as follows:

1. In Dynamics 365 Commerce, search for **Hardware profile**
2. Click **New**
3. Assign a hardware profile number, then provide a description. This is the hardware profile that will be used to group receipt printers and cash drawers, so a description such as "Network printer and cash drawer" would suffice.
4. In the device type fasttabs, set up the following:

| Device | Type | Description | Additional details |
| --- | --- | --- | ---|
| Printer | Network | **Epson** or **Star** | Print profile should be the same as the one mapped to the printer set up in the hardware profile assigned to the register. |
| Cash drawer | Fallback | **Epson** or **Star** | **Use shared shift** = **Yes** |

5. Click **Save**.

### Hardware stations

This feature requires two of hardware stations. One that is mapped to the register and one that is selected ad hoc when the need to print a receipt or open a cash drawer arises.

#### Register hardware station

1. Search for **All stores**.
2. Select a store by clicking on its **Retail Channel Id**.
3. Click **Edit**.
4. Scroll down to the **Hardware stations** fasttab and click to expand.
5. Click **Add**.
6. Set **Hardware station type** to **Dedicated**.
7. Provide a description. This is the hardware station that will be used for the register at all times. 
8. Set no other values for this hardware station. 

#### Hardware station for receipt printer and cash drawer

1. Click **Add**.
2. Set **Hardware station type** to **Dedicated**.
3. Provide a description. This is the hardware station that will be used for the receipt printer and cash drawer.
4. In the **Hardware profile** column, use the drop down to select the hardware profile previously created for the  receipt printer and cash drawer. 
5. Click **Save**.
6. With the hardware station for receipt printer and cash drawer selected, click **Configure IP addresses**.
7. Obtain the IP address for the printer and use that for the IP adresses for the receipt printer and cash drawer. 
8. Click **Save**
9. Search for **Distribution schedules**.
10. Select distribution schedule **1090** and click **Run now**.
11. Select distribution schedule **1070** and click **Run now**.

### Using ad hoc receipt printer and cash drawer selection

1. Using a supported POS client, close the current shift, if one is open. 
2. Log in and select **Non-drawer drawer operations**.
3. Use the **Manage hardware stations** operation to turn on the hardware station.
4. Select the hardware station created for register to make it active.
5. Log out of the point of sale, then log back in and open a shift.
6. The payment terminal assigned to the hardware profile will now always be active and the user will be prompted if a receipt printer or cash drawer are required. 

Many merchants who requested this feature are interested in reducing waste by providing email receipts and to encourage electronic payments. Depending on how the POS is configured, store associates will only be prompted to select a receipt printer or cash drawer when the customer wants a physical receipt or to pay with cash. 

The store associate will only be prompted to select a hardware station once per transaction, unless a scenario arises where a receipt needs to be printed and cash is used for payment, but the originally selected hardware profile does not include both devices. In that case, the store associate will be prompted again to select a hardware station that can be used to complete the transaction. 

## Related articles

[Set up POS hybrid app on Android and iOS](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/hybridApp)
[Dynamics 365 Payment Connector for Adyen](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3)
[Configuring network peripherals](https://go.microsoft.com/fwlink/?linkid=2129965)


Out of the box, the Android app communicates with network-enabled Epson printers that support Epson's ePOS-Print protocol. To enable this interface, connect the Epson printer to the network. ePOS-Print is enabled through a web interface that allows users to access Epson network-enabled printers through a browser. This web interface is typically reached by opening a web browser and typing http://<printer IP address>. The IP address for the printer can be obtained by connecting it to the network, then turning it off and on. After the network IP address is obtained, a receipt that displays the printer's IP address will print. For more information about configuring ePOS-Print, refer to the documentation provided by Epson. 
      
After the Epson printer has ePOS-Print enabled, turn the printer off and turn it back on. When the device comes back online, a receipt should print to indicate the device's IP address. Note the device's IP address and navigate to the POS register form in Dynamics 365. Select the register being set up and open for editing. On the **Register** tab in the ribbon area, note the subheading labeled **Hardware** with an available action called **Configure IP addresses**. Use this action to specify the IP address for the printer that is being used by this specific register. If the **IP address** field is not available for the printer, check the hardware profile assigned to the register to ensure that the printer type is set to **Network**. A port is not required for the out-of-the-box support for Epson printers.

**New for 10.0.8** - Cash drawers connected to Epson network printers via drawer kick (dk) port are now supported. To use a cash drawer connected to a network-enabled Epson printer, configure the printer according to the directions above. Set the cash drawer to type 'Network' in the hardware profile. Navigate to the register or hardware station the hardware profile is assigned to and use the **Configure IP addresses** function to set the IP address for the cash drawer, which is the same as the address configured for the printer.


### Sharing peripherals using built-in peripheral support

Payment terminals and receipt printers can be shared among Android POS clients and other MPOS devices. While peripherals can still be shared through an IIS hardware station; the addition of built-in peripheral support for Android POS enables sharing of these devices without deploying the hardware station as a web service.

To share devices among Android POS clients, instead of assigning the IP and hardware profile to the register, the hardware profile should be set on the dedicated hardware station itself. To do this, go to **Retail and Commerce > Channels > Stores > All stores**. Select the store and open for editing. Next, scroll down to the list of hardware stations for the store and assign the hardware profile with network payment terminal, EFT settings, and network printer directly to the hardware station itself. For this scenario, the EFT terminal ID will also need to be assigned to the hardware station at the store level.
