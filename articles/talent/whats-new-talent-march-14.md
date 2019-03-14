---
# required metadata

title: What's new or changed in Dynamics 365 for Talent (March 14, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent.
author: Darinkramer
manager: AnnBe
ms.date: 3/14/2019
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
ms.search.validFrom: 2019-03-14
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent (March 14, 2019)"

[!include [banner](includes/banner.md)]

This topic describes features that are either new or changed in Talent.

## Changes in Attract
There are minor bug fixes included with this release.

## Changes in Onboarding
There are minor bug fixes included with this release.

## Changes in Core HR
**Build 8.1.2186**

### Performance management not working in all scenarios when using duplicate security roles
Changes made in this release enable performance management scenarios when using the out of the box or duplicated roles.

### Mass assign checklists to workers
With this change you are now able to select multiple employees and then mass assign one or more checklists to those employees. 

### Platform Update 24
See additional details for Platform 24 [HERE](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-24). With platform 24 a couple significant changes include: Alerts have been enabled in Talent, Updated navigation bar that aligns with the Office header 

### Office location update, jump you to the top of the worker list
With the changes this week, changing the office location won't switch the context of the worker you are viewing when assigning an office location.

### Position assignment end date is not displayed correctly on worker hire and transfer actions
Position assignment end dates are now displayed correctly based on the user preferred time zone when using actions.

### CDS Job entity does not allow Job type and job function fields to be updated from CDS
CDS entities are now syncing correctly when updated via CDS.

## Coming Soon

###  Advanced compensation security (Fixed and Variable)
In many organizations the compensation and benefits managers may only have access to certain compensation records. They may be for Executives or Regional based employees. With this change HR can manage and maintain the compensation plans for different employee populations in the organization. Fixed and Variable plans can be assigned security roles which will determine the access to the plans and the employee data related to the plans. (Salary, Bonus records…) Only the roles with the given access will be able to process compensation for those employees.

###  Email support for alerts
With Platform update 24, users will be able to create Alert Rules that automatically dispatch email notifications to contacts when triggered by an event.

### Duplicate employee check: interface changes
With this change, as name fields are entered duplicates will be determined and a status displayed based on how may, if any, were found. A link will be presented and you will be able to open a new page to view and evaluate if the match should be used or not. The "matches" form will not automatically open which can interrupt data entry.
