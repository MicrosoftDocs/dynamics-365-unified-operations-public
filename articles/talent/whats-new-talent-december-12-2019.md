---
# required metadata

title: What's new or changed in Dynamics 365 Talent (December 10, 2019)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 12/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (December 10, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2660. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Feature management workspace

The **Feature management** workspace provides a list of features delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them. For more information about Feature management, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the **Feature management** workspace, you can turn them on. Some features may be on by default.
 
At times, an integral feature will be on by default and can't be turned off (for example, the **Feature management** workspace).
 
Once a feature is generally available, it may be turned on or off in production environments. The **Feature management** workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

### Streamlined worker form has moved to the Feature Management workspace (390583)

With this change, the streamlined worker form can now be enabled in the **Feature Management** workspace. This feature has been moved from the **System Parameters** form in **System Administration**.

### Prevent HcmWorkerPayrollInfo records from being written without a worker value (394526)

With this release, **HcmWorkerPayrollInfo** records are no longer created under without worker reference in this scenario. 

### Message log associated to the action isn't populated when the action fails to complete (374007)

This release includes a change to populate the action message log when an action fails in certain scenarios. 

### Common data service integration batch job creation (388030)

With this change, batch jobs for Common Data Service integration are created when the service is enabled.

### Additional pick list values to custom fields aren't reflected in Common Data Service after clicking apply on the custom fields form (379599)

With this change, new pick list values entered in Talent are now synchronized to Common Data Service when you apply your changes.

### Update to Common Data Service for then Leave bank transaction entity turns into an insert on Talent side (352938)

This change corrects an issue where an update to a leave bank transaction creates a new record in Talent.

## In preview

Preview features are only available in **Sandbox** environments.

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.

