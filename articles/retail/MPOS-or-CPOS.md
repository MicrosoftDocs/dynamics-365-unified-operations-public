---
# required metadata

title: Choosing between Moderns POS and Cloud POS
description: This document explains the key differences between Retail Modern POS and Cloud POS and provides considerations to help retailers implementing Dynamics 365 for Retail to make the best choice for their needs.
author: Jeff Blucher 
manager: AnnBe
ms.date: 10/12/2017
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
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: 
ms.search.validFrom: 2017-10-12
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Choosing between Modern POS and Cloud POS

[!include[banner](includes/banner.md)]

## Purpose of this document:
This document has been prepared as an added supplement to the standard user documentation.  The Insights and Implementation Consideration document is intended to provide an implementer with additional background, tips, and guidance for things to consider when deploying a Dynamics 365 feature.   Implementation resources should review and follow guidance in these documents as part of their deployment process, with the goal of utilizing this information to assist them in avoiding unnecessary issues that could impact user satisfaction or performance.

## Insights:
Microsoft Dynamics 365 for Retail provides a wide variety of deployment and topology options which allows retailers to choose the components and configuration that best meets their business and technology needs.  One of the most important implementation aspects that requires careful consideration is choosing most appropriate platform and formfactor for the point of sale (POS) component.

### POS platform and formfactor considerations
The following POS options are supported in Dynamics 365 for Retail:
* Retail Modern POS (MPOS) for Windows
* Retail Modern POS (MPOS) for Windows Phone
* Retail Modern POS (MPOS) for iPad or Android tablet
* Cloud POS (CPOS) with Edge, IE, and Chrome support

In all cases the POS (MPOS and CPOS) share the same core application code.  This is important because:
*	The user interface is consistent regardless of platform or formfactor
*	Most of the functional capabilities are identical regardless of platform or formfactor. There are some key differences however and these are called out below.
*	These variations of the POS can be mixed and coincide within a given store.  A retailer could utilize MPOS on a Windows PC for their main registers, but easily supplement them with browser based terminals or mobile devices.
*	Customizations and extensions can be easily leveraged across platforms and formfactors.  Since the core application code is shared, most customizations can be implemented once rather than individually

### Retail Modern POS applications vs Cloud POS
As much as MPOS and CPOS are the same, there are some key differences that must be understood.

**Retail Modern POS:**  MPOS whether on a Windows, iOS, or Android device is an application that is packaged and installed and serviced on that device.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Windows:** The application MPOS for Windows contains all the application code and the embedded CRT.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**iOS/Android:**  The application on these platforms acts as a host for the Cloud POS application code.  This means that the application code itself comes from the Cloud POS server on Azure or the Retail Store Scale Unit (RSSU). 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Learn more about **Retail Store Scale Unit** [here.](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/dev-itpro/retail-store-system-begin)

**Cloud POS:** Since Cloud POS runs in a browser the application is not installed on the device.  The browser accesses the application code from the Cloud POS server .  Due to this fact, Cloud POS cannot directly access POS hardware or work in an offline state.

### Store deployment considerations
In addition to the choice of platform and formfactor, the retailer also needs to choose from multiple deployment choices at the store.  The table below specifies the available configurations for each POS options.

|POS application         |Retail server        |Offline available|
|:------------------------|:---------------------|:-----------------|
|MPOS for Windows        |Cloud or RSSU        |Yes              |
|MPOS for iOS or Android |Cloud or RSSU        |No               |
|Cloud POS               |Cloud or RSSU        |No               |

**Retail server:** The Retail server is a component that hosts the Commerce Runtime (CRT) which contains all the business logic utilized by POS and provides access to the channel database.  While online, all POS clients in the store utilize the Retail server.  The Retail server can be deployed in the Dynamics cloud or deployed in the store (RSSU).  

**Offline mode:**  MPOS for Windows supports offline mode, which allows the POS to continue to process sales even if it has been disconnected from its Retail server and then sync with the channel database when connectivity is restored.  MPOS utilizes its own embedded instance of the CRT and temporarily utilizes its own local data source (offline SQL database). 

Learn more about offline functionality available at POS [here.](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/pos-offline-functionality)

###POS peripheral/hardware considerations
Another area to consider is how the POS will access devices and peripherals such as printers, cash drawers, and payment terminals.  Only MPOS for Windows supports direct communication to these devices.  MPOS for Windows Phone, iOS or Android, and Cloud POS require a hardware station to access the devices.  Hardware stations can be dedicated to a POS register or shared among the registers within the store.

Learn more about hardware station [here.](https://docs.microsoft.com/en-us/dynamics365/unified-operations/retail/retail-hardware-station-configuration-installation)

## Implementation Considerations
Below are some things to consider as you plan your POS implementation at your retail stores.

1. **Functional requirements** – The core business processes and capabilities are the same regardless of platform, formfactor, or deployment topology.  This means that for the most part retailers do not need to include this in their considerations when planning their implementation.  

2.	**Connectivity** - Network availability (WAN and LAN) is a major factor that needs careful considerations.  The cost and simplicity benefits of a zero footprint, cloud hosted solution, are completely lost if system is not available for business-critical processes. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Unless the connectivity for a given device is extremely dependable and resilient, or the retail can accept a certain amount of down time, it is recommended to either:

* Utilize Retail Modern POS on Windows with offline enabled
* Deploy a Retail Store Scale Unit on premises 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;It should also be noted that these options are not mutually exclusive.  For the most reliable topology, retailers can deploy a local RSSU reducing the dependency on internet connectivity or Azure availability and offline enabled POS registers should there be an issue with the local server or network.

3.	**Hardware devices/peripherals** – A key aspect of a Retail POS system is its ability to utilize POS peripherals such as printers, cash drawers, and payment terminals.  While any of the POS options available can utilize peripheral devices, only Retail Modern POS for Windows can support them directly.  For all other applications one or more Hardware stations are required.  This adds additional flexibility, but also additional components to be deployed, configured, and serviced.

4.	**System requirements** – Each POS application has varying system requirements.  Be sure to check the latest information before making your selection.  Running Cloud POS in a browser for example provides a wider selection of supported operation systems. Learn more about system requirements [here.](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/system-requirements)
 
5.	**Deployment and servicing** – Depending on the application and deployment choices, the complexity of the deployment and servicing requirements can vary.  For example, with a cloud hosted Cloud POS deployment there is no need to install and update on each device, which greatly reduces complexity and cost.  Deploying MPOS with offline on each register, along with shared hardware stations will vastly increase the number of end points to be managed.







