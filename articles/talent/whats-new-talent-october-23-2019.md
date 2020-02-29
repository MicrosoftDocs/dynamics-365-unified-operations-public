---
# required metadata

title: What's new or changed in Dynamics 365 Talent (October 23, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 10/23/2019
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
ms.search.validFrom: 2019-10-23
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (October 23, 2019)

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2569. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Platform update 30 for Finance and Operations apps

For more information, see [What's new or changed in Platform update 30 for Finance and Operations apps (November 2019)](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/whats-new-platform-update-30).

### Remove benefits open enrollment preview feature

In conjunction with our announcement in the [Strategic investments in core HR drive operational excellence](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/10/02/strategic-investments-in-core-hr-drive-operational-excellence) blog post, Microsoft is removing the benefits open enrollment feature from public preview on October 18, 2019. Instead, new functionality will be released in the future. Production use of the benefits open enrollment feature that is currently in public preview won't be supported.

### Error while selecting the country/region on the Worker form a second time (350294)

With this week's release, the issue has been corrected when selecting a country/region on the **Worker** form.

### Financial dimension values default to the Combination display field when Do not allow manual entry is set to true (340097)

With this change, when setting up financial dimensions and using the option to not allow manual entry, the system will correctly default the dimension value into the **Combination display** field.

### New relationship types should be added to Relationship lookup in the personal contacts form (347691)

This release includes new capabilities to add new relationship types in the **Relationship types** table and reflect those changes in the relationship lookup for personal contacts.

### Additional list values in custom fields aren't reflected in Common Data Service (379599)

With this week's release, adding a new list value to an existing custom field that's already synchronized with Common Data Service, the new pick list values will now appear after applying changes to the entity.

### On the Terms of employment page, all employees' terms of employment appear after selecting Open in Excel (348073)

With this release, only the selected employees' terms of employment will open in Excel. All company security is also honored.

### The association between the Work calendar holiday entity and the Work calendar entity is missing in Common Data Service (324178)

This relationship has been added with the release. This change will enable working days of an employee to display in PowerApps. 

### Error when using employee self-service workflows with configurable hierarchies (370132)

In this release, better messaging is available on how to configure workflows using configurable hierarchies. 

### System allows creation of new positions where the Available for assignment date is earlier than the Activation date (340103)

This change will display a warning when the **Available for assignment** date is before the position's **Activation** date.

## Coming soon

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.

### Feature management workspace

Features are added and updated in every release. The feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them.

To learn more about the changes coming with feature management, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
