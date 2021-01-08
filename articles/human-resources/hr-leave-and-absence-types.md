---
# required metadata

title: Configure leave and absence types
description: Set up types of leave that employees can take in Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 06/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
# ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure leave and absence types

Leave types in Dynamics 365 Human Resources define the types of absences that employees can report. You can tailor leave types according to the needs of your organization. Examples of leave types include:

- Paid time off (PTO)
- Unpaid leave
- Paid vacation
- Sick leave
- Medical leave
- Family leave
- Short-term disability
- Bereavement leave

## Add a leave type

1. On the **Leave and absence** page, select the **Links** tab.

2. Under **Setup**, select **Leave and absence types**.

3. Select **New**.

4. Enter a name for the leave type under **Type**, select a workflow from **Workflow ID**, and enter a description under **Description**.

5. In **General**, select **None**, **Scheduled**, or **Unscheduled** from the **Category** dropdown.

6. Select an earning code from the **Earning code** dropdown.

7. Under **Reason code required**, choose whether you want to require a reason code. If you want to require reason codes, you might need to add them. Under **Reason codes**, select **Add**, select a reason code, and then select the **Enabled** checkbox next to it.

8. Under **Restrict access to selected roles**, choose whether you want to restrict access. Then select the security roles under **Security roles for this leave type**. The security roles are defined in the workflow you selected under **Workflow ID** earlier in this procedure.

9. Under **Calendar color**, choose what color to display on leave and absence calendars for this leave type. 

10. Under **Suspension relations**, choose if you want to have this leave type either suspend another leave type or be suspended by another leave type. When a leave of absence request is submitted for the suspending leave type, a leave suspension will automatically be created for the suspended leave type. 

10. Select **Save**.

## Configure leave type rules

1. Set rounding options for the leave type. Options include **None**, **Up**, **Down**, and **Nearest**. You can also set rounding precision for the leave type.

2. Set **Holiday correction** for the leave type. When you select this option, Human Resources uses the number of holidays that fall on a work day to determine how to accrue time off for the leave type. For example, if Christmas Day falls on a Monday, Human Resources will subtract one day from the leave type when processing accruals.

   You set holidays in the working time calendar. For more information, see [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md)
   
 3. Set **Carry-forward leave type** for the leave type. When you select this option, any carry-forward balances will be transferred to the specified leave type. The carry-forward leave type also needs to be included in the leave and absence plan. 
 
 4. Define **Expiration rules** for the leave type. When you configure this option, you can choose the unit of days or months and set the duration for the expiry. You can also set the effective date of the expiration rule. Any leave balances that exist at the time of expiry will be subtracted from the leave type and will be reflected in the leave balance. 
 
 
## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave and absence plan](hr-leave-and-absence-plans.md)
- [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md)
- [Suspend leave](hr-leave-and-absence-suspend-leave.md)

