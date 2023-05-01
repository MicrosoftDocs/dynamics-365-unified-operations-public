---
# required metadata

title: System requirements for cloud deployments of Dynamics 365 Commerce
description: This article lists the system requirements for cloud deployments for the current version of Dynamics 365 Commerce.
author: jashanno 
ms.date: 02/02/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 55651
ms.search.region: Global
ms.search.industry: retail 
ms.author: jashanno
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# System requirements for cloud deployments of Dynamics 365 Commerce

[!include [banner](../includes/banner.md)]

This article lists the system requirements for cloud deployments of the current version of Dynamics 365 Commerce. If this step is appropriate, before you install Commerce, you should verify that the system that you're working with meets or exceeds the minimum network, hardware, and software requirements.

## Supported web browsers

The web application can run in any of the following web browsers that run on the specified operating systems:

- Microsoft Edge (latest publicly available version) on Windows 11, Windows 10
- Google Chrome (latest publicly available version) 
- Apple Safari (latest publicly available version)

> [!NOTE]
> It is possible for the Safari browser to show an error during device activation of a Store Commerce for web device due to an Azure Active Directory token being unattainable. You can resolve this issue by utilizing the [Microsoft Enterprise SSO plug-in for Apple devices](/azure/active-directory/develop/apple-sso-plugin).
>
> As of release 10.0.17, Internet Explorer is no longer a supported web browser.

To find the latest release for each web browser, go to the software manufacturer's website.

> [!NOTE]
> - To enable Task Recorder to capture screenshots and include them in Microsoft Word documents that are generated, you must install a pre-release Chrome extension. <!---For instructions about how to install the extension, see [Screenshot Extension setup](../../dev-itpro/user-interface/task-recorder).-->
> - The Workflow Editor and Report Designer for Financial reporting are started as ClickOnce applications. They require a 64-bit-compatible operating system. Only Microsoft Edge and Internet Explorer (on a supported version of Microsoft Windows) support ClickOnce applications out of the box. If you're using Chrome, you must install a ClickOnce extension, such as [Meta4](https://chrome.google.com/webstore/detail/meta4-clickonce-launcher/jkncabbipkgbconhaajbapbhokpbgkdc) to use ClickOnce applications. If you use Chrome in incognito mode, make sure that the ClickOnce extension is also enabled for incognito mode.
> - To preview PDF files, we recommend that you use browsers such as Microsoft Edge (latest publicly available version) on Windows 11 or Windows 10, or Google Chrome (latest publicly available version) on Windows 11, Windows 10, Windows 8.1, Windows 8, Windows 7, or Google Nexus 10 tablet.

### Supported web browsers for Store Commerce for web

Cloud point of sale (POS) can run in any of the following web browsers that run on the specified operating systems:

- Microsoft Edge (latest publicly available version) on Windows 11, Windows 10
- Chrome (latest publicly available version) on Windows 11, Windows 10, Windows 8.1, Windows 7

## Network requirements

- Commerce is designed for networks that have a latency of 250–300 milliseconds (ms) or less. This latency is the latency from a browser client to the Microsoft Azure datacenter that hosts Commerce. We recommend that you test network latency at [AzureSpeed.com](http://www.azurespeed.com).
- Bandwidth requirements for Commerce depend on your scenario. Most typical scenarios require a bandwidth that is more than 50 kilobytes per second (KBps). However, we recommend more bandwidth for scenarios that have high payload requirements, such as scenarios that involve workspaces or extensive customization.

In general, Commerce is optimized for the internet. The number of round trips from a browser client to the Azure datacenter is very small, and the whole payload is compressed.

> [!WARNING]
> Don't calculate bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. Customers who are concerned about bandwidth requirements should use a preview version of Commerce.

## .NET Framework requirements

Commerce requires the Microsoft .NET Framework version 4.7.2 or later for Call ClickOnce applications, such as the document routing agent. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers). For Commerce client components (sealed or legacy installers), we recommend that you always use the latest version of the .NET Framework that is available.

## Supported Microsoft Office applications

The following Microsoft Office applications are supported:

- To run the Microsoft Excel and Word add-ins, you must have Microsoft Office 2016 for Windows installed. For more information about version requirements, see [Troubleshoot the Office integration](../../fin-ops-core/dev-itpro/office-integration/office-integration-troubleshooting.md).
- To view documents that are generated by the Export to Excel or Export to Word functionality, you must have Microsoft Office 2007 or later installed.

## System requirements for Commerce client components

It's critical to perform proper performance testing prior to going live in production. The following are considered minimum system requirements for applications to function. To achieve desired performance, consider concepts like data volumes, transactional load per hour, and customization impact. Proper performance testing, both early into implementation and again prior to final testing, allows for any necessary performance improvements to be made and validates that the base solution meets the expected operation times required.

