---
# required metadata

title: What's new or changed in Dynamics 365 for Talent Core HR (January 23, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 for Talent Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 1/23/2019
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
ms.search.validFrom: 2019-01-23
ms.dyn365.ops.version: Talent

---
# "What's new or changed in Dynamics 365 for Talent Core HR (January 23, 2019)"

[!include [banner](includes/banner.md)]

**Build 8.1.2121**

This topic describes features that are either new or changed in Core HR.

## Changes

### Import of Employee fixed compensation not working when creating new fixed compensation records
A change has been made to the employee fixed compensation entity to retrieve the compensation level upon import. Prior to this release a message was displayed indicating the level was required.

### Remove the minimum balance field from the time off request dialog
The minimum balance field has been removed from the time off request dialog. This change will affects all areas where time off can be requested.

### Data upgrade for Compensation Levels not updating in all scenarios
A change has been made to update the compensation level on fixed compensation plans. This change will populate the compensation level on fixed plans for the job assigned to the employee.

### Payroll information in the Manage Changes form is only available when logged in as System Administrator
This change allows employees with the Payroll Administrator role access to the payroll information on the Changes Timeline > Manage Changes form of the position.

### Job fields defaulting to positions
When changing the Job on a position, job fields will default to the position. An alert message will appear giving an option to accept the default values or keep the existing values for those fields.

### Probation period and Calendar are not displayed for future hired employees.
With this change, Probation period and Calendar fields have been added to the Manage changes forms allowing for data entry for future and past employees.

### Platform update 23
Minor bug fixes have been included as part of Platform update 23. For more information on Platform update 23 view the article [located here]https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-23). 


