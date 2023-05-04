---
# required metadata

title: Configure leave and absence types
description: Set up types of leave that employees can take in Dynamics 365 Human Resources.
author: twheeloc
ms.date: 02/16/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LeavePlanFormPart, LeaveAbsenceWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

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

[!include [preview banner](../includes/preview-banner.md)]

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

1. On the **Leave and absence** workspace, select the **Links** tab.
2. Under **Setup**, select **Leave and absence types**.
3. Select **New**.
4. Enter a name for the leave type under **Type**, enter a description under **Description**, and select a workflow in the **Workflow ID** field. Based on the leave type, select a request type in the **Request type** field. For example, select **Time off** or **Leave of absence**.
5. In **General**, select **None**, **Scheduled**, or **Unscheduled** from the **Category** dropdown.
6. Select an earning code from the **Earning code** dropdown.
7. Under **Reason code required**, select whether you want to require a reason code. If you want to require reason codes, you might have to add them. Under **Reason codes**, select **Add**, select a reason code, and then select the **Enabled** checkbox next to it.
8. If the request type is **Leave of absence**, follow these steps:

    1. Under **Open ended**, select whether users should be able to create open-ended leaves.
    2. If **Open ended** is enabled, you can select whether workers must submit a return-to-work notice when they return from a leave of absence.
    3. If workers must submit a return-to-work notice, you can enable **Enable return to work notice**. If **Enable return to work notice** is enabled, **Attachment required** is automatically enabled and can't be disabled.

9. If users should upload documents when they create or update leave requests, you can enable **Attachment required**.
10. Under **Restrict access to selected roles**, select whether you want to restrict access. Then, under **Security roles for this leave type**, select the security roles. The security roles are defined in the workflow that you selected under **Workflow ID** earlier in this procedure.
11. Under **Calendar color**, select the color to show on leave and absence calendars for this leave type.
11. Under **Suspension relations**, select whether this leave type should either suspend another leave type or be suspended by another leave type. When a leave of absence request is submitted for the suspending leave type, a leave suspension will automatically be created for the suspended leave type.
12. Select **Save**.

## Configure leave type rules

1. Set rounding options for the **Leave and absence** type. Options include **None**, **Up**, **Down**, and **Nearest**. You can also set rounding precision for the leave type.
2. Set **Holiday correction** for the leave type. When you select this option, the number of holidays that fall on a work day will be used to determine how to accrue time off for the leave type. For example, if Christmas Day falls on a Monday, Human Resources will subtract one day from the leave type when processing accruals.

    You set holidays in the working time calendar. For more information, see [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md).

3. Set **Carry-forward leave type** for the leave type. When you select this option, any carry-forward balances will be transferred to the specified leave type. The carry-forward leave type also needs to be included in the leave and absence plan.
4. Define **Expiration rules** for the leave type. When you configure this option, you can choose the unit of days or months and set the duration for the expiration. The effective date of the expiration rule is used to determine when to start running the batch job that processes the leave expiration, or the date when the rule takes effect. The expiration itself will always occur on the accrual period start date. For example, if the accrual period start date is August 3, 2021, and the expiration rule was set at 6 months, the rule will be processed based on the expiration offset from the accrual period start date, so it would be executed on February 3, 2022. Any leave balances that exist at the time of expiry will be subtracted from the leave type and will be reflected in the leave balance.

## Configure the required attachment per leave type

> [!NOTE]
> To use the **Attachment required** field, you must first turn on the **Configure required attachment for leave requests** feature in Feature management. For more information about how to turn on features, see [Manage features](hr-admin-manage-features.md).

1. On the **Leave and absence** page, on the **Links** tab, under **Setup**, select **Leave and absence types**.
2. Select a **Leave and absence type** in the list. In the **General** section, use the **Attachment required** field to specify whether an attachment must be uploaded when an employee submits a new leave request for the selected leave type. 
3. If the **Attachment required** is selected based on the **Request type**, three additional fields will appear to provide flexibility in attachment requirements:

    - **On creating a leave request** – Requires users to upload an attachment when creating a leave request.
    - **On updating leave request** – Requires users to upload an attachment when updating a leave request.
    - **On cancelling leave request** – Requires users to upload an attachment when cancelling a leave request.

    > [!NOTE] 
    > The fields mentioned above are available after Dynamics 365 Human Resources release 10.0.32.

4. If the **Request type** is **Time off**, the **Attachment required** field will have two options: 

    - **On creating leave request** 
    - **On updating leave request**

    > [!NOTE]
    > For time off requests, attachments can't be required for cancellation. For more information on cancelling time off requests, see Cancel time off requests.

