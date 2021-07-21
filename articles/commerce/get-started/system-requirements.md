---
# required metadata

title: System requirements for cloud deployments of Dynamics 365 Commerce
description: This topic lists the system requirements for cloud deployments for the current version of Dynamics 365 Commerce.
author: jashanno 
ms.date: 05/11/2021
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

Commerce requires Microsoft .NET Framework 4.7.1 or later for all ClickOnce applications, such as the document routing agent. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers). For the Commerce client components (Sealed or legacy installers), it is recommended to always use the latest available version of .NET Framework.

## Supported Microsoft Office applications

The following Microsoft Office applications are supported:

- To run the Microsoft Excel and Word add-ins, you must have Microsoft Office 2016 for Windows installed. For more information about version requirements, see [Troubleshoot the Office integration](../../fin-ops-core/dev-itpro/office-integration/office-integration-troubleshooting.md).
- To view documents that are generated by the Export to Excel or Export to Word functionality, you must have Microsoft Office 2007 or later installed.

## System requirements for Commerce client components

It is critical to perform proper performance testing prior to going live in production. The following are considered minimum system requirements for applications to function. To achieve desired performance, consider concepts like data volumes, transactional load per hour, and customization impact. Proper performance testing both early into implementation and again prior to final testing will allow for any necessary performance improvements to be made and to validate that the base solution meets the expected operation times required.

If the Self-service component will utilize a SQL database, it is highly recommended that you review the [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses) section. For SQL Server versions, the recommendation is to use a version that is currently still within the mainstream support date.  Support dates can be searched for, by product, in the [Search Product and Services Lifecycle Information](/lifecycle/products/) article. SQL databases for Self-service components requires SQL Server 2017 or newer. The SQL Server version used must have the Full-Text Search feature installed. We recommend that you always use the latest version that is available and that you install all the latest service packs. By following these recommendations, you can help to ensure both compatibility and security. The legacy Self-service installers additionally support SQL Server 2016 with Service Pack 2+.

If the Self-service component will utilize a server certificate, such as Hardware station or Commerce Scale Unit (Self-hosted), it is critical to note that certificates must be managed for expiration. By default, a certificate expires in one calendar year (365 days).

> [!NOTE]
> It is critical to note that the legacy Commerce Scale Unit (Self-hosted) Self-service component additionally utilizes Azure Service to Service authentication. Both the generated Azure web application keys (formerly called *secrets*) and the server certificate must be managed for expiration. By default, a certificate and a generated Azure web application key expires in one calendar year (365 days).
> Starting August 1, 2019, the supported versions of the .NET Framework have been updated. Legacy Self-service client-side components require the Microsoft .NET Framework version 4.7.1 or later to be installed. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers). For the sealed installers, it is recommended to always have the latest version of .NET Framework installed on the target computer.

### Supported operating systems
The following are the supported operating systems for each Commerce Self-service installer.

[!WARNING] The Microsoft Windows 7 operating system is no longer supported for anything other than security-related fixes. As a result, while Dynamics 365 Commerce components may function on Windows 7, there will be no bug fixes that specifically relate to supporting this operating system.

#### Modern POS
 - Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates
     - Windows 10 Pro is not recommended unless as part of a domain so that Windows updates can be appropriately scheduled
 - Windows Server 2019
 - It is not recommended to use Modern POS on the same computer as another Self-service component (Hardware station or Commerce Scale Unit (Self-hosted))
 - The legacy Self-service installer additionally supports Windows Server 2016 and Windows 10 LTSB with the latest available updates
 - Modern POS for iOS supports iOS version 11 or later
 - Modern POS for Android supports Android version 6.0 or later

> [!NOTE]
> - If Modern POS will use an offline database, the computer must meet all system requirements for Microsoft SQL Server and the system must have no less than 15 GB of disk space available. It is recommended to have no less than 25 GB of disk space available. 

#### Hardware station and Commerce Scale Unit (Self-hosted))
 - Windows 10 (Pro, Enterprise, LTSC, and IOT Enterprise editions) with the latest available updates
     - Windows 10 Pro is not recommended unless as part of a domain so that Windows updates can be appropriately scheduled
 - Windows Server 2019
 - It is not recommended to use a Self-service component on the same computer as another Self-service component (Modern POS, for example)
 - The legacy Self-service installer additionally supports Windows Server 2016 and Windows 10 LTSB

### System requirements










MPOS
### Minimum system requirements

- The minimum supported effective resolution for POS Full layout (PCs and tablets) is 1,024 × 768 (recommended 1366 x 768 or greater)
- The minimum supported effective resolution for POS Compact layout (phones and small tablets) is 320 x 568 (recommended 360x640 or greater)
- The computer that Modern POS runs on must meet these requirements:

    - It must have, at a minimum, a dual-core processor that runs at no less than 2 gigahertz (GHz).
    - It must have, at a minimum, 3 gigabytes (GB) of random-access memory (RAM). When combining with SQL Server for offline, no less than 4 GB of RAM is required.
    - It must have internet access.

