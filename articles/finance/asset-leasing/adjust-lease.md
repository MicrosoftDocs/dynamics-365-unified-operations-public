---
# required metadata

title: Adjust leases
description: The topic explains how to adjust a lease. Adjustment might be required if the lease terms are modified, the lease is extended, or other circumstances change.
author: moaamer
manager: Ann Beebe
ms.date: 10/28/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14

---

# Adjust leases

[!include [banner](../includes/banner.md)]

The topic explains how to adjust a lease. Adjustment might be required if the lease terms are modified, the lease is extended, or other circumstances change. Asset leasing complies with the guidance that Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16) provide about lease modifications. ASC 842-20-15-1 defines a lease modification as any change to the terms and conditions of a contract that causes a change in the scope of, or the consideration for, a lease. Paragraph 39 of IFRS 16 states that a lessee must revalue the lease liability so that it reflects changes to the lease payments.

For organizations that adhere to ASC 842 or IFRS 16, a lease is remeasured to reflect a change in the present value of the future minimum lease payments (PVFMLP). If the PVFMLP increases, the journal entry that is created will be a debit to the right-of-use (ROU) asset and a credit to the lease liability for the difference between the new PVFMLP and the previous PVFMLP. If the PVFMLP decreases, the journal entry will be a debit to the lease liability and a credit to the ROU asset for the difference.

If the adjustment decreases the ROU asset past 0 (zero), the remainder will be credited to the gain on lease modification posting account that is specified on the **Lease posting accounts** page. The system accounts for these transactions and other adjustment entries, such as classification changes, initial direct costs, lease incentives, prepayments, and dismantling costs that arise from lease modifications.

For specific guidance about lease adjustment transactions, we recommend that you see IFRS 16 and ASC 842.

To adjust a lease, follow these steps. The modified data will update lease schedules after the users posts from the lease adjustment wizard. You can save and close the wizard and come back to your progress at any time.

## Lease adjustment wizard

To open the lease adjustment wizard from the lease summary:

1.	Go to Asset leasing > Leases > Lease summary 
2.	On the **Lease summary page**, select the lease to adjust, and then select **Adjustment wizard** 

To open the lease adjustment wizard for an adjustment in progress from the lease adjustments form:

1.	Go to **Lease > Leases > Lease adjustments**.
2.	Select a lease with adjustment status in progress and click **Adjustment wizard**
3.	Enter dates for the **Modification start date** and **Posting date**
4.	Click **Next**

The lease is now inserted into the Lease adjustments form. Enter the new information about the adjusted lease.

After the lease has been adjusted, the right-of-use considerations fields now apply to the adjusted lease. If no initial direct costs, lease incentives, prepayments, or dismantling costs are associated with the modified lease, leave these fields blank. The original amounts won't apply to the updated lease. 

For example, suppose that a lessor provides a $1,000 incentive for agreeing to a lease extension. In this case, when you adjust the lease to account for the extension, enter 1,000 in the Lease incentives arising from adjustment field.

The payment schedule lines now show all payments from the month in the **Modification start date** field and moving forward. Because modifications are prospective, payment schedule lines cannot start before the date that the modification starts. To view payment schedule lines from before the Modification start date, navigate to the Lease version history.

8.	Click **Next**

The form shows key details about the expected lease adjustment such as the carrying values of the lease liability prior to the modification and the new expected lease liability after the modification. The form also shows a preview of the expected lease adjustment journal entry.

9.	If the lease adjustment workflow is active and not yet approved, to submit the lease adjustment into the workflow, click **Submit to workflow**. For more information on using the lease adjustment workflow, please see the **Use lease adjustments workflows topic**.

Note: the system will recalculate the adjustment variables at this point to confirm that there were no transactions posted against this lease since the adjustment overview and adjustment journal entry were first calculated. If any values change, the adjustment overview grid will update and you can review again before clicking Submit to workflow again.

10.	If there is no workflow active or if the lease adjustment has been approved, to process the modification and post the adjustment journal entry, click Finish

>[!Note] 
>The system will recalculate the adjustment variables at this point to confirm that there were no transactions posted against this lease since the adjustment overview and adjustment journal entry were first calculated. If any values change, the adjustment overview grid will update and you can review again before clicking Finish. If the workflow is active and the lease adjustment was approved, any changes to the adjustment overview will revert the approval status back to “Not submitted” and the lease adjustment should be submitted to workflow again.


11.	The Adjustment status on the Lease adjustments form is marked Completed

From the Lease adjustments form, the user can still view the Adjustment overview and adjustment entry preview fast tabs. The lease details and date information are in the lease version history of that lease.

12.	A new lease version and set of schedules are now created using the modified information. 

13.	To view the new schedules, navigate to the lease and click Books.

14.	To view the newly created payment schedule, select Payment schedule

15.	To view the new lease liability amortization schedule that is generated from the new inputs, close the Payment schedule page, and open the Liability amortization schedule page.

16.	To view the newly generated asset depreciation schedule, open the Asset depreciation schedule page from the Book details page.

17.	To view the adjustment journal entry, select Journals > Asset leasing journal.

## Cancelling a lease adjustment

To delete a lease adjustment in progress, follow the steps below:

1.	Go to Lease > Leases > Lease adjustments
2.	Select the lease adjustment in progress to cancel
3.	Click Cancel adjustment 
4.	Click OK

>[!Note] Clicking Cancel on the lease adjustment wizard will rollback the most recent progress on the lease adjustment wizard but will not remove the adjustment in progress.  

## Use lease adjustment workflows

This topic explains how to use the lease adjustment workflow. The lease adjustment workflow provides consistency to the management of lease adjustment approvals by providing a set of approval steps and assigning specific users who approve a lease adjustment before the lease is adjusted. Once the lease adjustment is approved in the workflow, the user can finish the lease adjustment through the lease adjustment wizard.

1.	To submit a lease adjustment for approval, go Lease > Leases > Lease adjustments
2.	Select the lease adjustment and click **Adjustment wizard**
3.	On the last page of the wizard, select **Submit for approval**
4.	Enter a message and click **OK**

The workflow status will now change to “Pending approval” and all fields on the wizard will be locked from editing.

5.	To approve the lease adjustment, go Lease > Leases > Lease adjustments
6.	Click the Lease ID hyperlink to review the adjustment overview and adjustment entry preview fast tabs
7.	Select Workflow > Approved

The workflow status on the Lease adjustments form will update to Approved. Now the lease adjustment is ready to post the adjustment journal entry.

8.	To continue processing the lease adjustment and post the adjustment entry, go to Lease > Leases > Lease adjustments.
9.	Select the Lease ID and click **Adjustment wizard**
10.	Click **Next** through the wizard
11.	Click **Finish** on the final page of the wizard

The system will recalculate the carrying values of the lease to ensure the adjustment variables that were approved are current. If there are any changes, the approval status will revert to “Draft” and the lease adjustment should be submitted to workflow again.


## View lease versions

If a lease has been modified, you can view the different versions of it. You can also view the historical schedules and past lease details.

1. On the **Lease summary** page, select the lease, and then, on the Action Pane, select **Lease version history**.

    If the selected lease has been adjusted, the **Lease version history** page shows the different versions of it. The original lease is labeled **1**, and subsequent versions have ascending numerical order.

    For a selected lease version, you can view the financial dimensions, contract details, location, and payment schedule lines.

2. To view historical schedules, open the modified lease from the **Lease summary** page, select the desired book, and then, on the Action Pane, select **Book version history**.
3. On the **Book version** page, select the desired version and the desired schedule to view.