If the self-service component will use an SQL database, we highly recommend that you review [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses). We recommend that you use a SQL Server version that is currently still within the mainstream support date. You can search for support dates by product in [Search Product and Services Lifecycle Information](/lifecycle/products/). SQL databases for self-service components require SQL Server 2017 or later. The SQL Server version that is used must have the Full-Text Search feature installed. We recommend that you always use the latest version that is available, and install all the latest service packs. By following these recommendations, you can help ensure both compatibility and security. The legacy self-service installers also support SQL Server 2016 with Service Pack 2 or later.

If the self-service component will use a server certificate, it's critical that you manage certificates for expiration. By default, certificates expire after one calendar year (365 days). Self-service components that use a server certificate include Hardware station or Commerce Scale Unit (self-hosted).

> [!NOTE]
> The legacy Commerce Scale Unit (self-hosted) self-service component uses Azure Service to Service authentication. It's critical that you manage both the generated Azure web application keys (formerly called *secrets*) and the server certificate for expiration. By default, a certificate and a generated Azure web application key expire after one calendar year (365 days).
>
> The supported versions of the .NET Framework have been updated. Self-service client-side components such as Commerce Scale Unit - Self hosted, Store Commerce app, and Hardware Station require that the .NET Framework version 6.0 or later be installed. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers). For the sealed installers, we recommend that you always have the latest version of the .NET Framework installed on the target computer.

### Supported operating systems

This section lists the supported operating systems for each Commerce self-service installer.

> [!WARNING]
> The Windows 7 operating system isn't supported for anything except security-related fixes. Therefore, although Commerce components might work on Windows 7, there will be no bug fixes that are specifically related to supporting this operating system.

#### Store Commerce

- Store Commerce and Modern POS is supported on the following operating systems:

    - Windows 11 (Pro, Enterprise, Enterprise LTSC, and IoT Enterprise LTSC editions.)
    - Windows 10 (Pro, Enterprise, Enterprise LTSC, and IoT Enterprise LTSC editions) with the latest available updates.
    - Windows Server 2022 (Standard, Essentials.) 
    - Windows Server 2019 (Standard, Essentials) with the latest available updates.

    > [!NOTE]
    > Windows 10 Pro and Windows 11 Pro are not recommended, except as part of a domain, so that Windows updates can be appropriately scheduled.


- We recommend that you don't use Modern POS on the same computer as another self-service component (for example, Hardware station or Commerce Scale Unit \[self-hosted\]).
- iOS support requires iOS version 11 or later.
- Android support requires Android version 6.0 or later.
- Windows Server 2019 is supported.
- We don't recommend that you use the Store Commerce app on the same computer as another self-service component (for example, Hardware station or Commerce Scale Unit \[self-hosted\]).
- iOS support requires iOS version 16 or later.
- Android support requires Android version 7.0 or later.


> [!NOTE]
> If an offline database will be used, the computer must meet all system requirements for SQL Server. Additionally, the system must have at least 15 gigabytes (GB) of available disk space. However, we recommend a minimum of 25 GB of available disk space.

#### Hardware station and Commerce Scale Unit (self-hosted)

- Windows 11, 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates are supported.

    > [!NOTE]
    > Windows 10 Pro and Windows 11 Pro are not recommended, except as part of a domain, so that Windows updates can be appropriately scheduled.

- Windows Server 2019 is supported.
- We don't recommend that you use a self-service component on the same computer as another self-service component (for example, the Store Commerce app).
- The legacy self-service installer also supports Windows Server 2016 and Windows 10 LTSB.

### System requirements

Remember that performance testing is crucial to the successful use of Commerce self-service components. Across all components, the following bare-minimum system is supported for the purpose of testing functionality:

