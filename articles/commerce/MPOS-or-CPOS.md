---
# required metadata

title: Choose between Modern POS (MPOS) and Cloud POS
description: This topic explains the key differences between Modern POS and Cloud POS. It also describes various factors that retailers implementing Dynamics 365 Commerce should consider to help them make the best choice for their requirements.
author:  jblucher 
manager: AnnBe
ms.date: 10/13/2017
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
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2017-10-12
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
---

# Choose between Modern POS (MPOS) and Cloud POS

[!include [banner](includes/banner.md)]

This topic gives implementers additional background, tips, and guidance for factors that they should consider when they deploy Dynamics 365 Commerce. By reviewing and following this guidance as part of the deployment process, implementers can avoid issues that might affect user satisfaction or performance.

## Insights

Commerce provides a wide range of deployment and topology options. Therefore, retailers can choose the components and configuration that best meet their business and technology requirements. One aspect of implementation that requires careful consideration is the choice of a platform and form factor for the point of sale (POS) component.

### POS platform and form factor considerations

Commerce supports the following POS options:

- Modern POS (MPOS) for Microsoft Windows
- MPOS for Microsoft Windows Phone
- MPOS for Apple iPad or Google Android tablet
- Cloud POS (CPOS), which supports the Microsoft Edge, Internet Explorer, and Google Chrome browsers

In all cases, the POS (MPOS and CPOS) shares the same core application code. This point is important for the following reasons:

- The user interface (UI) is consistent, regardless of the platform or form factor.
- Most of the functional capabilities are the same, regardless of the platform or form factor. However, there are some important differences. These differences are noted in this topic.
- In a given store, the POS variations can be combined and can run concurrently. For example, for its main registers, a retailer can use MPOS on computers that run Windows. However, the retailer can supplement those registers with browser-based terminals or mobile devices.
- Customizations and extensions can easily be used across platforms and form factors. Because the core application code is shared, most customizations can be implemented one time instead of multiple times.

### MPOS vs. CPOS

Although MPOS and CPOS are largely the same, there are some important differences that you must understand.

#### MPOS

MPOS on a Windows, iOS, or Android device is an application that is packaged, installed, and serviced on that device.

- **Windows** – The MPOS for Windows application contains all the application code and the embedded commerce runtime (CRT). 
- **iOS/Android** – On these platforms, the application acts as a host for the CPOS application code. In other words, the application code comes from the CPOS server on Microsoft Azure or the Commerce Scale Unit. For more information, see [Retail Store Scale Unit overview](https://docs.microsoft.com/dynamics365/unified-operations/retail/dev-itpro/retail-store-system-begin).

#### CPOS

Because CPOS runs in a browser, the application isn't installed on the device. Instead, the browser accesses the application code from the CPOS server. Therefore, CPOS can't directly access POS hardware or work in an offline state.

### Store deployment considerations

In addition to a platform and form factor, retailers must also choose a deployment option at the store. The following table shows the configurations that are available for each POS option.

| POS application         | Commerce Scale Unit | Available offline |
|-------------------------|---------------|-------------------|
| MPOS for Windows        | Cloud or RSSU | Yes               |
| MPOS for iOS or Android | Cloud or RSSU | No                |
| Cloud POS               | Cloud or RSSU | No                |

#### Commerce Scale Unit

The Commerce Scale Unit is a component that hosts the CRT. The CRT contains all the business logic that the POS uses, and it provides access to the channel database. While they are online, all POS clients in the store use the Commerce Scale Unit. The Commerce Scale Unit can be deployed either in the cloud or in the store.

#### Offline mode

MPOS for Windows supports offline mode. In offline mode, the POS can continue to process sales even if it's disconnected from the Commerce Scale Unit. It can then be synchronized with the channel database when connectivity is restored. MPOS uses its own embedded instance of the CRT and temporarily uses its own local data source (offline SQL Server database). For more information about offline functionality, see [POS offline functionality](https://docs.microsoft.com/dynamics365/unified-operations/retail/pos-offline-functionality).

### POS peripheral/hardware considerations

Retailers must also consider how the POS will access devices and peripherals such as printers, cash drawers, and payment terminals. Only MPOS for Windows supports direct communication with these devices. MPOS for Windows Phone, iOS, or Android, and Cloud POS require a hardware station in order to access these devices. Hardware stations can be dedicated to a POS register or shared among the registers in a store. For more information about hardware stations, see [Configure and install Retail hardware station](https://docs.microsoft.com/dynamics365/unified-operations/retail/retail-hardware-station-configuration-installation).

## Implementation considerations

Consider the following information as you plan your POS implementation in your stores:

- **Functional requirements** – The core business processes and capabilities are the same, regardless of the platform, form factor, or deployment topology. Therefore, most retailers don't have to consider functional requirements when they plan their implementation.
- **Connectivity** – Network availability (wide area network \[WAN\] and local area network \[LAN\]) is a major factor that requires careful consideration. Any benefits that a zero-footprint, cloud-hosted solution brings in terms of cost and simplicity are lost if the system isn't available for business-critical processes.

    Unless the connectivity for a given device is very dependable and resilient, or unless a certain amount of downtime is acceptable to the retailer, we recommend one of the following options:

    - Use MPOS in Windows, and enable offline mode.
    - Deploy an on-premises Commerce Scale Unit.

    These two options aren't mutually exclusive. For the most reliable topology, retailers can deploy a local RSSU to reduce the dependency on internet connectivity or Azure availability, and they can also deploy POS registers where offline mode is enabled if there is an issue with the local server or network.

- **Hardware devices/peripherals** – One important aspect of a Retail POS system is its ability to use POS peripherals such as printers, cash drawers, and payment terminals. Although all the available POS options can use peripheral devices, only MPOS for Windows supports them directly. For all other applications, one or more hardware stations are required. Although this approach adds flexibility, additional components must be deployed, configured, and serviced.
- **System requirements** – The system requirements for the POS application vary. Be sure to check the latest information before you make your choice. For example, because CPOS runs in a browser, it supports a wider range of operating systems. For more information about system requirements, see [System requirements for cloud deployments](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/system-requirements).
- **Deployment and servicing** – The complexity of the deployment and servicing requirements can vary, depending on the application and deployment choices. For example, for a cloud-hosted CPOS deployment, you don't have to install and update on every device. Therefore, this approach greatly reduces complexity and cost. However, if you deploy MPOS on every register and enable offline mode, and you also deploy shared hardware stations, you greatly increase the number of endpoints that must be managed.
