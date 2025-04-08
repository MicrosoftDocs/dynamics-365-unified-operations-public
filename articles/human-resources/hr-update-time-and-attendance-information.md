---
title: Update time and attendance information in Dynamics 365 Human Resources
description: Learn about how to update time and attendance information in Dynamics 365 Human Resources, including adjusting registrations and deactivating past workers.
author: twheeloc
ms.author: twheeloc
ms.date: 01/24/2024
ms.topic: article
f1_keywords:
- indirect activities
- indirect activities costs
audience: Application User
ms.search.region: Global
---

# Update time and attendance information in Dynamics 365 Human Resources

There are various ways in which you can update time and attendance information for your workers.

This article discusses how to post indirect activities costs, how to adjust flex time, how to adjust registrations with future timestamps, unit count, and statistical payroll balances, how to clean up old time and attendance registrations, and how to deactivate past workers.

## Post indirect activities cost

Indirect activities costs can be posted periodically to update all costs that are related to indirect activities registrations found in **General ledger**.

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Update** \> **Post indirect activities costs**.
2. Select the **Transactions for dimensions** checkbox to generate a ledger journal line for each combination of financial dimensions and ledger accounts.
3. Select the date for the transaction in the **Transaction date** field.
4. In the **From date** and **To date** fields, select the period for which you want to post indirect activities costs.
5. Select the **Repost** checkbox only if you want to generate new ledger journal lines for transactions that have already been posted.

> [!NOTE]
> You can also post indirect activities by using a batch job. Submit a batch processing job from a page.

## Adjust flex time, unit count, and statistical payroll balances

Depending on which types of registrations workers are allowed to make, different types of balances can be generated, for example, flexible hours, or payroll statistics. You can recalculate the balances and, in some cases, make adjustments or set up an opening balance.

### Flexible hours

For workers who work flexible hours, it may be necessary to adjust the flexible hours balance. When you set up time and attendance registrations for workers, it is often relevant to enter an opening flex balance, if flexible hours are transferred from a previously used system.

### Specify an opening flex balance for a worker

1. Click **Human resources** \> **Common** \> **Workers** \> **Time registration workers**.
2. Select a worker.
3. On the **Action Pane**, click the **Time registration** tab.
4. In the **Setup** group, click **Set up time registration worker** and select **Opening flex balance**.
5. In the **Opening flex balance** field, enter the number of flex hours to be added to the opening balance.

> [!TIP]
> To recalculate the worker balance, select the **Recalculate flex balance** checkbox before you click **OK**.

### Specify an opening flex balance for multiple workers

You can recalculate balances for several workers at the same time.

1. Click **Set up time registration worker** and select **Recalculate worker balances**.
2. In the **Recalculate worker balances** dialog box, click the **Select**.
3. In the **Inquiry** page, on the **Range** tab, click the **Add** button to create a line.
4. In the **Field** field, select **Worker**.
5. In the **Criteria** field, select the record ID for each worker.
6. Repeat steps three through five for each worker.

### Adjust a flex balance

1. Click **Human resources** \> **Common** \> **Workers** \> **Time registration workers**.
2. Select a worker.
3. On the **Action Pane**, click the **Time registration** tab.
4. In the **Setup** group, click **Set up time registration worker** and select **Flex balance**.
5. Select the flex registration to correct.
6. Click **Flex correction**.
7. Press **CTRL+N** to create a new correction line.
8. Enter a description of the flex correction in the **Description** field.
9. Enter the number of flex hours to be adjusted in the **Flex correction** field.

> [!NOTE]
> To make corrections to a worker's pay, in addition to the flex balance, you can select a pay type in the **Pay type** field and insert the number of paid hours to be adjusted in the **Pay units** field.

### Recalculate a flex balance

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Flex** \> **Recalculate flex balance**.
2. Click **Select**.
3. Select the workers to recalculate flex balances for and then click **OK**.

### Statistical payroll balances

Statistical payroll balances can be adjusted and recalculated.

> [!NOTE]
> A payroll record must exist for the date that you make the adjustment for.

### Adjust statistical payroll balances for several workers

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Payroll** \> **Adjust payroll statistics**.
2. Select the group to adjust in the **Payroll statistics group** field.
3. In the **Pay type** field, select the pay type to be adjusted.
4. In the **Date** field, select the date when to make the adjustment.
5. In the **Adjustment type** field, select how to make the adjustment:
    
      - **Opening balance** – Adjust the opening balance to be the value that you insert in the **Value** field.    
      - **Balance** – Adjust the current balance for the selected **Pay type** to be the value that you insert in the **Value** field.    
      - **Adjustment** – Adjust the payroll record on the selected date with value that you insert in the **Value**. For example, if you insert the number 2 in the **Value** field, you will add two hours to the payroll balances of all the workers included in the selected payroll statistics group.

6. In the **Value** field, insert the number of hours to be adjusted, according to the adjustment method selected in the **Adjustment type** field.

### Adjust the statistical payroll balance for a specific worker