- Dual-core processor that runs at no less than 2 gigahertz (GHz) per core.
- 3 GB of RAM.
- Internet access and enough network throughput to handle the flow of requests and responses. (Note that this requirement is at both a computer level and a network level.)
- Component-specific system requirements, such as requirements for SQL Server and Internet Information Services (IIS).
- At least 10 percent of disk space is available. (We recommend that you've no less than 10 GB of available disk space when SQL Server is used.)

Additionally, as customizations and performance requirements are generated, each component typically requires a more powerful system to meet user needs.

#### Store Commerce app

- The minimum supported effective resolution for POS Full layout mode (PCs and tablets) is 1,024 × 768. (However, we recommend 1366 × 768 or more.)
- The minimum supported effective resolution for POS Compact layout mode (phones and small tablets) is 320 x 568. (However, we recommend 360 × 640 or more.)
- Here are the minimum recommendations for a more performant Store Commerce app terminal:

    - A minimum of 128 MB of dedicated graphical memory or 256 MB of shared graphical memory are recommended.
    - 4 GB or more of RAM are recommended. This recommendation requires additional review of SQL Server requirements for offline database support.
    - SQL Express is often used for offline databases. In these scenarios, it's necessary to keep track of the offline database size. (The maximum possible size is 10 GB.)

#### Hardware station

- The minimum supported system requirements for IIS
- The minimum supported system requirements for all third-party hardware that is attached and used

#### Commerce Scale Unit (self-hosted)

The minimum system requirements for Commerce Scale Unit (self-hosted) describe the bare minimum that are required to function, typically in a test scenario. The requirements that are described here aren't representative of a realistic production environment. It's critical that you do appropriate performance testing and validate that the computer hardware that is used will meet the demands of Hardware station, Store Commerce app, Store Commerce for web, and any third-party components that will access and use the Commerce Scale Unit (self-hosted) component or computer. Furthermore, we highly recommend that you use a standard licensed version of SQL Server or better (for example, Enterprise version) to take advantage of the full capabilities of the processor and RAM.

Here are the additional requirements:

- A minimum of 6 GB of RAM, although 64 GB or more of RAM might be required
- A 2.4 GHz multi-core CPU, although multiple multi-core CPUs on server-grade hardware might be required (A four-core processor is recommended.)
- Enough disk space to store the sum total of all Commerce data for all associated stores (channels)

    Disk requirements might be as little as 10 GB to 20 GB, or as much as multiple terabytes.

Additionally, we highly recommend that you consider the following aspects of performance when you're determining system requirements for Commerce Scale Unit (self-hosted):

- The number of physical network ports (More ports enhance throughput per second.)
- SQL Server log flush size (This factor directly affects SQL Server performance.)
- Data read and write capabilities (This factor directly affects SQL Server performance.)
- Will load balancing be required across multiple systems that handle separated Commerce Scale Unit subcomponents (such as multiple Retail Servers or a disaster recovery–enabled system for database failover)

## Dynamics AX 2012 R3 Connector requirements

Given the separated nature and specific usage of previous Dynamics AX 2012 R3 components such as Enterprise POS, the two Connector components have been kept in a separate section.

### Supported operating systems

The Connector for Microsoft Dynamics AX 2012 R3 has two separate installers: one for Async Server Connector service and one for Real-time service for Microsoft Dynamics AX 2012 R3.

- Both components are 32-bit applications, but they'll run on both x86 and x64 architectures.
- Both components are supported on the following operating systems:

    - Windows 11, Windows 10 Pro, Windows Enterprise, and Windows Enterprise LTSB editions

        > [!NOTE]
        > Windows 10 Pro isn't recommended, except as part of a domain, so that Windows updates can be appropriately scheduled.

    - Windows Server 2016 and Windows Server 2019

### Minimum system requirements

As for Commerce Scale Unit (self-hosted), much larger, server-grade hardware is often required to handle the throughput of a whole enterprise architecture of legacy POS systems. Nevertheless, here's the absolute minimum that is required to test functionality:

- 2 GB of RAM (However, 4 GB of RAM are recommended.)
- 1.6 GHz peak CPU speed per core (Two cores are the minimum.)
- 15 GB of free space (The channel database can require a large amount of space. The size might even be as much as multiple terabytes.)

## Recommended network exceptions

Often (especially in corporate environments), network-related security requires that specific exceptions be noted. In these security-focused networks, we recommend that you add, at a minimum, the following exceptions to a network-related allow list:

- \*.static.akamaitechnologies.com
- \*.azure.com
- \*.dynamics.com
- \*.microsoft.com
- \*.visualstudio.com
- \*.windows.net

## Requirements for development on local VMs

For information about the requirements for development on local virtual machines (VMs), see [VM that is running on-premises](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md#vm-that-is-running-locally).

## Database collation

The only supported collation for Commerce databases in the cloud is **SQL\_Latin1\_General\_CP1\_CI\_AS**. Please ensure that your SQL Server and database collations in development environments are set to this. Also ensure that any configuration environments that are published to Sandbox have this same collation.

## Additional resources

[Get an evaluation copy](../../fin-ops-core/dev-itpro/dev-tools/get-evaluation-copy.md)

[Dynamics 365 Commerce architecture overview](../commerce-architecture.md)

[Select an in-store topology](../dev-itpro/retail-in-store-topology.md)

[Device management implementation guidance](../implementation-considerations-devices.md)

[Configure and install Commerce Scale Unit (self-hosted)](../dev-itpro/retail-store-scale-unit-configuration-installation.md)

[Commerce Data Exchange implementation guidance](../dev-itpro/implementation-considerations-cdx.md)

<!--[Configure, install, and activate the Store Commerce app](../retail-modern-pos-device-activation.md)-->

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
