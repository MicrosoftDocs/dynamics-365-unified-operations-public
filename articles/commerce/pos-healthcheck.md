---
# required metadata

title: Health check for POS peripherals and services
description: This topic provides an overview of the health check operation in the point of sale (POS).
author: rubendel
manager: AnnBe
ms.date: 03/04/2020
ms.topic: article
ms.prod: 
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

# Health check for POS peripherals and services


[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes health check operation in the point of sale (POS).

## Overview

Retail stores can be complex environments with many applications and devices in use. As operations grow, it can become difficult to ensure that operations are always running smoothly because of dependencies on things like peripherals that can break or accidentally become unplugged over the course of the day. Troubleshooting issues related to devices and services can be costly for larger merchants and equally frustrating for smaller operations. 

Dynamics 365 Commerce versions 10.0.10 and higher include an operation that can alleviate some of this pain by providing a method to check devices from the POS outside of normal operations. This health check operation can help retailers detect problems before they occur. 

## Key terms

| Term | Description |
|---|---|
| Peripheral | Any device that the POS application uses to facilitate transactions and other operations within the store. Examples include cash drawers, bar code scanners, and payment terminals. |
| Service | In this topic, a service is an ancillary application that the POS application depends on to perform transactions and daily operations. Examples include apps that aid in tax or shipping calculations. |

## Health check operation

The health check is operation ID 717 on the **POS Operations** page in Commerce Headquarters (HQ). It can be used while the POS is in non-drawer mode, but a hardware station must be active. By default, the health check will only check devices that are configured in the hardware profile for the hardware station active at the time for a register. If a register uses multiple hardware stations over the course of a day, the register will need to connect to them one at a time to perform health checks for those hardware stations. There is  no store-level health check, but this type of check could potentially be done through retail server extensibility. 

### Out-of-box health checks

| Type | Connection | Details | 
|---|---|---|
| Printer | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close** |
| Line display | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close** |
| Dual display | Windows | Check to ensure a second Windows display is detected by the operating system. | 
| MSR | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close** |
| Drawer | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close** | 
| Scanner | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close** | 
| Scale | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**  |
| PIN pad | OPOS | Tests basic OPOS functions including: <br> **Open:** <br> **Open** &gt; **ClaimDevice** &gt; **DeviceEnabled=True** <br><br> **Close:**<br>**DeviceEnabled=False** &gt; **ReleaseDevice** &gt; **Close**  |
| Payment terminal | Payments SDK | **Lock** <br> **BeginTransaction** <br> **EndTransaction** <br> **ReleaseDevice** <br> **Close** |

### Use health check in POS

When the health check operation is invoked in the POS, the configured devices will be listed in a pane on the right side showing device status. To perform a health check on a single device, select the device and then click **Test selected**. To perform a health check for all devices, click **Test all**. The **Test all** function will check all devices one by one and update the status in the **Status** column. The **Last check** column indicates when the health check was last executed for each device. 

If the health check does not encounter an error, the device's status will be "Ok". If a health check fails, the status will indicate that there was a failure. The pane on the right side will provide details related to the error or instruct the user to contact their system administrator. 

Some devices, such as the OPOS keylock, do not have health checks out-of-box. If one of those devices is in use, but a health check test is not detected, the status will read "Not supported". 

### Extending health check

The out-of-box health check tests are configured to provide some user-friendly messages for common errors, but not all scenarios are covered. Through extensibility, merchants can map user-friendly messages to errors that may be specific to their environment. 

Custom health checks can also be created to check devices not supported out-of-box or services upon which the POS may depend. 

## Related articles

- [Modern POS (MPOS) and Cloud POS trigger extensibility](https://docs.microsoft.com/dynamics365/commerce/dev-itpro/modern-pos-trigger-extensibility)




