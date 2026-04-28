---
title: Asset Management mobile app deprecation
description: The Asset Management mobile app for Microsoft Dynamics 365 Supply Chain Management is deprecated. Learn the deprecation timeline, transition guidance for existing and new customers, and source-code availability.
author: 
ms.author: 
ms.reviewer: kamaybac
ms.search.form:
ms.topic: conceptual
ms.date: 04/30/2026
ms.custom: 
  - bap-template
---

# Asset Management mobile app deprecation

[!include [banner](../../includes/banner.md)]

> [!IMPORTANT]
> The Asset Management mobile app is deprecated as of April 30, 2026. Microsoft continues to provide critical maintenance and keeps the app available for installation through [Dynamics 365 apps in the Power Platform admin center](https://learn.microsoft.com/en-us/power-platform/admin/manage-apps) through October 30, 2026. After that date, the app is removed and no further updates are issued. Existing installations continue to work in customer tenants. There is no first-party replacement. The source code is available under the MIT license at [microsoft/scmsamples-EnterpriseAssetManagement](https://github.com/microsoft/scmsamples-EnterpriseAssetManagement) for customers and partners who want to take ownership.

## Deprecation timeline

| Date | Milestone |
|---|---|
| April 30, 2026 | Deprecation announced. Active development stops. The app enters a 6-month critical-maintenance window during which it remains available for installation through the Power Platform admin center, and Microsoft issues only critical fixes. |
| October 30, 2026 | End of support. The app is removed from the Power Platform admin center. Existing installations continue to function in customer tenants without further updates from Microsoft. |

## Guidance for existing customers

### Continue using the app as-is

Existing installations require no action. Microsoft delivers any critical fixes during the maintenance window through the same Power Platform admin center channel as previous versions. After October 30, 2026, the installed app continues to function in the customer tenant, but no further updates are issued.

### Customize the app for in-tenant use

For additive customizations to the data model, such as adding new fields, tables, or security roles, use solution layering in the Power Apps maker portal. These customizations live in the customer tenant's unmanaged solution layer and are preserved when Microsoft delivers managed-solution updates during the maintenance window.

For customizations to the canvas app itself, such as screens, formulas, or UI changes, customizations made in the maker portal can be overwritten when Microsoft delivers a critical update during the maintenance window. Customers who require canvas-app-level customization during the maintenance window should either defer customization until after October 30, 2026, when Microsoft no longer delivers updates, or take ownership of the source by following the guidance in the next section.

### Take ownership of the app source

Customers and partners who want to continue evolving the app can build from the open-source source code at [microsoft/scmsamples-EnterpriseAssetManagement](https://github.com/microsoft/scmsamples-EnterpriseAssetManagement). The source code is licensed under the MIT license.

By default, builds from the open-source source code identify Microsoft as the solution publisher in Microsoft Dataverse. This is appropriate for in-tenant evaluation but not for redistribution under another brand. Customers who plan to redistribute or operate the app under their own publisher must change the publisher in the solution metadata and update the customization prefix throughout the source before building. The repository README documents this process.

After a customer produces their own build under their own publisher, transitioning an existing tenant from the Microsoft-published version to the customer-published version requires uninstalling the Microsoft-published solutions (`msdyn_EnterpriseAssetManagementMobileV2` and `msdyn_EnterpriseAssetManagementMobileAnchor`) and importing the customer-built solution.

## Guidance for new customers

Microsoft does not recommend installing the Asset Management mobile app. There is no first-party replacement product. Customers who need field-level work order management for Supply Chain Management can:

- Evaluate Microsoft AppSource for partner-built alternatives.
- Build a custom solution by forking the open-source source code at [microsoft/scmsamples-EnterpriseAssetManagement](https://github.com/microsoft/scmsamples-EnterpriseAssetManagement).

## Support

For product issues with the Asset Management mobile app during the maintenance window, customers should use their existing Microsoft support agreements and Dynamics 365 support channels. After October 30, 2026, Microsoft does not provide product support for the app. Customers who require ongoing support should plan for transition to a partner alternative or take ownership of the open-source source code. Issues filed against the open-source repository are not triaged.
