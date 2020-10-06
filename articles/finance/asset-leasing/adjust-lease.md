---
# required metadata

title: Adjust leases
description: The topic explains how to adjust a lease. Adjustment might be required if the lease terms are modified, the lease is extended, or other circumstances change.
author: moaamer
manager: Ann Beebe
ms.date: 08/04/2020
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
ms.search.scope: Core, Operations, Retail

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: vstehman
ms.search.validFrom: 2020-08-04
ms.dyn365.ops.version: 10.0.14

---

# Adjust leases

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The topic explains how to adjust a lease. Adjustment might be required if the lease terms are modified, the lease is extended, or other circumstances change. Asset leasing complies with the guidance that Accounting Standards Codification Topic 842 (ASC 842) and International Financial Reporting Standard 16 (IFRS 16) provide about lease modifications. ASC 842-20-15-1 defines a lease modification as any change to the terms and conditions of a contract that causes a change in the scope of, or the consideration for, a lease. Paragraph 39 of IFRS 16 states that a lessee must revalue the lease liability so that it reflects changes to the lease payments.

For organizations that adhere to ASC 842 or IFRS 16, a lease is remeasured to reflect a change in the present value of the future minimum lease payments (PVFMLP). If the PVFMLP increases, the journal entry that is created will be a debit to the right-of-use (ROU) asset and a credit to the lease liability for the difference between the new PVFMLP and the previous PVFMLP. If the PVFMLP decreases, the journal entry will be a debit to the lease liability and a credit to the ROU asset for the difference.

If the adjustment decreases the ROU asset past 0 (zero), the remainder will be credited to the gain on lease modification posting account that is specified on the **Lease posting accounts** page. The system accounts for these transactions and other adjustment entries, such as classification changes, initial direct costs, lease incentives, prepayments, and dismantling costs that arise from lease modifications.

For specific guidance about lease adjustment transactions, we recommend that you see IFRS 16 and ASC 842.

To adjust a lease, follow these steps. The modified data will update lease schedules after the Create schedule process is run.

1. Go to **Asset leasing \> Leases \> Lease summary**.
2. On the **Lease summary** page, select the lease to adjust, and then select **Adjust lease**.
3. On the **Adjust lease** page, enter the new information for the adjusted lease.

    Notice that the **Adjust lease** page resembles the **Add lease** page. Additionally, just as the commencement date that you specify when you add a lease determines when the new lease starts, the **Modification date** field on the **Adjust lease** page determines when the modified lease starts. This date can't be after the start date on the payment schedule lines.

    > [!NOTE]
    > The **ROU considerations** fields apply to the lease adjustment. If no initial direct costs, lease incentives, prepayments, or dismantling costs are associated with the modified lease, you should leave these fields blank. The original amounts won't apply to the updated lease. Any additional costs that are incurred when the lease is modified should be entered on the **Adjust lease** page.
    > 
    > For example, a lessor provides a $1,000 incentive for signing in to a lease extension. In this case, when you adjust the lease to account for the extension, you enter **1,000** in the **Lease incentives** field. If no incentives are associated with the lease adjustment, you should clear any value that was previously entered in this field. The same logic is applied to other ROU considerations.

    The payment schedule lines of the adjusted lease should be created on a prospective basis. Payment schedule lines that are created on a prospective basis can't start before the lease modifications take effect.

    The following steps are almost identical to the steps for initially recognizing a lease.

4. Select **Create schedules** to generate the adjusted payment schedule. You receive a message that states that the payment schedule has been created for the lease.

    > [!IMPORTANT]
    > Before you select **Create schedules**, make sure that the modification date and payment schedule lines are accurate. Also make sure that all initial direct costs, lease incentives, prepayments, or dismantling costs correspond only to those costs that arise from the adjustment.

5. To view the newly created payment schedule, select **Books**, and open the **Payment schedule** page.
6. On the **Payment schedule** page, you can edit the adjusted payment amounts before you confirm the payment schedule. To confirm the schedule, select **Confirm schedule**.

    When the payment schedule is confirmed, the new asset depreciation and new lease liability schedules are created.

7. To view the new lease liability amortization schedule that is generated from the new inputs, close the **Payment schedule** page, and open the **Liability amortization schedule** page.
8. To view the newly generated asset depreciation schedule, open the **Asset depreciation schedule** page from the **Book details** page.
9. To generate the adjustment journal entry, select **Function \> Lease adjustment**. You receive a message that states that the adjustment journal entry has been created. 
10. To view the journal entry, select **Journals \> Asset leasing journal**.
11. To post the journal entry, select the line, and then select **Post**.

## View lease versions

If a lease has been modified, you can view the different versions of it. You can also view the historical schedules and past lease details.

1. On the **Lease summary** page, select the lease, and then, on the Action Pane, select **Lease version history**.

    If the selected lease has been adjusted, the **Lease versions** page shows the different versions of it. The original lease is labeled **1**, and subsequent versions have ascending numerical order.

    The lease status is shown under the lease ID. It indicates which lease version is currently active or closed. Transactions can't be entered for a closed lease.

    For a selected lease version, you can view the financial dimensions, contract details, location, and payment schedule lines.

2. To view historical schedules, open the modified lease from the **Lease summary** page, select the desired book, and then, on the Action Pane, select **Book version history**.
3. On the **Book version** page, select the desired version and the desired schedule to view.
