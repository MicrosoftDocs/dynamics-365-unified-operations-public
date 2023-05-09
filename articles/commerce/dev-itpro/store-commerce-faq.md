---
title: Store Commerce app FAQ
description: This article covers frequently asked questions about the Microsoft Dynamics 365 Commerce Store Commerce app and Commerce SDK migration. 
author: josaw1
ms.date: 05/26/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-03-01
ms.dyn365.ops.version: AX 10.0.25
---

# Store Commerce app FAQ

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article covers frequently asked questions about the Microsoft Dynamics 365 Commerce Store Commerce app and Commerce software development kit (SDK) migration.

### Why is MPOS being deprecated?

MPOS (also known as Modern POS, or Modern point of sale) uses the legacy Universal Windows App (UWP) rendering framework. Support for the UWP platform has been reduced, starting with Visual Studio 2019. The Store Commerce app is a Windows Presentation Foundation (WPF) shell application that uses the Microsoft Edge WebView2 control, which is more performant and supports the development of better experiences through components such as IndexedDB. Store Commerce also offers superior application lifecycle management options. 

For more information, see [Store Commerce app](store-commerce.md) and [Migrate Modern POS to Store Commerce](pos-extension/migrate-mpos-store-commerce.md). 

### Does the Store Commerce app offer the same functionality as MPOS?

Yes. The Store Commerce app has full functional parity with MPOS, including offline mode and dedicated hardware station. 

### Do I have to reactivate my registers after migrating to the Store Commerce app? 

No. Store Commerce for Windows offers an in-place upgrade option that captures the MPOS device token before uninstalling MPOS, which eliminates the need to reactivate. For more information about the `--inplaceupgradefrommodernpos` parameter, see [Store Commerce app](store-commerce.md). 

### I'm already using the Commerce SDK, do I need to migrate?

If you're already using the Commerce SDK for POS and Commerce Scale Unit (CSU) extensions and don't have any remaining instances of MPOS, you don't have any additional migration tasks. If you have any instances of MPOS, you should [migrate to the Store Commerce app](pos-extension/migrate-mpos-store-commerce.md).

### I'm already using the Store Commerce app, do I need to migrate?

No, you don't have to migrate if you're using the Store Commerce app and the Commerce SDK to build CSU extensions.

### Will the Retail SDK be available in infrastructure as a service (IaaS) virtual machine (VM)? 

No. Retail SDK will be removed from the IaaS VM (the Microsoft Dynamics Lifecycle Services development environment) effective in October 2023.

### Will legacy installers be supported?

No, legacy installers will stop working effective in October 2023. You should migrate to the sealed installers. 

### Will sealed MPOS be supported?

No. Sealed MPOS won't be supported effective October 2023. You must migrate your [sealed MPOS instances to the Store Commerce app](pos-extension/migrate-mpos-store-commerce.md).

### What happens if I continue to use the Retail SDK or MPOS beyond the deprecation date?

Existing deployments using Retail SDK and MPOS will remain functional after the deprecation date. However, Microsoft won't provide support or bug fixes for issues you encounter. There will be no newer versions of Retail SDK or MPOS released after October 2023. 

### Does the Commerce SDK apply for on-premises deployments too?

Yes. For on-premises deployments, the new [Commerce SDK](retail-sdk/migrate-commerce-sdk.md) enables sealed base installers where extensions are deployed via a dedicated installer that only contains extensions.

## Additional resources

[Store Commerce app capabilities](../store-commerce-capabilities.md)

[Modernizing the Dynamics 365 Commerce in-store technology stack](https://www.microsoft.com/download/details.aspx?id=103896)

[Commerce SDK Tech Talk series](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-commerce-extensions)

[POS extension overview](pos-extension/pos-extension-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
