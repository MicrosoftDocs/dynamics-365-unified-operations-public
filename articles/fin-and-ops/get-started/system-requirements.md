---
# required metadata

title: System requirements for cloud deployments
description: This topic lists the system requirements for the current version of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, for cloud deployments.
author: sericks007
manager: AnnBe
ms.date: 08/02/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core
# ms.tgt_pltfrm: 
ms.custom: 55651
ms.assetid: e564d51d-42d3-47c5-b388-93b8219c692a
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8

---

# System requirements for cloud deployments

[!include[banner](../includes/banner.md)]

This topic lists the system requirements for the current version of Microsoft Dynamics 365 for Finance and Operations, Enterprise edition, for cloud deployments. Before you install Finance and Operations, when this step is appropriate, verify that the system that you're working with meets or exceeds the minimum network, hardware, and software requirements.

## Supported web browsers
The web application can run in any of the following web browsers that run on the specified operating systems:

-   Microsoft Edge (latest publicly available version) on Windows 10
-   Internet Explorer 11 on Windows 10, Windows 8.1, or Windows 7
-   Google Chrome (latest publicly available version) on Windows 10, Windows 8.1, Windows 8, Windows 7, or Google Nexus 10 tablet
-   Apple Safari (latest publicly available version) on Mac OS X 10.10 (Yosemite), 10.11 (El Capitan) or 10.12 (Sierra), or Apple iPad

To find the latest release for each web browser, go to the software manufacturer’s website. 

> [!NOTE]
> -   You must install a pre-release Chrome extension to enable Task Recorder to capture screenshots and include them in Microsoft Word documents that are generated. <!---For instructions about how to install the extension, see [Screenshot Extension setup](../../dev-itpro/user-interface/task-recorder).-->
> -   The Workflow Editor is started as a ClickOnce application. Only Microsoft Edge and Internet Explorer (on a supported version of Microsoft Windows) support ClickOnce applications. The Workflow Editor ClickOnce application requires a 64-bit-compatible operating system.
> -   The Report Designer for Financial reporting is started as a ClickOnce application. It requires a 64-bit-compatible operating system. If you’re using Chrome, you must install a ClickOnce extension to download the Report Designer client. If you use Chrome in Incognito mode, make sure that the ClickOnce extension is also enabled for Incognito mode.
> -   To preview PDF files, we recommend that you use browsers such as Microsoft Edge (latest publicly available version) on Windows 10, or Google Chrome (latest publicly available version) on Windows 10, Windows 8.1, Windows 8, Windows 7, or Google Nexus 10 tablet.

### Supported web browsers for Retail Cloud POS

Retail Cloud POS can run in any of the following web browsers that run on the specified operating systems:

-   Microsoft Edge (latest publicly available version) on Windows 10
-   Internet Explorer 11 on Windows 10, Windows 8.1, or Windows 7
-   Chrome (latest publicly available version) on Windows 10, Windows 8.1, or Windows 7

## Network requirements
-   Finance and Operations is designed for networks that have a latency of 250–300 milliseconds (ms) or less. This latency is the latency from a browser client to the Microsoft Azure datacenter that hosts Finance and Operations. We recommend that you test network latency at <http://www.azurespeed.com>.
-   Bandwidth requirements for Finance and Operations depend on your scenario. Most typical scenarios require a bandwidth of more than 50 kilobytes per second (KBps). However, we recommend more bandwidth for scenarios that have high payload requirements, such as scenarios that involve workspaces or extensive customization.

In general, Finance and Operations is optimized for the internet. The number of round trips from a browser client to the Azure datacenter is very small, and the whole payload is compressed. 

> [!WARNING]
> Don't calculate bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. Customers who are concerned about bandwidth requirements should use a preview version of Finance and Operations.

