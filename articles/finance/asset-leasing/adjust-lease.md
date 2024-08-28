---
title: Adjust leases
description: Learn how to adjust a lease. Adjustment might be required if the lease terms are modified, the lease is extended, or other circumstances change.
author: moaamer
ms.author: moaamer
ms.topic: article
ms.date: 03/18/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2020-10-28
ms.search.form: 
ms.dyn365.ops.version: 10.0.14
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
---

# Adjust leases

[!include [banner](../includes/banner.md)]


The article explains how to adjust a lease. Adjustment might be required if the lease terms are modified, the lease is extended, or other circumstances change. Asset leasing complies with the guidance that Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16) provide about lease modifications. ASC 842-20-15-1 defines a lease modification as any change to the terms and conditions of a contract that causes a change in the scope of, or the consideration for, a lease. Paragraph 39 of IFRS 16 states that a lessee must revalue the lease liability so that it reflects changes to the lease payments.

For organizations that adhere to ASC 842 or IFRS 16, a lease is remeasured to reflect a change in the present value of the future minimum lease payments (PVFMLP). If the PVFMLP increases, the journal entry that is created will be a debit to the right-of-use (ROU) asset account and a credit to the lease liability account for the difference between the new PVFMLP and the previous PVFMLP. If the PVFMLP decreases, the journal entry will be a debit to the lease liability account and a credit to the ROU asset account for the difference.

If the adjustment decreases the ROU asset past 0 (zero), the remainder is credited to the gain on lease modification posting account that is specified on the **Lease posting accounts** page. The system accounts for these transactions and other adjustment entries, such as classification changes, initial direct costs, lease incentives, prepayments, and dismantling costs that arise from lease modifications.

For specific guidance about lease adjustment transactions, we recommend that you see IFRS 16 and ASC 842.

## Lease adjustment wizard

To adjust a lease, complete the following steps. The modified data will update lease schedules after you post from the **Lease adjustment** wizard. You can save your work and close the wizard at any time, and then come back later to resume your work.

To open the **Lease adjustment** wizard from the lease summary, follow these steps.

1. Go to **Asset leasing \> Leases \> Lease summary**. 
2. Select the lease to adjust, and then select **Adjustment wizard**.
3. Follow the prompts in the wizard to enter the required changes.

To open the **Lease adjustment** wizard from the **Lease adjustments** page, for an adjustment that is already in progress, follow these steps.

1.	Go to **Lease \> Leases \> Lease adjustments**.
2.	Select a lease that has an adjustment status of **In progress**, and then select **Adjustment wizard**.
3.	In the **Modification start date** and **Posting date** fields, enter the appropriate dates.
4.	Select **Next**.

    The lease is now added to the **Lease adjustments** page, where you can enter the new information about it.

    After the lease has been adjusted, the right-of-use considerations fields apply to it. If no initial direct costs, lease incentives, prepayments, or dismantling costs are associated with the modified lease, leave the corresponding fields blank. The original amounts won't apply to the updated lease. 

    For example, a lessor provides a $1,000 incentive for agreeing to a lease extension. In this case, when you adjust the lease to account for the extension, enter **1,000** in the **Lease incentives arising from adjustment** field.

    The payment schedule lines now show all payments from the month, and later months, in the **Modification start date** field. Because modifications are prospective, payment schedule lines can't start before the modification starts. To view payment schedule lines from before the modification start date, go to the **Lease version history** page.

8.	Select **Next**.

    The next page shows key details about the expected lease adjustment, such as the carrying values of the lease liability before the modification and the new expected lease liability after the modification. The page also shows a preview of the journal entry for the expected lease adjustment.

9.	Select **Submit to workflow** to submit the lease adjustment to the workflow system if the lease adjustment workflow is active and the adjustment hasn't yet been approved. For more information about how to use the lease adjustment workflow, see [Use lease adjustments workflows](use-create-lease-wrkflw.md).

    > [!NOTE]
    > At this point, the adjustment variables are recalculated to verify that no transactions have been posted against the lease since the adjustment overview and adjustment journal entry were first calculated. If any values change, the adjustment overview grid is updated, and you can review the information before you resubmit the lease adjustments to the workflow system.