1. Click **Human resources** \> **Common** \> **Workers** \> **Time registration workers**.
2. Select a worker, and then click the **Time registration** tab.
3. In the **Payroll statistics** group, click **Payroll statistics**.
4. Select the balance to adjust.
5. Click **Set adjustment**.
6. Insert the value to use to adjust the balance in the **Adjustment** field. For example, if you insert the number 2 in the field, you will add two hours to the payroll balance of the worker.

### Recalculate statistical payroll balances

You can recalculate statistical payroll balances for a group of workers.

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Payroll** \> **Recalculate payroll statistics**.
2. Select a **Payroll statistics group**, a **Pay type**, and, if necessary, a **Period code** (which is the pay period), to be recalculated.

### Recalculate the count unit balance for a worker

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Payroll** \> **Recalculate worker balances**.
2. Select a worker to recalculate count unit balances for.

> [!NOTE]
> After you have recalculated a count unit balance for a worker, you can see that the balance was updated. Click **Human resources** &gt; **Common** &gt; **Workers** &gt; **Time registration workers**. Double-click the worker. On the **Action Pane**, click the **Time registration** tab. In the **Worker balances** group, click **Worker balances**.

## About registrations with future timestamps

When workers clock in and clock out, the registration table is checked for the most recent clock-in or clock-out registration. If the most recent registration is a clock-out, the application clocks in the worker. If the most recent registration is a clock-in, the application clocks out the worker.

When registrations are calculated, a supervisor or team leader may mistakenly create a clock-in or clock-out registration that has a future timestamp. This is accomplished by using the missing clock-out feature.

### Example

On a Tuesday, a supervisor mistakenly registers a clock-out time for Wednesday at 16:00 for a worker by using the **Missing clock-out** function. When the worker clocks in Wednesday morning at 08:00, he or she receives a clock-in message, which is correct. However, when the worker attempts to clock out at 16:05, the registration is acknowledged as a clock-in, because the worker already has a clock-out registration for Wednesday at 16:00.

To prevent the problems that these types of registrations can cause, you can remove faulty registrations that contain future timestamps from the registration table.

### Remove registrations that have timestamps set for the future

1. Click **Production control** \> **Periodic** \> **Clean up** \> **Archive future registrations**.
    
    _or_
    
    Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Update** \> **Archive future registrations**.

2. Click **OK**.

> [!NOTE]
> You can set up this task to run regularly as a batch job, such as one time every 24 hours. Submit a batch processing job from a page.

## Clean up old time and attendance registrations

Registrations can accumulate over time, and can reduce the performance of the application. Therefore, we recommend that you clean up old registrations periodically.

You can remove old registrations in the following ways:

  - You can delete them.
  - You can export them to a file.
  - You can transfer them to an archive table.

> [!IMPORTANT]
> The clean-up function does not delete data that is not processed. Make sure that you do not delete registrations that may be required later for documentation purposes.

### Clean up registrations

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Update** \> **Clean up registrations**.
    
    _or_
    
    Click **Production control** \> **Periodic** \> **Clean up** \> **Clean up registrations**.
    
    _or_
    
    Click **Production control** \> **Inquiries** \> **Registrations** \> **Raw registrations archive**. On the toolbar, click **Clean up registrations**.

2. In the **Cleanup mode** field, select how you want to handle the old registrations:
    
      - Select **To table** to move the registrations to another table. The registrations are transferred to the **Raw registrations archive** page.    
      - Select **To file** to move the registrations to an external file.    
      - Select **Delete** to permanently delete the registrations.

3. In the **Maximum age** field, enter the maximum age, in days, of registrations that are kept in the raw registrations table. For example, if you enter the number 20, all registrations that are more than 20 days old are archived according to your selection in the **Cleanup mode** field.
4. If you select **To file** in the **Cleanup mode** field, enter a file name, or select an existing file, in the **File name** field.

### View archived registrations for a worker

If you have transferred registrations to an archive table, you are still able to view them.

1. Click **Production control** \> **Inquiries** \> **Registrations** \> **Raw registrations**.
2. Select the worker, and then click **Archive**.
3. Select the date for which you want to view archived registrations.

> [!TIP]
> To open the **Raw registrations archive** page. Click **Production control** &gt; **Inquiries** &gt; **Registrations** &gt; **Raw registrations archive**.

## Deactivate past workers

This topic describes how to prevent information about workers, who are no longer active, from being included in calculations and approvals for registrations in **Time and attendance**. For example, workers are no longer active after their employment has been terminated.

To deactivate a worker, follow these steps:

1. Click **Human resources** \> **Periodic** \> **Time and attendance** \> **Update** \> **Deactivate past workers**.
2. _Optional_: Enter settings for the batch job.
3. Click **OK**.

## See also

[Time and attendance information in Dynamics 365 Human Resources](hr-about-time-and-attendance-information.md)

[Set up time and attendance information in Dynamics 365 Human Resources](hr-set-up-time-and-attendance-information.md)
