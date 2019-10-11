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
ms.search.scope: Talent
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

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract

This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard

This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR

Changes described in this section apply to build number 8.1.2542. The numbers in parentheses in some headings refer to support numbers in Microsoft Dynamics Lifecycle Services (LCS).

### Removal of benefits open enrollment from public preview

In conjunction with our announcement in the blog post [Strategic investments in core HR drive operational excellence](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/10/02/strategic-investments-in-core-hr-drive-operational-excellence/), we are removing benefits open enrollment from public preview on October 18, 2019, in favor of launching new functionality in the future. Production use of the benefits open enrollment feature that is currently in public preview won't be supported. 

### Common Data Service integration is now turned off by default on new provisions (343675)
 
New environments are now provisioned with Common Data Service integration turned off. For more information, see [name of article--still pending](https://docs.microsoft.com/en-us/dynamics365/talent/hr-cds-admin-form).

### Streamlined employee entry and navigation

This functionality is now available in all environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This enables this feature for all users. You can turn this option off at any time.

For more information, see [Streamlined employee data entry](https://docs.microsoft.com/en-us/dynamics365-release-plan/2019wave2/dynamics365-talent/streamlined-employee-data-entry) in the Dynamics 365: 2019 release wave 2 plan.

### Issue: Attract and Onboard create inactive workers in Core HR (380517)

This week's release corrects an issue where Attract and Onboard create inactive workers in Core HR.

### Issue: Workflow fails when manager is signed into another company while terminating an employee (346852)

With this change, the workflow no longer fails based on the legal entity the manager is signed into.

### Issue: Missing information on HcmOnboardingWorkerChecklistTaskEntity (349591)

This release includes additional information on **HcmOnboardingWorkerChecklistTaskEntity**, including:

- **Group name** when assigned type is **group**
- **Employee name** when assigned type is **employee**
- **Manager name** when assigned type is **manager**

### Issue: Entities aren't listed in alphabetical order in Common Data Service Administration (377414)

With this change, entities are listed in alphabetical order in the **CDS Administration** form.

### Issue: Changing the employment type with a future date doesn't allow a position assignment (339958)

This change allows position assignments when changing worker types (for example, from employee to contractor).

### Issue: Updating the Common Data Service Leave bank transaction entity creates a new record in Talent (352938)

The leave transaction is now updated when an update is made to Common Data Service for leave bank transactions.

### Issue: Title for attachments for feedback items displays the feedback description (343765)

With this change, the feedback description no longer displays in the attachment title.

### Issue: Compensation workflow Comments field displays incorrect content (339297)

This change displays the content of the field **%HcmActionState.HcmWorkerActionComment.Comments%**.

### Issue: WorkCalendarEntity and WorkCalendarDayEntity aren't exposed through OData (376329)

In this release, **WorkCalendarEntity** and **WorkCalendarDayEntity** are now available through OData.

### Issue: HCMWorkerEntity is slow when using OData (375221)

Changes increase performance of **HCMWorkerEntity** when using the Excel workbook designer.

### Issue: Manager performance journal entry displays an error after deleting and creating a new one (336061)

This release corrects an issue that arises after deleting a performance journal and immediately creating a new one. This changes the behavior in manager self-service.

## Coming soon

### Print performance reviews

See [Print performance reviews](https://docs.microsoft.com/en-us/dynamics365-release-plan/2019wave2/dynamics365-talent/print-performance-reviews) in the Dynamics 365: 2019 release wave 2 plan.
