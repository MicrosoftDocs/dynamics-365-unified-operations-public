---
# required metadata

title: What's new or changed in Dynamics 365 Talent (March 14, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 03/14/2019
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
ms.search.validFrom: 2019-03-14
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (March 14, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Talent.

## Changes in Attract
There are minor bug fixes included with this release.

## Changes in Onboarding
There are minor bug fixes included with this release.

## Changes in Core HR
**Build 8.1.2186**

### Performance management not working in all scenarios when using duplicate security roles
Changes made in this release enable performance management scenarios when using the out-of-the-box or duplicated roles.

### Mass assign checklists to workers
With this change, you can now select multiple employees and bulk assign one or more checklists to those employees. 

### Platform update 24 for Finance and Operations
For additional details about Platform update 24 for Finance and Operations, see [What's new or changed in Finance and Operations platform update 24 (March 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-24). Significant changes in platform 24 include: 

- Alerts are enabled in Talent.
- The updated navigation bar now aligns with the Office header.

### Office location update switches the context to the top of the worker list
With the current release, changing the office location will no longer switch the context of the worker that you're viewing when assigning an office location.

### Position assignment end date doesn't display correctly on worker hire and transfer actions
Position assignment end dates now display correctly based on the user preferred time zone when using actions.

### Common Data Service job entity doesn't allow Job type and Job function fields to update
Common Data Service entities now syncronize correctly when updated using the Common Data Service.

## Coming soon

###  Advanced compensation security (fixed and variable)
In many organizations, the compensation and benefits managers might only have access to certain compensation records. These could be for executives or regional employees. With this change, HR can manage and maintain the compensation plans for different employee groups in the organization. You can assign security roles to fixed and variable plans that determine access to the plans and the employee data related to the plans, such as salary or bonus records. Only the roles with the access granted can process compensation for those employees.

###  Email support for alerts
With Platform update 24 for Finance and Operations, users can create alert rules that automatically dispatch email notifications to contacts when triggered by an event.

### Duplicate employee check: Interface changes
With this change, duplicates are detected as you enter name fields, and a status displays how many were found. You can select the provided link to open a new page to evaluate whether to use the detected match. The duplicates form doesn't automatically open, to avoid interrupting data entry.