5. If the **Request type** is **Leave of absence**, there will be three options: 

    - **On creating leave request**
    - **On updating leave request**
    - **On cancelling leave request** 

6. If attachments are required when updating a time off leave request, and the **Update time off** option selected: If the **Amount** is 0, then an attachment must be uploaded. If an attachment is not required in this case, use **Cancel time off**.

Employees will be required to upload an attachment when they submit a new leave request that has a leave type where the **Attachment required** field is enabled and based on the field values above. To view the attachment that was uploaded as part of a leave request, leave request approvers can use the **Attachments** option for the work items that are assigned to them. If a leave request is accessed by using the Human Resources app in Microsoft Teams, the **View details** option for the leave request can be used to view its details and any attachments.

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

Employees who submit a new leave request can select different leave types to construct their leave request. However, all leave types that are selected as part of a single leave request should have the same leave unit. Employees can view the leave unit for each leave type on the **Request time off** page.

### Hide leave balances

> [!NOTE]
> The **Hide leave balance** option is available in the preview of the 10.0.32 release. To use it, you must enable the **Hide leave balances** feature in Feature management. For more information about how to turn on features, see [Manage features](hr-admin-manage-features.md).

By default, leave balances are shown for leave types. However, organizations might want the leave balance for specific leave types to be hidden from workers. In this case, they can use the **Hide leave balance** option to hide leave balances. Other details, such as the leave grant and accrual details, are also hidden for a specific leave type.

To hide the leave balance for a leave type, follow these steps.

1. On the **Leave and absence** page, on the **Links** tab, under **Setup**, select **Leave and absence types**.
2. Select a leave and absence type in the list.
3. In the **General** section, select **Hide leave balance**.

After the **Hide leave balance** option is enabled for a leave type, employees of the organization won't be able to see the leave balance for that leave type. Instead, they'll see a dash (-). However, HR admins, managers, and absence managers will be able to see the leave balance of their employees.

> [!IMPORTANT]
> When the **Hide leave balance** option is enabled, the value of the **BalanceAvailable** and **TotalThisYear** fields in the **EssLeaveBalanceEntity** entity is set to **0** (zero) for integrations and is represented by a dash (-) in the user interface (UI).

### Include weekends and holidays

> [!NOTE]
> The **Include weekends and holidays** feature is available in the Dynamics 365 Human Resources 10.0.32 release. To use it, you must enable the **Configure leave units per leave type** and **Inclusion of weekends and holidays for leave and absence** features in Feature management. For more information about how to turn on features, see [Manage features](hr-admin-manage-features.md).

Leave types have closed days that are excluded. In other words, weekends and holidays aren't included in calculations of leave request amounts. However, organizations might want to include weekends and holidays for specific leave types. The **Include weekends and holidays** option helps organization distinguish whether calendar days or working days must be considered for specific leave types.

To include weekends and holidays for a leave type, follow these steps.

1. On the **Leave and absence** page, on the **Links** tab, under **Setup**, select **Leave and absence types**.
2. Select a leave and absence type in the list.
3. In the **General** section, select **Include weekends and holidays**.

> [!NOTE]
> If the unit of the leave type is set to **Hours**, after the **Include weekends and holidays** option is enabled, an additional field named **Standard closed day in hours** becomes available. You can use this field to define the total number of hours that make up a closed day. The value should be more than 0 (zero) and less than 24.

After the **Include weekends and holidays** option is enabled for a leave type, when employees of the organization request that leave type, all the closed days are also included in the amount calculation. Therefore, the total amount of leave that's requested equals the total number of calendar days, not the number of actual working days. For example, a worker of an organization requests a specific leave type between January 2, 2023, and January 10, 2023. If the **Include weekends and holidays** option is enabled, the total leave that's requested is nine calendar days. However, if the **Include weekends and holidays** option is disabled, the total leave that's requested is seven working days.

> [!NOTE]
> If leave requests that include closed days are created while the **Include weekends and holidays** option is enabled, they can be canceled only if the option is enabled. The closed days can't be canceled if the option is disabled.

## See also

- [Leave and absence overview](hr-leave-and-absence-overview.md)
- [Create a leave and absence plan](hr-leave-and-absence-plans.md)
- [Create a working time calendar](hr-leave-and-absence-working-time-calendar.md)
- [Suspend leave](hr-leave-and-absence-suspend-leave.md)
- [Create a buy and sell leave request workflow](hr-leave-and-absence-buy-sell-workflow.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
