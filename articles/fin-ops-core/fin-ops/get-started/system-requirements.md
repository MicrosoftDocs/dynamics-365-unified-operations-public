---
# required metadata

title: System requirements for cloud deployments
description: This article lists the system requirements for the current version of finance and operations apps.
author: sericks007
ms.date: 02/08/2022
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
ms.assetid: e564d51d-42d3-47c5-b388-93b8219c692a
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-08-30
ms.dyn365.ops.version: Platform update 8

---

# System requirements for cloud deployments

[!include [banner](../includes/banner.md)]

This article lists the system requirements for the current version of finance and operations apps. You should verify that the system that you're working with meets or exceeds the minimum network, hardware, and software requirements.

## Supported web browsers

Users can access the apps by using the most recent versions of these popular browsers: 

- Microsoft Edge (recommended: [Chromium-based Edge](https://support.microsoft.com/microsoft-edge/download-the-new-microsoft-edge-based-on-chromium-0f4a3dd7-55df-60f5-739f-00010dba52cf))
- Google Chrome
- Apple Safari
- Internet Explorer 11 (deprecated, not recommended)

To find the latest release for each web browser, go to the software manufacturer's website.

> [!NOTE]
> For optimal performance and an optimal experience, we recommend that you use the latest version of a modern browser, especially Microsoft Edge. 
> 
> **Version 10.0.21 and later:** Users of old versions of Microsoft Edge and Google Chrome (version 83 and earlier) will receive prompts to update their browser to the latest version.

### Internet Explorer deprecation

Support for Internet Explorer 11 was deprecated in December 2020, with end of support for the browser occurring in August 2021. For more information, see [Internet Explorer deprecation announcement](../../dev-itpro/get-started/removed-deprecated-features-platform-updates.md#platform-updates-for-version-10015-of-finance-and-operations-apps).

Starting in version 10.0.20, users accessing finance and operations apps with Internet Explorer will start seeing notifications about the end of support for that browser. Before August 17, 2021, Internet Explorer users will see an informational message that Internet Explorer support is soon ending. After that date, Internet Explorer users will see a warning that support has officially ended. Organizations are encouraged to keep these notifications on unless Internet Explorer is mandated for your users, in which case you can choose to suppress these notifications by disabling the **Internet Explorer end-of-support notifications** feature and relying on internal processes for migrating your user base to Microsoft Edge or another modern browser. 

Starting in version 10.0.25, the use of Internet Explorer 11 will be blocked in finance and operations apps. If your organization wants to block Internet Explorer earlier, and you're using version 10.0.21 or later, contact Microsoft Support. 

To prepare organizations and users for the upcoming block of Internet Explorer, in January 2022, Internet Explorer users will start to receive a non-dismissible error message that states that Internet Explorer support will soon be blocked. This error message is **not** controlled by the **Internet Explorer end-of-support notifications** feature. Customers will have to contact Microsoft Support if this message must be suppressed for their organization.

### Special considerations

- To enable Task Recorder to capture screenshots and include them in Microsoft Word documents that are generated, you must install a pre-release Chrome extension.
- The Workflow Editor and Report Designer for Financial reporting are started as ClickOnce applications. They require a 64-bit-compatible operating system. Only Microsoft Edge and Internet Explorer (on a supported version of Microsoft Windows) support ClickOnce applications out of the box. If you're using Chrome, you must install a ClickOnce extension, such as [Meta4](https://chrome.google.com/webstore/detail/meta4-clickonce-launcher/jkncabbipkgbconhaajbapbhokpbgkdc) to use ClickOnce applications. If you use Chrome in incognito mode, make sure that the ClickOnce extension is also enabled for incognito mode.
- To preview PDF files, we recommend that you use browsers such as Microsoft Edge (latest publicly available version) on Windows 10, or Google Chrome (latest publicly available version) on Windows 10, Windows 8.1, Windows 8, Windows 7, or Google Nexus 10 tablet.

## Network requirements

- The app is designed for networks that have a latency of 250–300 milliseconds (ms) or less. This latency is the latency from a browser client to the Microsoft Azure datacenter that hosts the app. We recommend that you test network latency at [AzureSpeed.com](https://www.azurespeed.com).
- Bandwidth requirements for the app depend on your scenario. Most typical scenarios require a bandwidth that is more than 50 kilobytes per second (KBps). However, we recommend more bandwidth for scenarios that have high payload requirements, such as scenarios that involve workspaces or extensive customization.

In general, the app is optimized for the internet. The number of round trips from a browser client to the Azure datacenter is very small, and the whole payload is compressed.

> [!WARNING]
> Don't calculate bandwidth requirements from a client location by multiplying the number of users by the minimum bandwidth requirements. The concurrent usage of a given location is very difficult to calculate. Customers who are concerned about bandwidth requirements should use a preview version of the app.

## .NET Framework requirements

The app requires the Microsoft .NET Framework version 4.6.2 for all ClickOnce applications, such as the document routing agent. For installation instructions, see [Install the .NET Framework for developers](/dotnet/framework/install/guide-for-developers).

## Supported Microsoft Office applications

The following Microsoft Office applications are supported in cloud:

- To run the Microsoft Excel and Word add-ins, you must have Microsoft Office 2016 for Windows installed. For more information about version requirements, see [Troubleshoot the Office integration](../../dev-itpro/office-integration/office-integration-troubleshooting.md).
- To view documents that are generated by the Export to Excel or Export to Word functionality, you must have Microsoft Office 2007 or later installed.

## Requirements for development on local VMs

For information about the requirements for development on local virtual machines (VMs), see [VM that is running locally](../../dev-itpro/dev-tools/access-instances.md#vm-that-is-running-locally).

## Database collation

The only supported collation for application databases in the cloud is **SQL\_Latin1\_General\_CP1\_CI\_AS**. Please ensure that your SQL Server and database collations in development environments are set to this. Also ensure that any configuration environments that are published to Sandbox have this same collation.

## Additional resources

[Get evaluations copies](../../dev-itpro/dev-tools/get-evaluation-copy.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

