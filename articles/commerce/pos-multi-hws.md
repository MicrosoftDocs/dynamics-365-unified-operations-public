---
# required metadata

title: Dedicated payment terminal with prompt for printer and cash drawer
description: This topic provides an overview of the capability to have a dedicated payment terminal while prompting the user to select a cash drawer and receipt printer.
author: rubendel
manager: AnnBe
ms.date: 05/16/2020
ms.topic: article
ms.prod: tonyafehr
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
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

# Dedicated payment terminal with prompt for printer and cash drawer

[!include [banner](includes/banner.md)]

This topic provides an overview of the capability to have a dedicated payment terminal while prompting the user to select a cash drawer and receipt printer.

## Overview

Modern retailers are always searching for ways to streamline the in-store chekout experience. In addition to making the purchasing experience friction-free, recent trends toward paperless checkout with electronic payments are lessening the need to have a full compliment of peripheral devices available for every store associate. 

This feature supports these trends in retail by enabling a scenario where the point of sale device can have a full-time payment terminal assigned to it without its own receipt printer or cash drawer. When the associate needs to print a receipt or take a cash payment, they are prompted to select a hardware station where those devices are configured.

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

| Device | Type | Description | Additional details |
| --- | --- | --- | ---|
| Printer | Fallback | *Any* | Print profile should be the same as the print profile mapped to the network printer set up in the hardware profile assigned to the hardware station at the channel level. |
| Cash drawer | Fallback | *Any* | **Use shared shift** = **Yes** |
| EFT service | Adyen | N/A | To set up the out of box Adyen connector, visit [this article](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3). Other payment connectors can be supported through the [payments SDK](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/end-to-end-payment-extension). 
| PIN pad | Network | **MicrosoftAdyenDeviceV001** | |

5. In Dynamics 365 Commerce, search for **Registers**
6. Select a register by clicking the register number and click **Edit**
7. Assign the previously created hardware profile to the register that will be using a dedicated payment terminal. The device mapped to this register must be use either the Modern POS for Windows or Android applications.
8. Click **Save**.
9. In the ribbon, click **Registers**>** Configure IP addresses.
10. In the **PIN pad** fasttab, provide the IP address for the payment terminal. Visit [this article](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3) for information on obtaining the payment terminal IP address using the Adyen connector. 
11. Click 'Save'.

### Hardware profiles

This feature requires two types of hardware profiles. The first is assigned to the register and the second is assigned to a hardware station at the store level and used to logically group network receipt printers and cash drawers. 

#### Receipt printer and cash drawer hardware profile

The hardware profile used to group network receipt printer and cash drawer should be set up as follows:

1. In Dynamics 365 Commerce, search for **Hardware profile**
2. Click **New**
3. Assign a hardware profile number, then provide a description. This is the hardware profile that will be used to group receipt printers and cash drawers, so a description such as "Network printer and cash drawer" would suffice.
4. In the device type fasttabs, set up the following:

| Device | Type | Description | Additional details |
| --- | --- | --- | ---|
| Printer | Network | *Any* | Print profile should be the same as the one mapped to the printer set up in the hardware profile assigned to the register. |
| Cash drawer | Fallback | *Any* | **Use shared shift** = **Yes** |

5. In Dynamics 365 Commerce, search for **Registers**
6. Select a register by clicking the register number and click **Edit**
7. Assign the previously created hardware profile to the register that will be using a dedicated payment terminal. The device mapped to this register must be use either the Modern POS for Windows or Android applications.
8. Click **Save**.
9. In the ribbon, click **Registers**>** Configure IP addresses.
10. In the **PIN pad** fasttab, provide the IP address for the payment terminal. Visit [this article](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/adyen-connector?tabs=8-1-3) for information on obtaining the payment terminal IP address using the Adyen connector. 
11. Click 'Save'.

### Out-of-box health checks

| Type | Connection | Details |
|---|---|---|
| Printer | OPOS | This check tests basic object linking and embedding for POS (OPOS) functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> |
| Line display | OPOS | This check tests basic OPOS functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> |
| Dual display | Windows | This check ensures that the operating system detects a second Windows display. | 
| MSR | OPOS | This check tests basic OPOS functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> |
| Drawer | OPOS | This check tests basic OPOS functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> | 
| Scanner | OPOS | This check tests basic OPOS functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> | 
| Scale | OPOS | This check tests basic OPOS functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> |
| PIN pad | OPOS | This check tests basic OPOS functions. Here are some examples:<ul><li>Open: **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True**</li><li>Close: **DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**</li></ul> |
| Payment terminal | Payments SDK | This check tests basic payment terminal functions provided by the Payments SDK. <ul><li>Lock</li><li>BeginTransaction</li><li>EndTransaction</li><li>ReleaseDevice</li><li>Close</li></ul> |

### Using the health check operation in the POS

When the health check operation is initiated in the POS, a pane on the right lists the configured devices and shows the status of each device. To do a health check for a single device, select the device, and then select **Test selected**. To do a health check for all devices, select **Test all**. The **Test all** function tests all the devices, one at a time, and updates the status of each device in the **Status** column.

The **Last check** column shows when the health check was last done for each device.

If the health check for a device passes (that is, if no errors are encountered), the device's status will be **OK**. If the health check fails, the status will indicate that there was an error. In this case, the pane on the right provides details that are related to the error, or it instructs the user to contact the system admin.

Some devices, such as the OPOS keylock, don't have out-of-box health check tests. If a health check test isn't detected for any device that is used, the status will be **Not supported**.

### Extending health checks

The out-of-box health check tests are configured to provide some user-friendly messages for typical errors. However, not all scenarios are covered. Through extensibility, merchants can map user-friendly messages to errors that might be specific to their environment.

Custom health checks can also be created to test devices that aren't supported out of the box, or to test any services that the POS depends on.

## Related articles

[Modern POS (MPOS) and Cloud POS trigger extensibility](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/modern-pos-trigger-extensibility)
