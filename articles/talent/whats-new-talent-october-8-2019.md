---
# required metadata

title: What's new or changed in Dynamics 365 Talent (October 8, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 10/8/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
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
# "What's new or changed in Dynamics 365 Talent (October 8, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2542.

### Public preview: Benefits open enrollment removal

In conjunction with our strategic investment announcement [here](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/10/02/strategic-investments-in-core-hr-drive-operational-excellence/) in core HR we are removing the benefits open enrollment feature in its current state and how it evolves going forward.  On October 18th, 2019 benefits open enrollment will be removed from public preview in all Dynamics 365 Talent environments.  As this feature will not GA, we will not support production use of benefits open enrollment and will look to launch a new open enrollment experience as part of the recently announced Advanced Benefits functionality.

### CDS Integration is now turned off by default on new provisions (343675)
 
Provisioning new environments will now provision with the CDS integration turned off. For more information view updated integration documentation [here](https://docs.microsoft.com/en-us/dynamics365/talent/hr-cds-admin-form).

### Streamlined employee entry and navigation

This functionality is now available in all environments. To turn this feature on, navigate to **System administration > Links > Setup > System parameters > Preview features**. Select **Enhanced worker form and navigation**. This will enable these changes for all users. You can turn this option off at any time.

### Talent allows Attract created Worker records in Talent through CDS integration when they should not (380517)

This week's release corrects an issue where attract and onboard were creating inactive workers in Core HR.

### Workflow fails when terminating an employee and the manager is logged into "another" company (346852)

With this change, workflow no longer fails based on the legal entity the manager is logged into.

### Missing information on HcmOnboardingWorkerChecklistTaskEntity (349591)

This release includes additional information on the HcmOnboardingWorkerChecklistTaskEntity, including: Group name when assigned type is group, Employee name when assigned type is employee and Manager name when assigned type is manager.

### Entities are not listed in alphabetic order in CDS Administration form (377414)

With this change, entities are not listed in alphabetic order in the CDS Administration form.

### Changing employment type with a future date does not allow a position assignment (339958)

This change will allow for position assignments when changing between worker types (Employee/Contractor).

### Updating CDS Leave bank transaction entity creates a new record in Talent (352938)

Changes have been made to update the leave transaction when an update is made to CDS for leave bank transactions.

### Title for attachments for feedback items displays the feedback description (343765)

With this change the feedback description will no longer display in the attachment title.

### Compensation workflow Comments field left as not displaying correct content (339297)

This change will now display the content of the field %HcmActionState.HcmWorkerActionComment.Comments%.

### WorkCalendarEntity and WorkCalendarDayEntity are not exposed through OData (376329)

In this release the WorkCalendarEntity and WorkCalendarDayEntity are now available through OData.

### HCMWorkerEntity slow using OData (375221)

Change have been made to increase performance of the HCMWorkerEntity when using the Excel workbook designer.

### Manager performance journal entry displays an error after deleting and creating a new one (336061)

This release includes a change that corrects an issue after deleting a performance journal and immediately creating an new on. This changes the behavior in manager self-service.

## Coming soon

### Print performance reviews

With this new functionality: Employees, managers, and HR will be able to print an employee's performance review. Performance reviews will be available using a "Print review" option that will launch Microsoft Word to view and print the performance review.