## Retail hardware station requirements

> [!NOTE]
> Starting August 1, 2019, Retail hardware station and other client-side components require that the .NET Framework version 4.7.1 or later be installed. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers).
> It is critical to note that this component utilizes a server certificate. Server certificates must be managed for expiration. By default, a certificate expires in one calendar year (365 days).

### Minimum system requirements

The computer must meet all system requirements for installing and using the following items:

- Microsoft Internet Information Services (IIS)
- Third-party hardware


## Commerce Scale Unit (self-hosted) requirements

Note that the minimum system requirements listed below are the bare minimum necessary to get a Commerce Scale Unit to function in a test scenario. The following is not representative of a realistic production environment. It is critical to perform proper performance testing and validate that the hardware used will meet the needs of the users. For SQL Server versions, the recommendation is to use a version that is currently still within the mainstream support date. Support dates can be searched for, by product, in  [Search Product and Services Lifecycle Information](/lifecycle/products/).


### Minimum system requirements

> [!NOTE]
> The following are the minimum system requirements for Commerce Scale Unit.  Both these and the recommended requirements are the minimum possible for testing and basic functionality.  It is crucial to perform performance testing and validate that the hardware used for Commerce Scale Unit meets expectations.

- 4 GB of RAM
- 1.6 GHz i5 (or equivalent) minimum CPU speed per core (2 cores are the minimum).
- At least 15 GB of free space (the channel database can require a large amount of space).
- A supported version of SQL Server.  It is recommended to use a standard license or better for a Commerce Scale Unit (self-hosted), as the Express edition could cause synchronization issues due to its known limitations. For more information, see [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses).

### Recommended system requirements

- 6 GB of RAM
- 2.4 GHz i7 (or equivalent) minimum CPU speed per core (4 cores are recommended).
- At least 20 GB of free space (the channel database can require a large amount of space).
- - A supported version of SQL Server. It is recommended to use a standard license or better for a Commerce Scale Unit (self-hosted), as the Express edition could cause synchronization issues due to its known limitations. For more information, see [SQL Server versions and licenses](../dev-itpro/implementation-considerations-cdx.md#sql-server-versions-and-licenses).

It would be in an organization's best interest to also take the following items into consideration when determining personal hardware needs:

- Number of physical network ports (more ports enhances throughput per second).
- SQL Server log flush size (this directly impacts SQL Server performance).
- Data read and write capabilities (this directly impacts SQL Server performance).
- Number of CPU(s) core, number of simultaneous threads per core, and speed per core (this impacts overall throughput of the system).
- Whether load balancing will be required.

## Dynamics AX 2012 R3 Connector requirements

### Supported operating systems

- The Connector for Microsoft Dynamics AX 2012 R3 has two separate installers, one for Async Server Connector service and one for Real-time service for Microsoft Dynamics AX 2012 R3.
- Both components are 32-bit applications, but they will run on both x86 and x64 architectures.
- Both components are supported on the following operating systems:

    - Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions.
    - Windows 10 Pro, Enterprise, and Enterprise LTSB editions.
    - Windows Server 2016 and Windows Server 2019.
    - It is not recommended to use Commerce components on Windows 10 Pro unless within a domain as Windows 10 Pro doesn't allow for advanced management of updates to the operating system.

### Minimum system requirements

- 2 GB of RAM (4 GB of RAM are recommended).
- 1.6 GHz peak CPU speed per core (2 cores are the minimum).
- At least 15 GB of free space (the channel database can require a large amount of space, possibly in the size of terabytes).

## Requirements for development on local VMs

For information about the requirements for development on local virtual machines (VMs), see [VM that is running on-premises](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md#vm-that-is-running-locally).

## Database collation

The only supported collation for Commerce databases in the cloud is **SQL\_Latin1\_General\_CP1\_CI\_AS**. Please ensure that your SQL Server and database collations in development environments are set to this. Also ensure that any configuration environments that are published to Sandbox have this same collation.

## Additional resources

- [Get an evaluation copy](../../fin-ops-core/dev-itpro/dev-tools/get-evaluation-copy.md)
- [Dynamics 365 Commerce architecture overview](../commerce-architecture.md)
- [Select an in-store topology](retail-in-store-topology.md)
- [Device management implementation guidance](../implementation-considerations-devices.md)
- [Configure, install, and activate Modern POS (MPOS)](../retail-modern-pos-device-activation.md)
- [Configure and install Commerce Scale Unit (self-hosted)](retail-store-scale-unit-configuration-installation.md)
- [Commerce Data Exchange implementation guidance](implementation-considerations-cdx.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
