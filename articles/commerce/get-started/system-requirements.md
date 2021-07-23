---
# required metadata

title: System requirements for cloud deployments of Dynamics 365 Commerce
description: This topic lists the system requirements for cloud deployments for the current version of Dynamics 365 Commerce.
author: jashanno 
ms.date: 07/23/2021
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

This topic lists the system requirements for cloud deployments of the current version of Dynamics 365 Commerce. If this step is appropriate, before you install Commerce, you should verify that the system that you're working with meets or exceeds the minimum network, hardware, and software requirements.

## Supported web browsers

The web application can run in any of the following web browsers that run on the specified operating systems:

- Microsoft Edge (latest publicly available version) on Windows 10
- Google Chrome (latest publicly available version) 
- Apple Safari (latest publicly available version)

> [!NOTE]
> It is possible for the Safari browser to show an error during device activation of a Cloud POS device due to an Azure Active Directory token being unattainable. You can resolve this issue by utilizing the [Microsoft Enterprise SSO plug-in for Apple devices](/azure/active-directory/develop/apple-sso-plugin).
> Beginning with release 10.0.17, Internet Explorer is no longer a supported web browser.

To find the latest release for each web browser, go to the software manufacturer's website.

> [!NOTE]
> - To enable Task Recorder to capture screenshots and include them in Microsoft Word documents that are generated, you must install a pre-release Chrome extension. <!---For instructions about how to install the extension, see [Screenshot Extension setup](../../dev-itpro/user-interface/task-recorder).-->
> - The Workflow Editor and Report Designer for Financial reporting are started as ClickOnce applications. They require a 64-bit-compatible operating system. Only Microsoft Edge and Internet Explorer (on a supported version of Microsoft Windows) support ClickOnce applications out of the box. If you're using Chrome, you must install a ClickOnce extension, such as [Meta4](https://chrome.google.com/webstore/detail/meta4-clickonce-launcher/jkncabbipkgbconhaajbapbhokpbgkdc) to use ClickOnce applications. If you use Chrome in incognito mode, make sure that the ClickOnce extension is also enabled for incognito mode.
> - To preview PDF files, we recommend that you use browsers such as Microsoft Edge (latest publicly available version) on Windows 10, or Google Chrome (latest publicly available version) on Windows 10, Windows 8.1, Windows 8, Windows 7, or Google Nexus 10 tablet.

### Supported web browsers for Cloud POS

Cloud point of sale (POS) can run in any of the following web browsers that run on the specified operating systems:

- Microsoft Edge (latest publicly available version) on Windows 10
- Chrome (latest publicly available version) on Windows 10, Windows 8.1, or Windows 7

## Network requirements

- Commerce is designed for networks that have a latency of 250–300 milliseconds (ms) or less. This latency is the latency from a browser client to the Microsoft Azure datacenter that hosts Commerce. We recommend that you test network latency at [AzureSpeed.com](http://www.azurespeed.com).
- Bandwidth requirements for Commerce depend on your scenario. Most typical scenarios require a bandwidth that is more than 50 kilobytes per second (KBps). However, we recommend more bandwidth for scenarios that have high payload requirements, such as scenarios that involve workspaces or extensive customization.

In general, Commerce is optimized for the internet. The number of round trips from a browser client to the Azure datacenter is very small, and the whole payload is compressed.

> [!WARNING]
> Don't calculate bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. Customers who are concerned about bandwidth requirements should use a preview version of Commerce.

## .NET Framework requirements

Commerce requires Microsoft .NET Framework 4.7.1 or later for all ClickOnce applications, such as the document routing agent. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers). For Commerce client components (sealed or legacy installers), it is recommended to always use the latest available version of .NET Framework.

## Supported Microsoft Office applications

The following Microsoft Office applications are supported:

- To run the Microsoft Excel and Word add-ins, you must have Microsoft Office 2016 for Windows installed. For more information about version requirements, see [Troubleshoot the Office integration](../../fin-ops-core/dev-itpro/office-integration/office-integration-troubleshooting.md).
- To view documents that are generated by the Export to Excel or Export to Word functionality, you must have Microsoft Office 2007 or later installed.

