---
title: Store Commerce app
description: This article covers frequently asked questions about the Store Commerce app and Commerce SDK migration. 
author: josaw1
ms.date: 10/25/2022
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2022-03-01
ms.dyn365.ops.version: AX 10.0.25
---

# Store Commerce app - FAQ

[!include [banner](../includes/banner.md)]

## Why is MPOS being deprecated?

MPOS (aka Modern POS, or Modern Point of Sale) uses the legacy Universal Windows App (UWP) rendering framework. Support for the UWP platform has been reduced, starting with Visual Studio 2019. The Store Commerce app is a Windows Presentation Foundation shell application that uses the Microsoft Edge WebView2 control, which is far more performant and supports the development of better experiences through components such as IndexedDB. Store Commerce also offers superior application lifecycle management options. 

See the [Store Commerce app](store-commerce.md) and [Migrate Modern POS to Store Commerce](pos-extension/migrate-mpos-store-commerce.md) help topics for more information. 

## Does Store Commerce app offer the same functionality as MPOS?

Yes. Store Commerce app has full functional parity with MPOS, including offline mode and dedicated hardware station. 

## Do I have to reactivate my registers after migrating to Store Commerce app? 

No. Store commerce for Windows offers an in-place upgrade option that captures the Modern POS device token before uninstalling MPOS, which eliminates the need to reactivate. Read more about the `--inplaceupgradefrommodernpos` parameter in the [Store Commerce app](store-commerce.md) help topic. 

## I am already using Commerce SDK, do I need to migrate?

If you are already using Commerce SDK for POS and Scale Unit extensions, and don’t have any remaining instances of Modern POS, you don't have any additional migration tasks. If you have any instances of MPOS, you should [migrate to Store Commerce app](pos-extension/migrate-mpos-store-commerce.md).

## I am already using Store Commerce app, do I need to migrate?

No, you don’t have to migrate if you are using Store Sommerce app and using Commerce SDK to build any Scale Unit extensions you have.

## Will Retail SDK be available in IaaS VM? 

No. Retail SDK will be removed from IaaS VM (LCS Dev environment) effective October 2023.

## Will Legacy installers be supported?

No. legacy installers will stop working effective October 2023. You should migrate to the sealed installers. 

## Will sealed MPOS be supported?

No. Sealed MPOS will not be supported effective October 2023. You have to migrate your [sealed MPOS instances to Store Commerce app](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Flearn.microsoft.com%2Fen-us%2Fdynamics365%2Fcommerce%2Fdev-itpro%2Fpos-extension%2Fmigrate-mpos-store-commerce&data=05|01|stuharg%40microsoft.com|547685291c6e42c588e608db3f9ff74c|72f988bf86f141af91ab2d7cd011db47|1|0|638173728507629660|Unknown|TWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D|3000|||&sdata=9mO9bNpB41%2BfHrqRzKYL1Yzf%2FB89SKjHP6QLfyFvMys%3D&reserved=0).

## What happens if I continue to use Retail SDK or MPOS beyond the deprecation date?

Existing deployments using Retail SDK and MPOS will remain functional. However, Microsoft will not provide support or bug fixes for issues you encounter. In addition, there will be no newer versions of Retail SDK or MPOS released after October 2023. 

## Does Commerce SDK apply for on-prem deployments too?

Yes. For on-prem deployments, the new [Commerce SDK](retail-sdk/migrate-commerce-sdk.md) enables sealed base installers where extensions are deployed via a dedicated installer containing extensions only.





## Additional Resources

[Store Commerce app capabilities](../store-commerce-capabilities.md)

[Modernizing the Dynamics 365 Commerce in-store technology stack](https://www.microsoft.com/download/details.aspx?id=103896)

[Commerce SDK Tech Talk Series](https://community.dynamics.com/365/dynamics-365-fasttrack/b/techtalks/posts/techtalk-series-commerce-extensions)

[Store Commerce Extensions Overview](pos-extension/pos-extension-overview.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
