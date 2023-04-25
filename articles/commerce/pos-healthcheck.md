---
# required metadata

title: Health check for POS peripherals and services
description: This article provides an overview of the health check operation in the point of sale (POS).
author: BrianShook
ms.date: 03/06/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 141393
ms.assetid: e23e944c-15de-459d-bcc5-ea03615ebf4c
ms.search.region: Global
ms.search.industry: Retail
ms.author: brshoo
ms.search.validFrom: 2019-03-31
ms.dyn365.ops.version: AX 7.0.1

---

# Health check for POS peripherals and services

[!include [banner](includes/banner.md)]

This article describes the health check operation in the point of sale (POS).

## Overview

Retail stores can be complex environments where many applications and devices are used. As operations grow, it can become difficult to ensure that operations always run smoothly, because of dependencies on, for example, peripherals that can break or accidentally become unplugged over the course of a day. Troubleshooting for issues that are related to devices and services can be costly for larger merchants and equally frustrating for smaller operations.

Microsoft Dynamics 365 Commerce includes a health check operation that can help prevent some of this cost and frustration. This operation provides a method for testing devices directly from the POS outside of normal operations, and two tests for network-related issues. Therefore, it can help retailers detect issues before they occur.

## Key terms

| Term | Description |
|---|---|
| Peripheral | Any device that the POS application uses to facilitate transactions and other operations in the store. Examples include cash drawers, bar code scanners, and payment terminals. |
| Service | In this article, a service is an ancillary application that the POS application depends on to perform transactions and daily operations. Examples include apps that help with tax or shipping calculations. |

## Health check operation

The health check operation is operation 717 on the **POS Operations** page in Commerce Headquarters. It can be used while the POS is in non-drawer mode. However, a hardware station must be active.

Health check can be accessed by point of sale users in two ways:

1. The **Health check** button on the Settings page.
2. By adding a tile to a button grid that is part of your screen layout and associating the health check operation to that tile. 

### Peripheral health checks

By default, the health check tests only devices that are configured in the hardware profile for the hardware station that is currently active for a register. If a register uses multiple hardware stations over the course of a day, to do health checks for all of them, it must connect to one hardware station at a time. There is no store-level health check. However, it's possible that this type of check can be done through Commerce Server extensibility.

#### Out-of-box health checks

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

#### Using peripheral health checks in the point of sale

When the health check operation is initiated in the POS, a pane on the right lists the configured devices and shows the status of each device. To do a health check for a single device, select the device, and then select **Test selected**. To do a health check for all devices, select **Test all**. The **Test all** function tests all the devices, one at a time, and updates the status of each device in the **Status** column.

The **Last check** column shows when the health check was last done for each device.

If the health check for a device passes (that is, if no errors are encountered), the device's status will be **OK**. If the health check fails, the status will indicate that there was an error. In this case, the pane on the right provides details that are related to the error, or it instructs the user to contact the system admin.

Some devices, such as the OPOS keylock, don't have out-of-box health check tests. If a health check test isn't detected for any device that is used, the status will be **Not supported**.

### Network health checks

Two network health checks are always included in the health check list regardless of the peripherals configured for this terminal, the Retail server connectivity test and the Network latency test. They can be selected and run individually or together. 

Out-of-box health checks

| Name                       | Details                                                      |
| -------------------------- | ------------------------------------------------------------ |
| Retail server connectivity | The Retail server connectivity health check verifies that the terminal can communicate with Retail Server and the channel database, and verifies that real-time service calls can be made to Dynamics Headquarters. |
| Network latency            | The Network latency health check tests the network latency between the terminal and Retail server. The test returns the average latency for 10 calls to Retail server of a 5 second period. |

#### Network latency health check

The results of the latency health check are categorized as follows:

| Latency range       | Meaning                                                      |
| ------------------- | ------------------------------------------------------------ |
| 0-50ms.             | **Good** - your network latency is low and not likely to be source of any performance related issues. |
| 50-100ms.           | **Acceptable** - your network latency is in an acceptable range, but may be degrading performance for network-intensive operations such as offline sync. |
| greater than 100ms. | **Poor** - Your network latency is likely degrading your point of sale operations. Latency in the 100-150ms. range may not cause noticable performance degradation for common operations, but latency above 150ms, most operations will become slower.  <br /><br />To further diagnose network latency, run an internet speed test on this register to test the internet. If the latency on the internet speed test is high, please inform your system administrator that you are experiencing high latency with your internet connection. |

### Extending health checks

The out-of-box health check tests are configured to provide some user-friendly messages for typical errors. However, not all scenarios are covered. Through extensibility, merchants can map user-friendly messages to errors that might be specific to their environment.

Custom health checks can also be created to test devices that aren't supported out of the box, or to test any services that the POS depends on.

## Related articles

[Modern POS (MPOS) triggers and printing](dev-itpro/pos-trigger-printing.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]