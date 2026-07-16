---
title: Update time and attendance information in Dynamics 365 Human Resources
description: Learn about how to update time and attendance information in Dynamics 365 Human Resources, including adjusting registrations and deactivating past workers.
author: twheeloc
ms.author: twheeloc
ms.date: 06/12/2026
ms.topic: how-to
f1_keywords:
- indirect activities
- indirect activities costs
audience: Application User
ms.search.region: Global
---

# Update time and attendance information in Dynamics 365 Human Resources

You can update time and attendance information for your workers in various ways.

This article discusses how to post indirect activities costs, adjust flex time, adjust registrations with future timestamps, unit count, and statistical payroll balances, clean up old time and attendance registrations, and deactivate past workers.

## Post indirect activities cost

Indirect activities costs can be posted periodically to update all costs that are related to indirect activities registrations found in **General ledger**.

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Update** > **Post indirect activities costs**.
1. Select the **Transactions for dimensions** checkbox to generate a ledger journal line for each combination of financial dimensions and ledger accounts.
1. Select the date for the transaction in the **Transaction date** field.
1. In the **From date** and **To date** fields, select the period for which you want to post indirect activities costs.
1. Select the **Repost** checkbox only if you want to generate new ledger journal lines for transactions that are already posted.

> [!NOTE]
> You can also post indirect activities by using a batch job. Submit a batch processing job from a page.

## Adjust flex time, unit count, and statistical payroll balances

Depending on which types of registrations workers are allowed to make, different types of balances can be generated, for example, flexible hours, or payroll statistics. You can recalculate the balances and, in some cases, make adjustments or set up an opening balance.

### Flexible hours

For workers who work flexible hours, it may be necessary to adjust the flexible hours balance. When you set up time and attendance registrations for workers, it's often relevant to enter an opening flex balance, if flexible hours are transferred from a previously used system.

### Specify an opening flex balance for a worker

1. Select **Human resources** > **Common** > **Workers** > **Time registration workers**.
1. Select a worker.
1. On the **Action Pane**, select the **Time registration** tab.
1. In the **Setup** group, select **Set up time registration worker**, and then select **Opening flex balance**.
1. In the **Opening flex balance** field, enter the number of flex hours to add to the opening balance.

> [!TIP]
> To recalculate the worker balance, select the **Recalculate flex balance** checkbox before you select **OK**.

### Specify an opening flex balance for multiple workers

You can recalculate balances for several workers at the same time.

1. Select **Set up time registration worker**, and then select **Recalculate worker balances**.
1. In the **Recalculate worker balances** dialog box, select **Select**.
1. In the **Inquiry** page, on the **Range** tab, select the **Add** button to create a line.
1. In the **Field** field, select **Worker**.
1. In the **Criteria** field, select the record ID for each worker.
1. Repeat steps three through five for each worker.

### Adjust a flex balance

1. Select **Human resources** > **Common** > **Workers** > **Time registration workers**.
1. Select a worker.
1. On the **Action Pane**, select the **Time registration** tab.
1. In the **Setup** group, select **Set up time registration worker** and select **Flex balance**.
1. Select the flex registration to correct.
1. Select **Flex correction**.
1. Press **CTRL+N** to create a new correction line.
1. Enter a description of the flex correction in the **Description** field.
1. Enter the number of flex hours to adjust in the **Flex correction** field.

> [!NOTE]
> To make corrections to a worker's pay, in addition to the flex balance, you can select a pay type in the **Pay type** field and insert the number of paid hours to be adjusted in the **Pay units** field.

### Recalculate a flex balance

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Flex** > **Recalculate flex balance**.
1. Select **Select**.
1. Select the workers to recalculate flex balances for, and then select **OK**.

### Statistical payroll balances

Statistical payroll balances can be adjusted and recalculated.

> [!NOTE]
> A payroll record must exist for the date that you make the adjustment for.

### Adjust statistical payroll balances for several workers

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Payroll** > **Adjust payroll statistics**.
1. Select the group to adjust in the **Payroll statistics group** field.
1. In the **Pay type** field, select the pay type to adjust.
1. In the **Date** field, select the date for the adjustment.
1. In the **Adjustment type** field, select how to make the adjustment:

      - **Opening balance** – Adjust the opening balance to be the value that you enter in the **Value** field.
      - **Balance** – Adjust the current balance for the selected **Pay type** to be the value that you enter in the **Value** field.
      - **Adjustment** – Adjust the payroll record on the selected date with value that you insert in the **Value**. For example, if you insert the number 2 in the **Value** field, you'll add two hours to the payroll balances of all the workers included in the selected payroll statistics group.

1. In the **Value** field, enter the number of hours to adjust, according to the adjustment method selected in the **Adjustment type** field.

### Adjust the statistical payroll balance for a specific worker