## .NET Framework requirements
Finance and Operations requires the Microsoft .NET Framework version 4.6.2 for all ClickOnce applications, such as the document routing agent. For installation instructions, see [Installing the .NET Framework](https://msdn.microsoft.com/en-us/library/5a4x27ek(v=vs.110).aspx).

## Supported Microsoft Office applications
The following Microsoft Office applications are supported in cloud and on-premises deployments of Finance and Operations:

-   To run the Microsoft Excel and Word add-ins, you must have Microsoft Office 2016 for Windows or Mac installed. For more information about version requirements, see [Office integration troubleshooting](../../dev-itpro/office-integration/office-integration-troubleshooting.md).
-   To view documents that are generated by the Export to Excel or Export to Word functionality, you must have Microsoft Office 2007 or later installed.

## Retail Modern POS requirements

> [!NOTE]
> If Retail Modern POS will use an offline database, the computer must meet all system requirements for Microsoft SQL Server. A Retail Modern POS offline database will work on Microsoft SQL Server 2012 with Service Pack 3 or later, Microsoft SQL Server 2014 with Service Pack 2 or later, and Microsoft SQL Server 2016. We recommend that you always use the latest version that is available, and that you install all the latest service packs.

### Supported operating systems

-   Retail Modern POS is a 32-bit application, but it will run on both x86 and x64 architectures.
-   Retail Modern POS is supported only on Windows 10 Pro, Enterprise, and Enterprise Long Term Servicing Branch (LTSB) editions.

### Minimum system requirements

-   The minimum supported resolution is 1,280 × 1,024.
-   The computer that Retail Modern POS runs on must meet these requirements:

    -   It must have, at a minimum, a dual-core processor that runs at no less than 2 gigahertz (GHz).
    -   It must have, at a minimum, 3 gigabytes (GB) of random-access memory (RAM).
    -   It must have internet access.

## Retail hardware station requirements
### Supported operating systems

-   Retail hardware station is a 32-bit application, but it will run on both x86 and x64 architectures.
-   Retail hardware station is supported on the following operating systems:

    -   Windows 7 Professional, Enterprise, and Ultimate editions 
    
        > [!NOTE]
        > Windows 7 is supported only if Internet Explorer 11 is manually installed on the system.

    -   Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions
    -   Windows 10 Pro, Enterprise, and Enterprise LTSB editions

### Minimum system requirements

The computer must meet all system requirements for installing and using the following items:

-   Internet Information Services (IIS)
-   Third-party hardware

## Retail Store Scale Unit requirements
### Supported operating systems

-   Retail Store Scale Unit is a 32-bit application, but it will run on both x86 and x64 architectures.
-   Retail Store Scale Unit is supported on the following operating systems:

    -   Windows 7 Professional, Enterprise, and Ultimate editions
    -   Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions
    -   Windows 10 Pro, Enterprise, and Enterprise LTSB editions

### Minimum system requirements

-   4 GB of RAM
-   1.6 GHz peak CPU speed per core (Two cores are the minimum.)
-   At least 10 GB of free space (The channel database can require a large amount of space.)

### Recommended system requirements

-   6 GB of RAM
-   2.4 GHz i7 (or equivalent) peak CPU speed per core (Four cores are recommended.)
-   At least 10 GB of free space (The channel database can require a large amount of space.)

## Connector requirements
### Supported operating systems

-   The Connector for Microsoft Dynamics AX has two separate installers, one for Async Server Connector service and one for Real-time service for Dynamics AX 2012 R3.
-   Both components are 32-bit applications, but they will run on both x86 and x64 architectures.
-   Both components are supported on the following operating systems:

    -   Windows 7 Professional, Enterprise, and Ultimate editions
    -   Windows 8.1 Update 1 Professional, Enterprise, and Embedded editions
    -   Windows 10 Pro, Enterprise, and Enterprise LTSB editions
    -   Microsoft Windows Server 2012 R2 and Microsoft Windows Server 2016

### Minimum system requirements
-   2 GB of RAM (4 GB of RAM are recommended.)
-   1.6 GHz peak CPU speed per core (Two cores are the minimum.)
-   At least 10 GB of free space (The channel database can require a large amount of space.)

## Requirements for development on local VMs
For information about the requirements for development on local virtual machines (VMs), see [VM running on-premises](../../dev-itpro/dev-tools/access-instances.md).


## See also

[Get an evaluation copy of Dynamics 365 for Finance and Operations, Enterprise edition](../../dev-itpro/dev-tools/get-evaluation-copy.md)
