---
title: Asset Management mobile app open-source release
description: Microsoft is releasing the Asset Management mobile app for Microsoft Dynamics 365 Supply Chain Management as open source so you can customize the app to fit your needs. Learn the timeline, transition guidance, and how to build a custom version from the source.
author: 
ms.author: 
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 05/01/2026
ms.custom: 
  - bap-template
---

# Asset Management mobile app open-source release

[!include [banner](../../includes/banner.md)]

> [!IMPORTANT]
> The Asset Management mobile app is now available as an open-source sample at [microsoft/scmsamples-EnterpriseAssetManagement](https://github.com/microsoft/scmsamples-EnterpriseAssetManagement). Same functionality, freely customizable. The existing app remains available for installation through [Dynamics 365 apps in the Power Platform admin center](/power-platform/admin/manage-apps) until October 31, 2026, with critical fixes from Microsoft during this transition period. After that date, the app is no longer distributed through the admin center; existing installations continue to work in customer tenants.

Until now, canvas-app customizations made in Power Apps Studio weren't preserved across official updates. Releasing the source code as open source removes that limitation: you can build from the source, customize it freely, and deploy under your own publisher without your changes being overwritten by Microsoft updates.

## Timeline

| Date | Milestone |
|---|---|
| May 1, 2026 | Source code released as open source. The app enters a 6-month transition period during which it remains available for installation through the Power Platform admin center, with critical fixes from Microsoft. |
| October 31, 2026 | End of the transition period. Microsoft maintenance concludes and the app is no longer distributed through the Power Platform admin center. Existing installations continue to function in customer tenants. |

## Guidance for existing customers

### Continue using the installed app

Existing installations require no action. Microsoft delivers any critical fixes during the maintenance window through the same Power Platform admin center channel as previous versions. After October 31, 2026, the installed app continues to function in the customer tenant. Customers who plan to evolve the app beyond that date should follow the [Build from the open-source code](#build-from-the-open-source-code) guidance.

### Customize the app for in-tenant use

For additive customizations to the data model, such as adding new fields, tables, or security roles, use solution layering in the Power Apps maker portal. These customizations live in the customer tenant's unmanaged solution layer and are preserved when Microsoft delivers managed-solution updates during the maintenance window.

For customizations to the canvas app itself, such as screens, formulas, or UI changes, the recommended path is to build from the [open-source code](#build-from-the-open-source-code) so your changes persist. Customizations made directly in Power Apps Studio aren't preserved across Microsoft updates during the maintenance window.

### Build from the open-source code

To customize the app and make it your own, build from the open-source code at [microsoft/scmsamples-EnterpriseAssetManagement](https://github.com/microsoft/scmsamples-EnterpriseAssetManagement). The source code is licensed under the MIT license, which permits free use, modification, and redistribution.

By default, builds from the open-source code use a Microsoft-branded sample publisher (`AssetManagementMobileSample`, display name "Microsoft Asset Management Mobile Sample") in Microsoft Dataverse. This is distinct from the first-party Microsoft publisher used by in-market Dynamics 365 products. The default publisher is appropriate when you customize and run the app in your own organization's tenant. If you plan to distribute your custom build to other organizations, change the publisher and customization prefix to your own brand before building. The repository README documents this process.

After producing a custom build under your own publisher, transitioning an existing tenant requires deleting the existing solutions (`msdyn_EnterpriseAssetManagementMobileV2` and `msdyn_EnterpriseAssetManagementMobileAnchor`) and importing the custom-built solution. For details on deleting solutions, see [Work with solutions in Power Apps](/power-apps/maker/data-platform/solutions-overview#work-with-solutions-in-power-apps).

## Guidance for new customers

For Supply Chain Management customers who need field-level work order management, the recommended path is to build a custom solution from the open-source code at [microsoft/scmsamples-EnterpriseAssetManagement](https://github.com/microsoft/scmsamples-EnterpriseAssetManagement). The MIT-licensed source can be customized freely and deployed under your own publisher to fit your needs. Alternatively, evaluate Microsoft AppSource for partner-built alternatives.

The existing app remains available for installation through the Power Platform admin center until October 31, 2026. For new deployments, build from the open-source code instead.

## Support

For product issues during the maintenance window, customers should use their existing Microsoft support agreements and Dynamics 365 support channels. After October 31, 2026, Microsoft does not provide product support for the app. Issues filed against the open-source repository are not triaged.