## System requirements for Commerce client components

It is critical to perform proper performance testing prior to going live in production. The following are considered minimum system requirements for applications to function. To achieve desired performance, consider concepts like data volumes, transactional load per hour, and customization impact. Proper performance testing both early into implementation and again prior to final testing will allow for any necessary performance improvements to be made and to validate that the base solution meets the expected operation times required.

If the self-service component will utilize a SQL database, it is highly recommended that you review the [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses) section. For SQL Server versions, the recommendation is to use a version that is currently still within the mainstream support date.  Support dates can be searched for, by product, in the [Search Product and Services Lifecycle Information](/lifecycle/products/) article. SQL databases for self-service components requires SQL Server 2017 or newer. The SQL Server version used must have the Full-Text Search feature installed. We recommend that you always use the latest version that is available and that you install all the latest service packs. By following these recommendations, you can help to ensure both compatibility and security. The legacy self-service installers additionally support SQL Server 2016 with Service Pack 2 or later.

If the self-service component will utilize a server certificate, such as Hardware station or Commerce Scale Unit (self-hosted), it is critical to note that certificates must be managed for expiration. By default, a certificate expires in one calendar year (365 days).

> [!NOTE]
> It is critical to note that the legacy Commerce Scale Unit (self-hosted) self-service component additionally utilizes Azure Service to Service authentication. Both the generated Azure web application keys (formerly called *secrets*) and the server certificate must be managed for expiration. By default, a certificate and a generated Azure web application key expires in one calendar year (365 days).
> 
> The supported versions of the .NET Framework have been updated. Legacy self-service client-side components require the Microsoft .NET Framework version 4.7.1 or later to be installed. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers). For the sealed installers, it is recommended to always have the latest version of .NET Framework installed on the target computer.

### Supported operating systems
The following are the supported operating systems for each Commerce self-service installer.

[!WARNING] The Microsoft Windows 7 operating system is not supported for anything other than security-related fixes. As a result, while Dynamics 365 Commerce components may function on Windows 7, there will be no bug fixes that specifically relate to supporting this operating system.

#### Modern POS
 - Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates
     - Windows 10 Pro is not recommended unless as part of a domain so that Windows updates can be appropriately scheduled
 - Windows Server 2019
 - It is not recommended to use Modern POS on the same computer as another self-service component (Hardware station or Commerce Scale Unit (self-hosted))
 - The legacy Self-service installer additionally supports Windows Server 2016 and Windows 10 LTSB with the latest available updates
 - Modern POS for iOS supports iOS version 11 or later
 - Modern POS for Android supports Android version 6.0 or later

> [!NOTE]
> - If Modern POS will use an offline database, the computer must meet all system requirements for Microsoft SQL Server and the system must have no less than 15 GB of disk space available. It is recommended to have no less than 25 GB of disk space available. 

#### Hardware station and Commerce Scale Unit (self-hosted)
 - Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates
     - Windows 10 Pro is not recommended unless as part of a domain so that Windows updates can be appropriately scheduled
 - Windows Server 2019
 - It is not recommended to use a self-service component on the same computer as another self-service component (Modern POS, for example)
 - The legacy self-service installer additionally supports Windows Server 2016 and Windows 10 LTSB

