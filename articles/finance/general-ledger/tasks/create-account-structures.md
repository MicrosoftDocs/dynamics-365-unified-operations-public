---
title: Creating, activating, and deleting account structures
description: Learn how to create, activate, and delete account structures, including step-by-step procedures and guidance on resolving blocking transactions.
author: aprilolson
ms.author: aolson
ms.topic: how-to
ms.date: 09/05/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: DimensionConfigureAccountStructure, DimensionCreateAccountStructure, DimensionHierarchyAddLevel, DimensionHierarchyConstraintActivate
ms.dyn365.ops.version: Version 7.0.0
---

# Creating, modifying, and deleting account structures

[!include [banner](../../includes/banner.md)]

This article walks through the process of creating, activating, and deleting account structures. The steps use the USMF demo data company.

## Creating account structures

1. Go to **General ledger > Chart of accounts > Structures > Configure account structures**.
2. On the **Action pane**, click **New** to open the drop dialog.
3. In the **Account structure** field, enter a name to describe the purpose of the account structure.
4. In the **Description** field, enter a description to specify the purpose of the account structure.
5. Click **Create**.
6. In the **Segments and allowed values**, click **Add segment**.
7. In the dimensions list, select the dimension to add to the account structure.
8. At the end of the list, click **Add segment**.
9. Repeat step 6 to 9 as needed.
10. In the **Allowed value details** section, select the segment to edit the allowed values.
    For example, click the **Main Account** field.
11. In the **Operator** field, select an option, such as is between and includes.
12. In the **Value** field, type a value. For example, 600000.
13. In the **through** field, type a value. For example, 699999.
14. In the **Allowed value details** section, click **Apply**.
15. Repeat step 10 to 15 as needed.
16. In the **Allowed value details** section, click **Add new criteria**.
17. In the **Operator** field, select an option, such as is between and includes.
18. In the **Value** field, type a value. For example, 033.
19. In the **through** field, type a value. For example, 034.
20. Click **Apply**.
21. In the grid, select the segment to edit the allowed values. For example, Cost Center.
22. In the **CostCenter** field, type a value. For example, 007..021.
23. In the **Segments and allowed values**, click **Add**.
24. In the **MainAccount** field, type a value. For example, 600000..699999
25. In the grid, select the segment to edit the allowed values. For example, Department.
26. In the **Department** field, type a value. For example, 032.
27. In the **CostCenter** field, type a value. For example, 086.
28. On the **Action pane**, click **Validate**.
29. On the **Action pane**, click **Activate**.
30. Click **Activate**.

## Activating account structures

When you're satisfied with your new setup or a change to an account structure, you must activate it before it takes effect. During activation, the system validates the structure and then synchronizes all unposted transactions to match the new structure. Posted transactions aren't affected by account structure changes.

> [!NOTE]
> Account structure activation is not the same as dimension activation. Account structure activation synchronizes unposted transactions to match your updated structure and runs as a batch job during normal operations. It can't be performed in maintenance mode.

The activation process runs as a batch job. Depending on the volume of unposted transactions, activation can take anywhere from a few seconds to several hours. While activation is running, the structure is marked as **Activating** on the **Account structures** page.

> [!IMPORTANT]
> Don't cancel a running activation. Canceling resets the process, and resubmitting starts the work over from the beginning — it doesn't resume from where it left off.

### Monitoring activation status

As of application version 10.0.31, the **Account structure activation performance enhancement** feature lets you activate account structures more quickly by running multiple transaction updates at the same time. After the structure itself is validated, it's marked as active while unposted transaction processing continues in the background.

To monitor activation progress:

1. On the **Account structures** page, select **View activation status** above the grid, or select **View** on the Action Pane and then **Activation status**.
2. A dialog box appears showing the individual tasks running as part of the activation process, along with each task's status and completion time.

For more information, see [Account structure activation performance enhancement](../account-structure-improvement.md).

### Account structure activation failure

If an activation fails, the structure reverts to **Draft** status. The error is typically not displayed on the account structure form itself — check the **batch job error log** for the specific error message.

The most common reasons for activation failure are overlapping criteria, either within the structure or across other structures on the same ledger. For more information, see [Account structures overview](../configure-account-structures.md).

## Modifying an existing account structure

In many cases, modifying an existing account structure is preferable to deleting it and creating a new one. Modification avoids the overhead of reassigning the structure across legal entities and reconfiguring dependent processes.

Modification is suitable for scenarios such as:

- **Broadening a range** — For example, changing from 1000-2000 to 1000-3000.
- **Restricting a range** — For example, specifying a **Department** segment range of 012-014.
- **Subdividing a main account range** — For example, splitting a **BalanceSheet** structure with range 1000-3000 into two structures: **BalanceSheet_Small** with range 1000-2000 and **BalanceSheet_Large** with range 2000-3000.
- **Adding or removing dimensions** — For example, adding a new segment or removing one that is no longer needed.

To modify an account structure:

1. Go to **General ledger** > **Chart of accounts** > **Structures** > **Configure account structures** and select the desired structure.
2. Select **Edit** on the Action Pane. The system creates a draft copy while keeping the original active for ongoing transactions.
3. Make your changes — update criteria, add or remove segments, or adjust ranges as needed.
4. Select **Validate** to check your changes.
5. Select **Activate** to apply your changes and wait for successful activation.

## Deleting account structures

If an account structure is no longer needed and has no blocking unposted transactions, it can be deleted. Before deleting, consider whether [modifying the structure](#modifying-an-existing-account-structure) would better serve your needs.

### Resolving blocking transactions

You can't delete an account structure if unposted transactions reference it. To find and resolve these transactions:

1. Navigate to the journal which has the transactions (e.g. **General ledger** > **Journal entries** > **General journals**).
2. Filter by **Show** > **Not posted**.
3. Select a journal and select **Lines** on the Action Pane to view its transactions.
4. Transactions that reference the account structure can be removed with the **Delete** button or updated to reference a different ledger account or offset account.

### Deleting the structure

After all blocking transactions are resolved:

1. Go to **General ledger** > **Chart of accounts** > **Structures** > **Configure account structures**.
2. Select the account structure you want to delete.
3. Select **Delete** on the Action Pane.

If you can't locate the blocking transactions, contact Microsoft Support for assistance.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
