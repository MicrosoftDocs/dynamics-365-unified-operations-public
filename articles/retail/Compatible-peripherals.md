---
# required metadata

title: Peripheral compatibility for Retail  
description: This topic describes the process of listing peripheral devices as 'compatible' with Microsoft Dynamics 365 for Retail. Whether a device has been previously tested for compatibility or not, devices should always be tested with the customer's specific environment to ensure compatibility. 
author: rubencdelgado
manager: AnnBe
ms.date: 10/08/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata
# ms.search.form:  RetailHardwareProfile
audience: IT Pro
# ms.devlang: 
# ms.reviewer: sericks
ms.search.scope: 

# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: [Global for most topics. Set Country/Region name for localizations]
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: [author's Microsoft alias]
ms.search.validFrom: [month/year of release that feature was introduced in, in format yyyy-mm-dd]
ms.dyn365.ops.version: 

---

# Peripheral compatibility for Retail

[!include[banner](../includes/banner.md)]

Devices listed on this page have been tested for compatiblity with Microsoft Dynamics for Retail using the [Peripheral simulator for Retail](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-peripheral-simulator). For each device, the party who performed the test and submitted successful results to Microsoft is listed in the 'Tested by' column. For devices listed as tested by 'Microsoft Corp.', support requests should be directed to Microsoft. Issues with devices tested by a party other than Microsoft should be first reported to the testing party. 

## Compatible devices by type

### Line display
| Date tested  | Tested by  | Manufacturer  | Mfg website  | Support email  | Support telephone  | Driver version | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP  | HP  | http://www.hp.com  |   support@hp.com  | 1-713-200-8378  | HPTD620Display  | HPTD620Display  | 6.6.5.6  | 1.02.11  | OPOS  | USB  | http://www.hp.com  |

### MSR
| Date tested  | Tested by  | Manufacturer  | Mfg website  | Support email  | Support telephone  |  Driver version | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP  | HP  | http://www.hp.com  |   support@hp.com  | 1-713-200-8378  | HPSinglenoSRDMSR  | HPSinglenoSRDMSR  | 3.29  | 5.37  | OPOS  | USB  | http://www.hp.com  |

### Printer
| Date tested  | Tested by  | Manufacturer  | Mfg website  | Support email  | Support telephone  | Driver version | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP  | HP  | http://www.hp.com  |   support@hp.com  | 1-713-200-8378  | H300  | H300  | 1.14.1.19  | 1.61B  | OPOS  | USB  | http://www.hp.com  |


### Bar code scanner
| Date tested  | Tested by  | Manufacturer  | Mfg website  | Support email  | Support telephone  | Driver version | Driver name | Driver version | Firmware version | Driver type | Connection | Driver download link |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 10/17/2017 | HP  | HP  | http://www.hp.com  |   support@hp.com  | 1-713-200-8378  | N3680-HP  | N3680-HP  | 1.14.0.5  | DX000010BAA  | OPOS  | USB  | http://www.hp.com  |


Note: This compatiblity list is new as February 2017. The list will grow over time as devices are tested successfully and results are submitted to Microsoft. 

## Device compatiblity testing

Devices can be tested for compatibility using the Peripheral simulator for Retail. Details around device testing and how to produce test logs for submission to Microsoft can be found here: (https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-peripheral-simulator)

Once a device has been successfully tested, in order for compatiblity to be acknowledged, the test results must be submitted to drpc@microsoft.com. This simulator is can be obtained via a download link on the hardware profile within Dynamics 365. Device manufacuturers likely do not have access to Dynamics 365. To obtaining a copy of the Peripheral simulator for Retail, contact drpc@microsoft.com. 

Testing must be performed for every retail peripheral setup that goes into production. If the compatiblity list indicates that the exact same device/POS setup has been tested in the past, testing should still be done as part of UAT testing. In those cases, test results do not need to be submitted to Microsoft. For all other successful test results, it is encouraged to submit results to drpc@microsoft.com to help build the list of compatible devices. 

## Supported devices

Only devices that have been previously tested for compatibility, with results submitted to Microsoft, will be supported for new implementations. This is necessary to ensure new implementations have been adequately tested and to help build a library of previously tested devices. Previously, Microsoft has performed internal testing on devices and the results have been listed in places such as on the [Retail peripherals overview](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/retail-peripherals-overview). Due to the sheer variance in devices in the market, that process is not does not scale. So, moving forward, the majority of testing must be done by partners, customers and -most importatly- device manufacturers. Ideally, devices will be tested proactively by manufacturers to ensure that partners and customers can make peripheral selections based on the list of compatible devices. 

## Disclaimer


