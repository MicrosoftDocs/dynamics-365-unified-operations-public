---
# required metadata

title: What's new or changed in Dynamics 365 Talent (April 23, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent.
author: Darinkramer
manager: AnnBe
ms.date: 04/23/2019
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
ms.search.validFrom: 2019-04-23
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent (April 23, 2019)

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes features that are either new or changed in Dynamics 365 Talent.

## Changes in Attract
This release includes minor bug fixes for Dynamics 365 Talent: Attract.

## Changes in Onboard
This release includes minor bug fixes for Dynamics 365 Talent: Onboard.

## Changes in Core HR
Changes described in this section apply to build number 8.1.2253. Numbers in parentheses refer to support numbers in Lifecycle Services (LCS).

### Common Data Service entity support for custom fields
With this week's release, the following entities support custom fields: Compensation level, Benefit option, Skill type, and Compensation region.

### Additional OData entities (302992)
The following entities are now supported within OData: Worker professional experience and Worker education.
   
### Performance journal attachments for managers and employees (308248)
With this release, attachments are now available for both managers and employees when creating and updating performance journal entries.

### Employee rehire flag always available (310047)
The employee rehire option is now available for updating outside of the termination process. 

### Cannot change the name of **My payment method** (308815)
Personalization has been enabled to allow for the **My payment method** label to be changed in Employee self-service.

### Financial dimensions against a Position can't be deleted (293908)
Financial dimensions can now be removed when requesting a change for an existing position and the financial dimensions cross company boundaries. 

### Customer is unable to publish back data into Talent when opening the data from Excel (302955)
This change corrects a publishing issue when using related tables.

## In preview

### Allow reason codes to be specified on leave types
Organizations might need additional information about time-off requests. You can now specify reason codes for leave types and enable employees to select a reason code on their time-off requests.

### Require reason codes for certain leave types on time-off requests
Organizations might require reason codes for specific leave types when employees submit time off. This might be due to company policy or regulatory requirements. You can now specify which leave types require a reason code, and you can require employees to provide a reason code for the leave type on their time-off requests.

### Provide leave and absence transaction list for HR
Tracking employee time off and understanding how time off is calculated not only helps HR answer employee questions, but also ensures accurate time-off awards for employees. HR now has a new view into the transactions (grants, accruals, adjustments, and requests) to see the reasons behind balances.

## Coming soon

### Improvements to the user interface for duplicate employee check
With this change, duplicates are detected as you enter name fields, and a status displays the number of duplicates found. You can select the provided link to open a new page to evaluate whether to use the detected match. To avoid interrupting data entry, the duplicates form doesn't automatically open.
## Known issues

### Email support for alerts
With Platform update 26 for Finance and Operations, users can create alert rules that automatically send email notifications to contacts when triggered by an event.
