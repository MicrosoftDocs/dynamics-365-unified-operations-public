---
# required metadata

title: Peripheral compatibility for Commerce 
description: This topic lists peripheral devices that have been tested for compatibility with Dynamics 365 Commerce.
author: BrianShook
ms.date: 11/30/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata
# ms.search.form:  RetailHardwareProfile
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: brshoo
ms.search.validFrom: 2017-10-08
ms.dyn365.ops.version: 

---

# Peripheral compatibility for Commerce

[!include [banner](../includes/banner.md)]

Devices listed on this page have been tested for compatibility with Dynamics 365 Commerce using the [Peripheral simulator for Commerce](dev-itpro/retail-peripheral-simulator.md). For each device, the party who performed the test and submitted successful results to Microsoft is listed in the 'Tested by' column. For devices listed as tested by 'Microsoft Corp.', support requests should be directed to Microsoft. Issues with devices tested by a party other than Microsoft should be first reported to the testing party.

## Compatible devices by type

### Line display

| Date tested | Tested by | Manufacturer | Manufacturer website | Support email | Support telephone | Model name | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP | HP | https://www.hp.com | support@hp.com | | HPTD620Display | HPTD620Display | 6.6.5.6 | 1.02.11 | OPOS | USB | https://www.hp.com |

### MSR

| Date tested | Tested by | Manufacturer | Manufacturer website | Support email | Support telephone | Model name | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP | HP | https://www.hp.com | support@hp.com | | HPSinglenoSRDMSR | HPSinglenoSRDMSR | 3.29 | 5.37 | OPOS | USB | https://www.hp.com |

### Printer

| Date tested | Tested by | Manufacturer | Manufacturer website | Support email | Support telephone | Model name | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP | HP | https://www.hp.com | support@hp.com | | H300 | H300 | 1.14.1.19 | 1.61B | OPOS | USB | https://www.hp.com |

### Bar code scanner

| Date tested | Tested by | Manufacturer | Manufacturer website | Support email | Support telephone | Model name | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP | HP | https://www.hp.com | support@hp.com | | N3680-HP | N3680-HP | 1.14.0.5 | DX000010BAA | OPOS | USB | https://www.hp.com |

> [!NOTE]
> This compatibility list is new as September 2018. The list will grow over time as devices are tested successfully and results are submitted to Microsoft.

## Device compatibility testing

Devices can be tested for compatibility using the peripheral simulator. For information on obtaining the peripheral simulator, conducting device testing, and producing test logs for submission to Microsoft, see [Peripheral simulator for Commerce](dev-itpro/retail-peripheral-simulator.md). Testing must be performed for every peripheral setup that goes into production. If the compatibility list indicates that the exact same device/POS setup has been tested in the past, testing should still be done as part of user acceptance testing (UAT).

## Supported devices

Only devices that have been previously tested for compatibility, with results submitted to Microsoft, will be supported for new implementations. This is necessary to ensure new implementations have been adequately tested and to help build a library of previously tested devices. Previously, Microsoft has performed internal testing on devices and the results have been listed in places such as on the [Peripherals](retail-peripherals-overview.md). Due to the sheer variance in devices in the market, that process is not does not scale. So, moving forward, the majority of testing must be done by partners, customers and – most importantly – device manufacturers. Ideally, devices will be tested proactively by manufacturers to ensure that partners and customers can make peripheral selections based on the list of compatible devices.

## Disclaimer

©2018 Microsoft Corporation. All rights reserved

This document is for informational purposes only. Results are based on testing specific devices and configurations in a controlled lab environment in which the specified Microsoft Dynamics software was used. Any difference in system hardware, software design or configuration, customizations, or transaction mix may affect actual performance or results.

MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS SUMMARY. This document is provided "as-is." Information and views expressed in this document, including URL and other Internet Web site references, may change without notice. You bear the risk of using it. This document does not provide you with any legal rights to any intellectual property in any Microsoft product. You may copy and use this document for your internal, reference purposes.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
