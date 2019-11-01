---
# required metadata

title: What's new or changed in Dynamics 365 Talent (October 29, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 10/29/2019
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
ms.search.validFrom: 2019-10-29
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 Talent (October 29, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2586.

### Delete Parties with no roles should be on by default. - (371233)

In Talent, when you provision a new environment the parameter to delete parties if no roles exist will be turned on by default.  When deleting a worker the Party associated with the worker does not get removed unless this setting is on. This change will limit duplicate records in the global address book when importing workers and changes/reimporting of data is needed.

### Draft and cancelled leave requests should be allowed to be deleted in CDS - (376999)

With this change, leave requests with a status of draft or cancelled can now be deleted via CDS.

### Adding additional list values to custom fields are not being reflected in CDS after clicking apply on the custom fields form. - (379599)

With this change, adding new pick list values to an existing custom field already sync'ed with CDS, will now be available in CDS after applying your changes in the custom fields form.

### Applying (onboarding) checklists across legal entities when more than one employment exists - (371270)

In this week's release, you will now be able to apply checklists to employees with more than one employment. This can be done using the worker form->checklists functionality.

### Benefits open enrollment preview feature has been removed.

The preview option for benefits open enrollment has been removed. In conjunction with our strategic investment announcement [here](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/10/02/strategic-investments-in-core-hr-drive-operational-excellence/) in core HR we have removed the benefits open enrollment feature in its current state and how it evolves going forward. We will look to launch a new open enrollment experience as part of the recently announced Advanced Benefits functionality.

## Coming soon

### Print performance reviews

With this new functionality: Employees, managers, and HR will be able to print an employee's performance review. Performance reviews will be available using a "Print review" option that will launch Microsoft Word to view and print the performance review.

### Feature management workspace

Features are added and updated in every release. The Feature management experience provides a workspace where you can view a list of features that have been delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them

To learn more about the changes coming with feature management view the article posted [HERE](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).
