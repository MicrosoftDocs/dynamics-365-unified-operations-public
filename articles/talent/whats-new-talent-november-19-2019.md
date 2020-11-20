---
# required metadata

title: What's new or changed in Dynamics 365 Talent (November 19, 2019)
description: This article describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 11/19/2019
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
ms.search.validFrom: 2019-11-19
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (November 19, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This article describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2621. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Platform update 31 for Finance and Operations apps

For more information, see [Preview features in Platform update 31 for Finance and Operations apps (January 2020)](https://docs.microsoft.com/dynamics365/fin-ops-core/dev-itpro/get-started/whats-new-platform-update-31).

### Feature management workspace (383856)

The **Feature management** workspace provides a list of features delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them. For more information about Feature management, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the **Feature management** workspace, you can turn them on. Some features may be on by default.
 
At times, an integral feature will be on by default and can't be turned off (for example, the **Feature management** workspace).
 
Once a feature is generally available, it may be turned on or off in production environments. The **Feature management** workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

### Message appears when canceled action exists for a position (382887)

The following message no longer appears when you select a specific position and a canceled action is all that's available for the position: **An incomplete action is in progress for position xxxxxx**.

### In learning analytics, the Course type and Status display incorrect data (381151)

This week's release updated learning analytics to correctly display **Course type** and **Status**.

### Personnel number should display in the New worker form banner (383832)

In the **New worker** form, **Personnel number** now displays in the banner for quick reference.

### Position start date determines the Job record to use when retrieving a compensation level during hire (350361)

In this release, **Compensation start date** determines the level assigned to the new job.

### Custom pick list fields in the Position table aren't synchronized to Common Data Service (387503)

With this release, pick list items are now synchronized with Common Data Service.

### Worker address entity doesn't synchronize with Common Data Service while importing new data (349673)

In this week's release, address data now synchronizes with Common Data Service while importing new data.

## In preview

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.
