---
# required metadata

title: Suspend leave
description: You can suspend leave for an employee in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 10/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SuspendLeave, LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: Human Resources

---

# Suspend leave

>[!Important]
>The functionality noted in this topic is currently available for customers on the stand-alone Dynamics 365 Human Resources. Some or all of the functionality will be available as part of a future release on the Finance infrastructure after Finance release 10.0.26.


[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can suspend leave for an employee to stop leave accruals from being processed for selected leave types. 

## Suspend leave and absence for an employee

1. On the employee's record, select **Leave**.

2. Select **Suspend leave**.

3. Select **New**.

4. In the **Suspend leave accrual** dialog box, select the **Leave type** along with the **Start date** and **End date** for the suspension.

5. Optionally, you can add a **Comment** for the suspension. 

If accruals are processed while the employee's leave is suspended, no accrual will be made for the suspended leave types.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Configure leave and absence types](hr-leave-and-absence-types.md)
- [Accrue leave and absence plans](hr-leave-and-absence-accrue.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
