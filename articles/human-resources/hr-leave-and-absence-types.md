---
# required metadata

title: Configure leave and absence types
description: Set up types of leave that employees can take in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 09/09/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
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
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure leave and absence types

> [!Important]
> The functionality noted in this topic is currently available for customers on the stand-alone Dynamics 365 Human Resources. Some or all of the functionality will be available as part of a future release on the Finance infrastructure after Finance release 10.0.26.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

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

2. Set **Holiday correction** for the leave type. When you select this option, the number of holidays that fall on a work day will be used to determine how to accrue time off for the leave type. For example, if Christmas Day falls on a Monday, Human Resources will subtract one day from the leave type when processing accruals.

   You set holidays in the working time calendar. For more information, see [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md).
   
 3. Set **Carry-forward leave type** for the leave type. When you select this option, any carry-forward balances will be transferred to the specified leave type. The carry-forward leave type also needs to be included in the leave and absence plan. 
 
4. Define **Expiration rules** for the leave type. When you configure this option, you can choose the unit of days or months and set the duration for the expiration. The effective date of the expiration rule is used to determine when to start running the batch job that processes the leave expiration, or the date when the rule takes effect. The expiration itself will always occur on the accrual period start date. For example, if the accrual period start date is August 3, 2021, and the expiration rule was set at 6 months, the rule will be processed based on the expiration offset from the accrual period start date, so it would be executed on February 3, 2022. Any leave balances that exist at the time of expiry will be subtracted from the leave type and will be reflected in the leave balance.
 
## Configure the required attachment per leave type

> [!NOTE]
> To use the **Attachment required** field, you must first turn on the **Configure required attachment for leave requests** feature in Feature management. For more information about how to turn on features, see [Manage features](hr-admin-manage-features.md).

1. On the **Leave and absence** page, on the **Links** tab, under **Setup**, select **Leave and absence types**.

2. Select a leave and absence type in the list. Then, in the **General** section, use the **Attachment required** field to specify whether an attachment must be uploaded when an employee submits a new leave request for the selected leave type. 

Employees will be required to upload an attachment when they submit a new leave request that has a leave type where the **Attachment required** field is enabled. To view the attachment that was uploaded as part of a leave request, leave request approvers can use the **Attachments** option for the work items that are assigned to them. If a leave request is accessed by using the Human Resources app in Microsoft Teams, the **View details** option for the leave request can be used to view its details and any attachments.

## Configure leave units (hours/days) per leave type

> [!NOTE]
> To use the leave units per leave type functionality, you must first turn on the **Configure leave units per leave type** feature in Feature management. For more information about how to turn on features, see [Manage features](hr-admin-manage-features.md).

> [!IMPORTANT]
> By default, the leave types in a legal entity use the leave units from the configuration of leave parameters at the legal entity level.
> 
> The leave unit of a leave and absence type can be modified only if there are no leave transactions for that leave type.
> 
> The feature can't be turned off after it has been turned on.

1. On the **Leave and absence** page, on the **Links** tab, under **Setup**, select **Leave and absence types**.

2. Select a leave and absence type in the list. Then, in the **General** section, in the **Unit** field, select the leave unit. You can select **Hours** or **Days**.

3. Optional: If you selected **Hours** in the **Unit** field, you can use the **Enable half day definition** field to specify whether employees can select the first half day or the second half day off if they are requesting a half-day leave.

Employees who submit a new leave request can select different leave types to construct their leave request. However, all leave types that are selected as part of a single leave request should have the same leave unit. Employees can view the leave unit for each leave type in the **Request time off** form.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave and absence plan](hr-leave-and-absence-plans.md)
- [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md)
- [Suspend leave](hr-leave-and-absence-suspend-leave.md)
- [Create a buy and sell leave request workflow](hr-leave-and-absence-buy-sell-workflow.md)



[!INCLUDE[footer-include](../includes/footer-banner.md)]