1. Select **Human resources** > **Common** > **Workers** > **Time registration workers**.
1. Select a worker, and then select the **Time registration** tab.
1. In the **Payroll statistics** group, select **Payroll statistics**.
1. Select the balance to adjust.
1. Select **Set adjustment**.
1. Enter the value to use to adjust the balance in the **Adjustment** field. For example, if you enter the number 2 in the field, you add two hours to the payroll balance of the worker.

### Recalculate statistical payroll balances

You can recalculate statistical payroll balances for a group of workers.

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Payroll** > **Recalculate payroll statistics**.
1. Select a **Payroll statistics group**, a **Pay type**, and, if necessary, a **Period code** (which is the pay period), to recalculate.

### Recalculate the count unit balance for a worker

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Payroll** > **Recalculate worker balances**.
1. Select a worker to recalculate count unit balances for.

> [!NOTE]
> After you have recalculated a count unit balance for a worker, you can see that the balance was updated. Select **Human resources** &gt; **Common** &gt; **Workers** &gt; **Time registration workers**. Double-click the worker. On the **Action Pane**, select the **Time registration** tab. In the **Worker balances** group, click **Worker balances**.

## About registrations with future timestamps

When workers clock in and clock out, the registration table is checked for the most recent clock-in or clock-out registration. If the most recent registration is a clock-out, the application clocks in the worker. If the most recent registration is a clock-in, the application clocks out the worker.

When registrations are calculated, a supervisor or team leader might mistakenly create a clock-in or clock-out registration that has a future timestamp. This registration is created by using the missing clock-out feature.

### Example

On a Tuesday, a supervisor mistakenly registers a clock-out time for Wednesday at 16:00 for a worker by using the **Missing clock-out** function. When the worker clocks in Wednesday morning at 08:00, they receive a clock-in message, which is correct. However, when the worker attempts to clock out at 16:05, the registration is acknowledged as a clock-in, because the worker already has a clock-out registration for Wednesday at 16:00.

To prevent the problems that these types of registrations can cause, remove faulty registrations that contain future timestamps from the registration table.

### Remove registrations with timestamps set in the future

1. Select **Production control** > **Periodic** > **Clean up** > **Archive future registrations**.

    _or_

    Select **Human resources** > **Periodic** > **Time and attendance** > **Update** > **Archive future registrations**.

1. Select **OK**.

> [!NOTE]
> Set up this task to run regularly as a batch job, such as one time every 24 hours. Submit a batch processing job from a page.

## Clean up old time and attendance registrations

Registrations can accumulate over time, and can reduce the performance of the application. Therefore, we recommend that you clean up old registrations periodically.

Remove old registrations in the following ways:

- Delete them.
- Export them to a file.
- Transfer them to an archive table.

> [!IMPORTANT]
> The clean-up function doesn't delete data that isn't processed. Make sure that you don't delete registrations that might be required later for documentation purposes.

### Clean up registrations

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Update** > **Clean up registrations**.

    _or_

    Select **Production control** > **Periodic** > **Clean up** > **Clean up registrations**.

    _or_

    Select **Production control** > **Inquiries** > **Registrations** > **Raw registrations archive**. On the toolbar, select **Clean up registrations**.

1. In the **Cleanup mode** field, select how you want to handle the old registrations:

      - Select **To table** to move the registrations to another table. The registrations are transferred to the **Raw registrations archive** page.
      - Select **To file** to move the registrations to an external file.
      - Select **Delete** to permanently delete the registrations.

1. In the **Maximum age** field, enter the maximum age, in days, of registrations that stay in the raw registrations table. For example, if you enter the number 20, all registrations that are more than 20 days old are archived according to your selection in the **Cleanup mode** field.
1. If you select **To file** in the **Cleanup mode** field, enter a file name, or select an existing file, in the **File name** field.

### View archived registrations for a worker

If you transfer registrations to an archive table, you can still view them.

1. Select **Production control** > **Inquiries** > **Registrations** > **Raw registrations**.
1. Select the worker, and then select **Archive**.
1. Select the date for which you want to view archived registrations.

> [!TIP]
> To open the **Raw registrations archive** page, select **Production control** &gt; **Inquiries** &gt; **Registrations** &gt; **Raw registrations archive**.

## Deactivate past workers

This article describes how to prevent information about workers who are no longer active from being included in calculations and approvals for registrations in **Time and attendance**. For example, workers are no longer active after their employment is terminated.

To deactivate a worker, follow these steps:

1. Select **Human resources** > **Periodic** > **Time and attendance** > **Update** > **Deactivate past workers**.
1. _Optional_: Enter settings for the batch job.
1. Select **OK**.

## See also

[Time and attendance information in Dynamics 365 Human Resources](hr-about-time-and-attendance-information.md)

[Set up time and attendance information in Dynamics 365 Human Resources](hr-set-up-time-and-attendance-information.md)