### System requirements
As a reminder, performance testing is crucial to the successful usage of Commerce self-service components. Across all components, the bare minimum system supported for purposes of testing functionality is as follows:

 - Dual-core processor that runs at no less than 2 gigahertz (GHz) per core
 - 3 gigabytes (GB) RAM
 - Internet access and enough network throughput to handle the flow of requests and responses (Note that this is at a computer level and at a network level.)
 - Component specific system requirements such as for SQL Server and IIS
 - No less than 10% of disk space available (It's recommended to have no less than 10 GB of disk space available when SQL Server is used.)

Past the above, as customizations and performance requirements are generated, each component typically requires a more powerful system to meet the user needs.

#### Modern POS
- Minimum supported effective resolution for POS Full layout (PCs and tablets) is 1,024 × 768 (recommended 1366 x 768 or greater)
- Minimum supported effective resolution for POS Compact layout (phones and small tablets) is 320 x 568 (recommended 360x640 or greater)
- It is recommended to have no less than the following for a more performant Modern POS terminal:
    - 128 MB of dedicated graphical memory or 256 MB of shared graphical memory is recommended at a minimum
    - 4 GB of RAM or more, requiring additional review of SQL Server requirements for offline database support
    - Often SQL Express is used for offline databases, and in these scenarios, it is necessary to keep track of the offline database size (10 GB being the maximum size possible)

#### Hardware station 
- Minimum supported system requirements for Microsoft Internet Information Services (IIS)
- Minimum supported system requirements for all third-party hardware attached and used

#### Commerce Scale Unit (self-hosted)
The minimum system requirements for a CSU (self-hosted) is exactly that, the bare minimum necessary to function, typically in a test scenario. The following is not representative of a realistic production environment. It is critical to perform proper performance testing and validate that the computer hardware used will meet the demands of all hardware station, Modern POS, Cloud POS, and any third-party components that will access and utilize the CSU (self-hosted) component or computer. Further, it is highly recomended to use a standard licensed version of SQL Server or better (Enterprise version, for example) so that the full capabilities of the processor and RAM may be utilized. 

The additional requirements are as follows:

- 6 GB of RAM minimum, potentially reaching 64 GB of RAM or more
- 2.4 GHz multi-core CPU, potentially reaching multiple multi-core CPUs on server grade hardware (with a recommendation of a four coure processor)
- Enough disk space to store the sum total of all Commerce data for all associated stores (Channels)
    - Disk requirements could be as low as 10 GB to 20 GB or as much as multiple terabytes

Additionally, it is highly recommended to consider the following aspects of performance when determining CSU (self-hosted) system requirements:

- Number of physical network ports (more ports enhances throughput per second)
- SQL Server log flush size (this directly impacts SQL Server performance)
- Data read and write capabilities (this directly impacts SQL Server performance)
- Whether load balancing will be required across multiple systems handling either separated CSU sub-components (such as multiple Retail Servers or a disaster recovery enabled system for database failover)

## Dynamics AX 2012 R3 Connector requirements
Given the separated nature and specific usage of previous Dynamics AX 2012 R3 components such as Enterprise POS, the two Connector components have been kept in its own section.

### Supported operating systems

The Connector for Microsoft Dynamics AX 2012 R3 has two separate installers, one for Async Server Connector service and one for Real-time service for Microsoft Dynamics AX 2012 R3.
- Both components are 32-bit applications, but they will run on both x86 and x64 architectures.
- Both components are supported on the following operating systems:

    - Windows 10 Pro, Enterprise, and Enterprise LTSB editions
        - Windows 10 Pro is not recommended unless as part of a domain so that Windows updates can be appropriately scheduled
    - Windows Server 2016 and Windows Server 2019

### Minimum system requirements
Similar to a CSU (self-hosted), it is often required to have much larger, server grade hardware to handle the throughput of an entire enterprise architecture of legacy POS systems.  This stated, the following is the absolute minimun to test functionality:

- 2 GB of RAM (4 GB of RAM are recommended)
- 1.6 GHz peak CPU speed per core (2 cores are the minimum)
- At least 15 GB of free space (the channel database can require a large amount of space, possibly in the size of terabytes)

## Requirements for development on local VMs

For information about the requirements for development on local virtual machines (VMs), see [VM that is running on-premises](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md#vm-that-is-running-locally).

## Database collation

The only supported collation for Commerce databases in the cloud is **SQL\_Latin1\_General\_CP1\_CI\_AS**. Please ensure that your SQL Server and database collations in development environments are set to this. Also ensure that any configuration environments that are published to Sandbox have this same collation.

## Additional resources

- [Get an evaluation copy](../../fin-ops-core/dev-itpro/dev-tools/get-evaluation-copy.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](../dev-itpro/retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](../dev-itpro/retail-store-scale-unit-configuration-installation.md)
- [Commerce Data Exchange implementation guidance](../deb-itpro/implementation-considerations-cdx.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
