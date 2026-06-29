---
# required metadata

title: Suspend leave of absence
description: You can suspend a leave of absence for an employee in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 06/11/2026
ms.topic: how-to
# optional metadata

ms.search.form: SuspendLeave, LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-04-01
ms.dyn365.ops.version: Human Resources

---

# Suspend leave

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

You can suspend a leave of absence for an employee to stop accruing leave from being processed for selected leave types.

## Suspend leave and absence for an employee

1. On the employee's record, select **Leave**.
1. Select **Suspend leave**.
1. Select **New**.
1. In the **Suspend leave accrual** dialog box, select the **Leave type** along with the **Start date** and **End date** for the suspension.
1. Optionally, add a **Comment** for the suspension.

If you process accruals while the employee's leave is suspended, no accrual is made for the suspended leave types.

> [!NOTE]
> Leave of absence requests suspend time-off requests, but time-off requests don't suspend leave of absence requests.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Configure leave and absence types](hr-leave-and-absence-types.md)
- [Accrue leave and absence plans](hr-leave-and-absence-accrue.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
