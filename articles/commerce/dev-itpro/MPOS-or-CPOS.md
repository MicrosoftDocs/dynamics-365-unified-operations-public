---
title: Choose between Store Commerce app and Store Commerce for web
description: This article provides an overview of the key differences between the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web.
author: josaw1
ms.date: 02/18/2026
ms.topic: overview
ms.author: josaw
ms.reviewer: v-griffinc
ms.search.region: global
ms.search.validFrom: 2017-10-12
ms.custom: 
  - bap-template
---

# Choose between Store Commerce app and Store Commerce for web

[!include [banner](../includes/banner.md)]

This article explains the key differences between the Microsoft Dynamics 365 Commerce Store Commerce app and Store Commerce for web. It describes various factors that retailers who implement Dynamics 365 Commerce should consider to help them make the best choice for their requirements. It also gives implementers more background, tips, and guidance for factors that they should consider when they deploy Dynamics 365 Commerce. By reviewing and following this guidance as part of the deployment process, implementers can avoid problems that might affect user satisfaction or performance.

## Insights

Commerce provides a wide range of deployment and topology options. Therefore, retailers can choose the components and configuration that best meet their business and technology requirements. One aspect of implementation that requires careful consideration is the choice of a platform and form factor for the point of sale (POS) component.

### POS platform and form factor considerations

Commerce supports the following POS options:

- Store Commerce for Microsoft Windows
- Store Commerce for iOS and Android
- Store Commerce for web, which supports the Microsoft Edge and Google Chrome browsers
- Store Commerce app for Microsoft Windows (Modern Point of Sale [MPOS] was deprecated in October 2023.)  

In all cases, the POS (Store Commerce app and Store Commerce for web) shares the same core application code. This point is important for the following reasons:

- The user interface (UI) is consistent, regardless of the platform or form factor.
- Most of the functional capabilities are the same, regardless of the platform or form factor. However, there are some important differences. This article notes these differences.
- In each store, you can combine and run concurrently the POS variations. For example, for its main registers, a retailer can use Store Commerce on computers that run Windows. However, the retailer can supplement those registers with browser-based terminals or mobile devices.
- You can easily use customizations and extensions across platforms and form factors. Because the core application code is shared, you can implement most customizations one time instead of multiple times.

### Store Commerce app vs. Store Commerce for web

Although the Store Commerce app and Store Commerce for web are largely the same, some important differences exist.

#### Store Commerce

Store Commerce is a desktop application that you install and service on a device.

- **Windows** – The Store Commerce app for Windows contains the application code, Commerce Runtime (CRT), and Hardware Station (HWS).
- **iOS/Android** – On these platforms, the application acts as a host for the Store Commerce for web application code. In other words, the application code comes from the Commerce Scale Unit (CSU). For more information, see [Commerce Scale Unit overview](retail-store-system-begin.md).

#### Store Commerce for web

Because Store Commerce for web runs in a browser, you don't install the application on the device. Instead, the browser accesses the application code from the Commerce Scale Unit (CSU). Therefore, Store Commerce for web can't directly access POS hardware or work in an offline state.

### Store deployment considerations

In addition to a platform and form factor, retailers must also choose a deployment option at the store. The following table shows the configurations that are available for each POS option.

| POS application            | Commerce Scale Unit | Available offline | Local HWS support |
|----------------------------|---------------------|-------------------|-------------------|
| Store Commerce for Windows | Cloud or RSSU       | Yes               | Yes               |
| Store Commerce for Android | Cloud or RSSU       | No                | Yes               |
| Store Commerce for iOS     | Cloud or RSSU       | No                | Yes               |
| Store Commerce for web     | Cloud or RSSU       | No                | No                |

#### Commerce Scale Unit

The Commerce Scale Unit is a component that hosts the CRT. The CRT contains all the business logic that the POS uses, and it provides access to the channel database. While they're online, all POS clients in the store use the Commerce Scale Unit. You can deploy the Commerce Scale Unit either in the cloud or in the store.

#### Offline mode

Store Commerce for Windows supports offline mode. In offline mode, the POS can continue to process sales even if it's disconnected from the Commerce Scale Unit. It can then synchronize with the channel database when connectivity is restored. Store Commerce uses its own embedded instance of the CRT and temporarily uses its own local data source (offline SQL Server database). For more information about offline functionality, see [POS offline functionality](pos-offline-functionality.md).

### POS peripheral and hardware considerations

Retailers must also consider how the POS accesses devices and peripherals such as printers, cash drawers, and payment terminals. Hardware stations can be dedicated to a POS register or shared among the registers in a store.

| POS application            | Local HWS OPOS | Network peripherals | Shared HWS support |
|----------------------------|----------------|---------------------|--------------------|
| Store Commerce for Windows | Yes            | Yes                 | Yes                |
| Store Commerce for Android | No             | Yes                 | Yes                |
| Store Commerce for iOS     | No             | Yes                 | Yes                |
| Store Commerce for web     | No             | No                  | Yes                |

For more information about hardware stations, see [Configure and install Retail hardware station](retail-hardware-station-configuration-installation.md).

## Implementation considerations

Consider the following information as you plan your POS implementation in your stores:

- **Functional requirements** – The core business processes and capabilities are the same, regardless of the platform, form factor, or deployment topology. Therefore, most retailers don't need to consider functional requirements when they plan their implementation.
- **Connectivity** – Network availability (wide area network \[WAN\] and local area network \[LAN\]) is a major factor that requires careful consideration. Any benefits that a zero-footprint, cloud-hosted solution brings in terms of cost and simplicity are lost if the system isn't available for business-critical processes.

    Unless the connectivity for a given device is dependable and resilient, or unless a certain amount of downtime is acceptable to the retailer, use one of the following options:

    - Use Store Commerce in Windows, and enable offline mode.
    - Deploy an on-premises Commerce Scale Unit.

    These two options aren't mutually exclusive. For the most reliable topology, retailers can deploy a local RSSU to reduce the dependency on internet connectivity or Azure availability, and they can also deploy POS registers where offline mode is enabled if there's an issue with the local server or network.

- **Hardware devices/peripherals** – One important aspect of a Retail POS system is its ability to use POS peripherals such as printers, cash drawers, and payment terminals. Although all the available POS options can use peripheral devices, only Store Commerce for Windows supports them directly. For all other applications, one or more hardware stations are required. Although this approach adds flexibility, you must deploy, configure, and service more components.
- **System requirements** – The system requirements for the POS application vary. Be sure to check the latest information before you make your choice. For example, because Store Commerce for web runs in a browser, it supports a wider range of operating systems. For more information about system requirements, see [System requirements for cloud deployments](../../fin-ops-core/dev-itpro/get-started/system-requirements.md).
- **Deployment and servicing** – The complexity of the deployment and servicing requirements can vary, depending on the application and deployment choices. For example, for a cloud-hosted Store Commerce for web deployment, you don't have to install and update on every device. Therefore, this approach greatly reduces complexity and cost. However, if you deploy Store Commerce on every register and enable offline mode, and you also deploy shared hardware stations, you greatly increase the number of endpoints that must be managed.
- **Web browser considerations** - Popular web browsers have the ability to put idle tabs to sleep to free up system resources. This feature can cause unexpected behavior when using Store Commerce for web. If you're using Store Commerce for web, disable this feature.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
