---
# required metadata

title: Adjust a lease
description: The topic lists the steps for adjusting a lease, which might be necessary if the lease terms are modified, the lease is extended, or if other circumstances change that require an adjustment to the lease.  
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

# Adjust a lease

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The topic lists the steps for adjusting a lease, which might be necessary if the lease terms are modified, the lease is extended, or if other circumstances change that require an adjustment to the lease. Asset leasing is compliant with the guidance provided by ASC 842 and IFRS 16 regarding lease modifications. ASC 842 defines a lease modification as a change to the terms and conditions of a contract that result in a change in scope of, or the consideration for, a lease (ASC 842-20-15-1).

IFRS 16 states that a lessee must revalue the lease liability to reflect changes to the lease payments (Paragraph 39).

For organizations that adhere to ASC 842 or IFRS 16, the lease is remeasured to reflect the change in the present value of the future minimum lease payments (PVFMLP). If there is an increase to the PVFMLP, the journal entry created will be a debit to the right-of-use asset (ROU) and a credit to the lease liability for the difference between the new PVFMLP and prior PVFMLP. A decrease in the present value of future minimum lease payments will debit the lease liability and credit the right-of-use asset for the difference.

Should the adjustment decrease the ROU asset past 0, the remainder will be credited to the gain on lease modification posting account specified on the **Lease posting accounts** page. The system accounts for these transactions and other adjustment entries such as classification changes, initial direct costs, lease incentives, prepayments, and dismantling costs arising from lease modifications.

We recomment that you refer to IFRS 16 and ASC 842 for specific guidance on lease adjustment transactions.

1. To adjust a lease, select the lease to be adjusted from the **Asset leasing| Leases| Lease summary** page and select **Adjust lease**. The modified data will update lease schedules after the **Create schedule** process has run.
2. **Adjust lease**  page that's similar to the **Add lease** page will appear. The user may enter the new information for the adjusted lease. Note, like the commencement date when first adding a lease, the **Modification date** field determines when the modified lease will commence. This date cannot be after the Start Date on the payment schedule lines.

 > [!Note] 
 > The **ROU considerations** fields apply to the lease adjustment. If there are no initial direct costs, lease incentives, prepayments, or dismantling costs associated with the modified lease, these fields should be left blank. The original amounts will not apply to the updated lease. Any additional costs incurred in modifying the lease should be inputted in this form.

For example, assume that a lessor provides a $1,000 incentive for signing into a lease extension. When adjusting the lease to account for the extension, you would enter 1,000 in the **Lease incentives** field. If there no incentives were associated with the lease adjustment, any value previously in this field should be removed. The same logic is applied to other ROU Considerations.

1.	The payment schedule lines of the adjusted lease should be created on a prospective basis. Creating payment schedule lines on a prospective basis means they cannot start before the lease modification takes effect.
2.	The steps that follow are nearly identical to initially recognizing a lease. Select **Create schedules** to generate the adjusted payment schedule. A notification will show that the payment schedule has been created for that lease.

   > [!Note]
   > Before clicking **Create schedules**, ensure that the **Modification date** and **Payment schedule lines** are accurate. Also ensure the Initial direct costs, Lease incentives, Prepayments, or Dismantling costs all correspond with only those costs arising from adjustment.

1.	To view the newly created Payment schedule, select **Books** and navigate to the **Payment schedule**.
2.	The **Payment schedule** will open, and the user can edit the adjusted payment amounts before confirming the schedule by clicking **Confirm schedule**. 

When confirmed, the new asset depreciation and new lease liability schedules will be created.

3.	To view the new lease liability amortization schedule generated from the new inputs, exit the **Payment Schedule** page and navigate to **Liability amortization schedule**.
4.	To view the newly generated asset depreciation schedule, open the **Asset depreciation schedule** from the **Book details** page.
5.	To generate the adjustment journal entry, select **Function > Lease adjustment**.
6.	A message will appear to notify you that the adjustment journal entry has been created. To view the journal entry, click **Journals > Asset leasing journal**.
7.	To post the journal entry, select the line and click **Post**.


## View Lease Versions

If a lease has been modified, the user is able to view the different versions of the lease including the historical schedules and past lease details.

1.	Navigate to that lease and select the lease in the Lease summary and select **Lease version history** in the top ribbon.
2.	The **Lease versions** page displays the versions of a lease if it has been adjusted. The original lease is labeled "1" with subsequent versions in ascending numerical order. The **Lease status** is shown under the lease ID, which indicates which lease version is currently active or closed. Transactions cannot be entered for a closed lease. The user can view the financial dimensions, contract details, location, and payment schedule lines of the selected lease version.
3.	To view historical schedules, open the modified lease from the **Lease summary** page, and then select the desired book. Then, click **Book version history** in the top ribbon.
4.	From the **Book version** page, select the desired version and the desired schedule to view.
