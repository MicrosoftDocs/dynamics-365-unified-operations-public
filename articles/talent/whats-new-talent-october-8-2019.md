---
# required metadata

title: What's new or changed in Dynamics 365 Talent (October 8, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 10/08/2019
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
ms.search.validFrom: 2019-10-08
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (October 8, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

The changes that are described in this section apply to build number 8.1.2542. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Removal of benefits open enrollment from public preview

In conjunction with our announcement in the [Strategic investments in core HR drive operational excellence](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/10/02/strategic-investments-in-core-hr-drive-operational-excellence/) blog post, Microsoft is removing the benefits open enrollment feature from public preview on October 18, 2019. Instead, new functionality will be released in the future. Production use of the benefits open enrollment feature that is currently in public preview won't be supported. 

### Common Data Service integration is now turned off by default on new provisions (343675)
 
When new environments are provisioned, Common Data Service integration is now turned off. For more information, see [Configure Common Data Service integration](hr-common-data-service-integration.md).

### Streamlined employee entry and navigation

Functionality for employee entry and navigation is now available in all environments. To turn on this feature, go to **System administration \> Links \> Setup \> System parameters \> Preview features**, and select **Enhanced worker form and navigation**. The feature is then turned for all users. You can turn this option off at any time.

For more information, see [Streamlined employee data entry](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/streamlined-employee-data-entry) in the Dynamics 365: 2019 release wave 2 plan.

### Attract and Onboard create inactive workers in Core HR (380517)

This week's release corrects an issue where Attract and Onboard create inactive workers in Core HR.

### The workflow fails when the manager is signed in to another company while terminating an employee (346852)

The workflow no longer fails based on the legal entity that the manager is signed in to.

### Missing information on HcmOnboardingWorkerChecklistTaskEntity (349591)

This release includes additional information on **HcmOnboardingWorkerChecklistTaskEntity**. Here are some examples:

- **Group name** when the assigned type is **group**
- **Employee name** when the assigned type is **employee**
- **Manager name** when the assigned type is **manager**

### Entities aren't listed in alphabetical order in Common Data Service Administration (377414)

Entities are now listed in alphabetical order on the **CDS Administration** page.

### Changing the employment type with a future date doesn't allow a position assignment (339958)

This change allows for position assignments when worker types are changed (for example, from employee to contractor).

### Updating the Common Data Service Leave bank transaction entity creates a new record in Talent (352938)

The leave transaction is now updated when an update is made to Common Data Service for leave bank transactions.

### The title of attachments for feedback items shows the feedback description (343765)

The feedback description no longer appears in the attachment title.

### Compensation workflow Comments field shows incorrect content (339297)

This change shows the content of the **%HcmActionState.HcmWorkerActionComment.Comments%** field.

### WorkCalendarEntity and WorkCalendarDayEntity aren't exposed through OData (376329)

In this release, **WorkCalendarEntity** and **WorkCalendarDayEntity** are now available through Open Data Protocol (OData).

### HCMWorkerEntity is slow when OData is used (375221)

Changes improve the performance of **HCMWorkerEntity** when the Microsoft Excel workbook designer is used.

### Manager performance journal entry shows an error after deleting a performance journal and creating a new one (336061)

This release corrects an issue that occurs after one performance journal is deleted and a new one is created immediately afterward. This correction changes the behavior in manager self-service.

## Coming soon

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.