10.	If a workflow isn't active, or if the lease adjustment has been approved, select **Finish** to process the changes and post the adjustment journal entry.

    > [!NOTE] 
    > At this point, the adjustment variables are recalculated to verify that no transactions have been posted against the lease since the adjustment overview and adjustment journal entry were first calculated. If any values change, the adjustment overview grid is updated, and you can review the changes before you select **Finish**. If the workflow is active and the lease adjustment has been approved, any changes to the adjustment overview causes the approval status to be set back to **Not submitted**. In this case, you should resubmit the lease adjustment to the workflow system.

    On the **Lease adjustments** page, the adjustment status is now set to **Completed**.

    On the **Lease adjustments** page, you can view the **Adjustment overview** and **Adjustment entry preview** FastTabs. The lease details and date information are shown in the version history of that lease.

    A new lease version and a new set of schedules are now created by using the modified information. 

13.	To view the new schedules, go to the lease, and then select **Books**.
14.	To view the newly generated payment schedule, select **Payment schedule**.
15.	To view the new lease liability amortization schedule that is generated from the new information, close the **Payment schedule** page, and open the **Liability amortization schedule** page.
16.	To view the newly generated asset depreciation schedule, open the **Asset depreciation schedule** page from the **Book details** page.
17.	To view the adjustment journal entry, select **Journals \> Asset leasing journal**.

## Cancel a lease adjustment

To delete a lease adjustment that is in progress, follow these steps.

1.	Go to **Lease \> Leases \> Lease adjustments**.
2.	Select that in-progress lease adjustment to cancel.
3.	Select **Cancel adjustment**. 
4.	Select **OK**.

    > [!NOTE] 
    > If you select **Cancel** in the **Lease adjustment** wizard, you roll back the most recent change that you completed in the wizard, but you don't remove an adjustment that is in progress.

## Use the lease adjustment workflow

This section explains how to use the lease adjustment workflow. The lease adjustment workflow helps you manage lease adjustments in a consistent manner by providing a set of approval steps and assigning them to specific users who approve a lease adjustment before it becomes final. After the lease adjustment is approved in the workflow, you can use the **Lease adjustment** wizard to complete the lease adjustment.

1.	To submit a lease adjustment for approval, go to **Lease \> Leases \> Lease adjustments**.
2.	Select the lease ID of the lease adjustment, and then select **Adjustment wizard**.
3.	On the last page of the wizard, select **Submit for approval**.
4.	Enter a comment about the adjustment, and then select **OK**.

    The workflow status is changed to **Pending approval**, and all the fields in the wizard are locked for editing.

5.	To approve the lease adjustment, go to **Lease \> Leases \> Lease adjustments**.
6.	Select the lease ID of the lease adjustment, and review the **Adjustment overview** and **Adjustment entry preview** FastTabs.
7.	Select **Workflow \> Approved**.

    On the **Lease adjustments** page, the workflow status is now set to **Approved**. At this point, the lease adjustment is ready to be posted through the adjustment journal entry.

8.	To continue to process the lease adjustment and post the adjustment entry, go to **Lease \> Leases \> Lease adjustments**.
9.	Select the lease ID of the lease adjustment, and then select **Adjustment wizard**.
10.	Select **Next** until you reach the last page of the wizard, and then select **Finish**.

The carrying values of the lease are recalculated to ensure that the adjustment variables that were approved are current. If there are any changes, the approval status is set to **Draft**, and you should resubmit the lease adjustment to the workflow system.

## View lease versions

If a lease has been adjusted, you can view the different versions of it. You can also view the historical schedules and past lease details.

1. On the **Lease summary** page, select the lease, and then, on the Action Pane, select **Lease version history**.

    If the selected lease has been adjusted, the **Lease version history** page shows the different versions. The original lease is labeled **1**, and subsequent versions have ascending numerical order.

    For a selected lease version, you can view the financial dimensions, contract details, location, and payment schedule lines.

2. To view historical schedules, open the modified lease from the **Lease summary** page, select the desired book, and then, on the Action Pane, select **Book version history**.
3. On the **Book version** page, select a version and a schedule to view.

## Adjust a lease book

Follow these steps to adjust a lease book only.

1. Go to **Asset leasing** \> **Leases** \> **Lease summary**.
2. Select and open a lease.
3. On the **Lease details** page, select **Books**.
4. On the **Books details** page, on the Action Pane, in the **Maintain** group, select **Adjust book**. 
5. Remove the payment schedule lines.
6. In the **Lease modification date** field, enter the modification date. Then consider removing all additional asset/liability considerations (initial direct cost, lease incentive, lease prepayment, dismantling cost, and residual value guarantee), if there are any. 
7. To help prevent inaccurate calculations for the lease adjustment, add new payment schedule lines for the new payment dates that match the modification date. 

> [!NOTE] 
> We recommend that you use the **Lease adjustment** wizard to adjust a lease. The wizard reduces the number of manual steps, provides a preview of balances after the adjustment, and lets you change amounts before posting.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
