---
# required metadata

title: What's new or changed in Dynamics 365 Talent - Core HR (January 23, 2019)
description: This topic describes features that are either new or changed in Microsoft Dynamics 365 Talent - Core HR.
author: Darinkramer
manager: AnnBe
ms.date: 01/23/2019
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
ms.search.validFrom: 2019-01-23
ms.dyn365.ops.version: Talent

---
# What's new or changed in Dynamics 365 Talent - Core HR (January 23, 2019)

**Build 8.1.2121**

This topic describes features that are either new or changed in Core HR.

## Changes

### Import of employee fixed compensation not working when creating new fixed compensation records
A change has been made to the employee fixed compensation entity to retrieve the compensation level upon import. Prior to this release, a message was displayed indicating that the level was required.

### Remove the minimum balance field from the time off request dialog box
The **Minimum balance** field has been removed from the **Time off request** dialog box. This change affects all areas where time off can be requested.

### Data upgrade for compensation levels not updating in all scenarios
A change has been made to update the compensation level on fixed compensation plans. This change will populate the compensation level on fixed plans for the job assigned to the employee.

### Payroll information in the Manage changes page is only available when logged in as System Administrator
This change allows employees with the Payroll Administrator role access to the payroll information on the **Changes timeline > Manage changes** page for the position.

### Job fields default to positions
When changing the job on a position, job fields will default to the position. An alert message will appear giving an option to accept the default values or keep the existing values for those fields.

### Probation period and calendar are not displayed for future hired employees.
With this change, **Probation period** and **Calendar** fields have been added to the **Manage changes** page to allow for data entry for future and past employees.

### Platform update 23 for Finance and Operations
Minor bug fixes have been included as part of Platform update 23 for Finance and Operations. For more information, see [What's new or changed in Dynamics 365 Finance and Operations platform update 23 (January 2019)](https://docs.microsoft.com/dynamics365/unified-operations/fin-and-ops/get-started/whats-new-platform-update-23). 
