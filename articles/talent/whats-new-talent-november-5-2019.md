---
# required metadata

title: What's new or changed in Dynamics 365 Talent (November 5, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 11/05/2019
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
# ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2019-11-05
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (November 5, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2598. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Copy a Core HR instance

In this week's release, you can use Microsoft Dynamics Lifecycle Services (LCS) to copy a Microsoft Dynamics 365 Talent: Core HR database to a sandbox environment. If you have another sandbox environment, you can also copy the database from that environment to a targeted sandbox environment. For more information, see:

- [Broader environment management](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/broader-environment-management) in the Dynamics 365: 2019 release wave 2 plan

- [Copy a Core HR instance](hr-copy-instance.md) in Talent documentation

### Common Data Service integration batch jobs aren't created when Common Data Service integration is enabled (388030)

This change will create batch jobs for Common Data Service integration when it's enabled.

### The HcmPersonImageEntity doesn't resize the person image when uploaded (369469)

This week's release changes how images are resized for better performance when imported through data management.

### A position's Available for assignment date can be earlier than the Activation date (340103)

With this change, a warning will appear if you select an **Available for assignment date** that's earlier than the position's **Activation date**.

### Can't create a compensation change request in employee self-service for step-based plans (376872)

This release corrects an issue when requesting compensation changes through employee self-service for step-based plans. 

### Reason code doesn't sync to Common Data Service if the description is longer than 30 characters, Core HR allows 60 (352682)

with this change, reason codes with more than 30 characters will be updated in Common Data Service. Changes made in Common Data Service will also be reflected back in Talent.

### Address integration from Talent to Finance and Operations (351961)

This release fixes an issue where addresses updated in Talent weren't updating in Finance and Operations. Changes to address blocks will now update.

## Coming soon

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.

### Feature management workspace

Features are added and updated in every release. The feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them.

To learn more about the changes coming with feature management, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
