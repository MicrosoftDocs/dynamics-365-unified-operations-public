---
# required metadata

title: Health check for point of sale peripherals and services
description: This topic provides an overview of the health check operation in the point of sale..
author: rubendel
manager: AnnBe
ms.date: 05/09/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: rubendel
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.1

---

# Health check for point of sale peripherals and services


[!include [banner](../includes/banner.md)]

This topic describes the new health check operation in the point of sale.

## Overview

Retail stores can be complex environments with many applications and devices in use. As operations grow, it can become difficult to ensure that operations are always running smoothly due to dependencies on things like peripherals that can break or accidentally become unplugged over the course of the day. Troubleshooting issues related to devices and services can become very costly for larger merchants and equally frustrating for smaller operations. 

For 10.0.10, a new operation is being introduced which can alleviate some of this pain by providing a method to check these devices from the point of sale, outside of normal operations. This new health check operationswill help retailers detect problems before they occur with a customer standing in line. 

## Key terms

| Term | Description |
|---|---|
| Peripherals | Any device that the point of sale application uses to facilitate transactions and other operations within the store. Examples include cash drawers, bar code scanners, and payment terminals. |
| Services | For the purpose of this document, services describe ancillary applications that the point of sale application depends on to perform transactions and daily operations. Examples include services that aid in tax or shipping calculations. |

## Health check operation

The health check is operation ID 717 in the **POS Operations** back office form. It can be used while the POS is in non-drawer mode, but a hardware station must be active. By defualt, the health check will only check devices that are configured in the hardware profile for the hardware station which is active at the time for a register. If a register uses multiple hardware stations over the course of a day, to perform health checks for those hardware stations, it will need to connect to them one at a time. There is currently no store-level health check which can be performed, but this could potentially be done through retail server extensiblity. 

### Out of box health checks

| Type | Connection | Details | 
|---|---|---|
| Printer | OPOS | Tests basic OPOS functions including **Open** &gt; **Claim** &gt; **Release** &gt; **Close** |
| Printer | Windows driver | Basic Windows printer health check functions such as those described [here](https://gallery.technet.microsoft.com/scriptcenter/Printer-Health-Check-Up-29da22b2). |
| Printer | Device |  |
| Line display | OPOS | Tests basic OPOS functions including **Open** &gt; **Claim** &gt; **Release** &gt; **Close** |
| Dual display | Windows | Check to ensure a second Windows display is detected by the operating system. | 
| MSR | OPOS | Tests basic OPOS functions including **Open** &gt; **Claim** &gt; **Release** &gt; **Close** |
| Drawer | OPOS | Checks drawer open/closed status | 
| Scale | OPOS | Tests basic OPOS functions including **Open** &gt; **Claim** &gt; **Release** &gt; **Close** |
| EFT service | Adyen | If the out of box Adyen payment connector is configured, checks the device connection and network connection. |

### Using health check in POS

When the health check operation is invoked in the POS, the configured devices will be listed with a pane on the right hand side showing device status. To perform a health check on a single device, select the device and then click **Test selected**. To perform a health check for all devices, click **Test all**. The **Test all** function will check all devices one by one and update the status in the **STATUS** column. The **LAST CHECK** column indicates when the health check was last executed for the each device. 

If the health check does not encounter an error, the device's status will be **OK**. If a health check fails, the status will indicate that there was a failure. The pane on the right hand side will provide details related to the error or instruct the user to contact their system administrator. 

Some devices, such as the OPOS keylock, do not have healtch checks out of box. If one of those devices is in use, but a health check test is not detected, the status will read **Not supported**. 

### Extending health check

The out of box health check tests have been configured to provide some user friendly messages for common errors, but not all scenarios are covered. Through extensibility, merchants can map user friendly messages to errors that may be specific to their environment. 

Custom health checks can also be created to check devices not supported out of box or services upon which the point of sale may depend. 

## Related articles

- [Modern POS(MPOS) and Cloud POS Trigger Extensibility](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/modern-pos-trigger-extensibility)
- (



