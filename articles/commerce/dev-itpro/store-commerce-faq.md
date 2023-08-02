---
title: Store Commerce app FAQ
description: This article answers frequently asked questions about the Microsoft Dynamics 365 Commerce Store Commerce app and Commerce SDK migration.
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

This article answers frequently asked questions about the Microsoft Dynamics 365 Commerce Store Commerce app and Commerce software development kit (SDK) migration.

### Why is MPOS being deprecated?

Modern point of sale (Modern POS or MPOS) uses the legacy Universal Windows App (UWP) rendering framework. As of Visual Studio 2019, support for the UWP platform has been reduced. The Store Commerce app is a Windows Presentation Foundation (WPF) shell application that uses the Microsoft Edge WebView2 control. This control has better performance and supports the development of better experiences through components such as IndexedDB. Store Commerce also offers superior application lifecycle management options.

For more information, see [Store Commerce app](store-commerce.md) and [Migrate Modern POS to Store Commerce](pos-extension/migrate-mpos-store-commerce.md).

### Does the Store Commerce app offer the same functionality as MPOS?

Yes. The Store Commerce app has full functional parity with MPOS, including offline mode and dedicated hardware station.

### Do I have to reactivate my registers after I migrate to the Store Commerce app?

No. Store Commerce for Windows offers an in-place upgrade option that captures the MPOS device token before MPOS is uninstalled. Therefore, reactivation isn't required. For more information about the `--inplaceupgradefrommodernpos` parameter, see [Store Commerce app](store-commerce.md).

### I'm already using the Commerce SDK. Do I have to migrate?

If you're already using the Commerce SDK for POS and Commerce Scale Unit (CSU) extensions, and you don't have any remaining instances of MPOS, no additional migration tasks are required. If you have any instances of MPOS, you should [migrate to the Store Commerce app](pos-extension/migrate-mpos-store-commerce.md).

### I'm already using the Store Commerce app. Do I have to migrate?

No, you don't have to migrate if you're using the Store Commerce app and the Commerce SDK to build CSU extensions.

### Will the Retail SDK be available in the IaaS VM?

No. In October 2023, the Retail SDK will be removed from the infrastructure as a service (IaaS) virtual machine (VM). (The IaaS VM is the Microsoft Dynamics Lifecycle Services development environment.)

### Will legacy installers be supported?

No. Legacy installers will stop working in October 2023. You should migrate to the sealed installers.

### Will sealed MPOS be supported?

No. Support for sealed MPOS will end in October 2023. You must migrate your [sealed MPOS instances to the Store Commerce app](pos-extension/migrate-mpos-store-commerce.md).

### What happens if I continue to use the Retail SDK or MPOS beyond the deprecation date?

Existing deployments that use the Retail SDK and MPOS will remain functional after the deprecation date. However, Microsoft won't provide support or updates for issues that you encounter. No newer versions of the Retail SDK or MPOS will be released after October 2023.

### Does the Commerce SDK apply to on-premises deployments too?

Yes. For on-premises deployments, the new [Commerce SDK](retail-sdk/migrate-commerce-sdk.md) enables sealed base installers where extensions are deployed via a dedicated installer that contains only extensions.

## Additional resources

[Store Commerce app capabilities](../store-commerce-capabilities.md)

[Modernizing the Dynamics 365 Commerce in-store technology stack](https://www.microsoft.com/download/details.aspx?id=103896)

[Commerce SDK Tech Talk series](https://community.dynamics.com/blogs/post/?postid=a7ae4e0b-3af0-48a0-8943-9ee9d0f941c6)

[POS extension overview](pos-extension/pos-extension-overview.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
