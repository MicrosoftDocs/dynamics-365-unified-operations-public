---
# required metadata

title: Record leases in foreign currencies
description: This topic describes the adjustment to lease liability for a right of use asset that arises from changes in variable lease payments because of a change in the index rate.
author: moaamer
manager: Ann Beebe
ms.date: 08/05/2020
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
ms.search.validFrom: 2020-08-05
ms.dyn365.ops.version: 10.0.14
---

# Revalue lease payments tied to an Index Rate

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic describes the adjustment to lease liability for a right of use asset that arises from changes in variable lease payments because of a change in the index rate. The lease liability and right-of-use (ROU) assets will be adjusted to account for the new payments. Under US GAAP ASC 842, only the variable payments will change when payments increase/decrease due to a change in the index rate unless there are additional changes to cash flows such as a change in lease terms related to interest rates. For more information, refer to ASC 842-10-55-225 and IFRS 16 paragraph 42(b).

1.	To run the lease index revaluation process, open the **Index rate revaluation** page (**Asset leasing > Periodic > Index rate revaluation**).
   The Index rate revaluation page shows all prior lease index revaluation processes that have been run. Information included on this form are the Process ID generated from the number sequences setup form, the legal entity, number of leases adjusted, total liability adjustment for IFRS 16 leases, and the total variable payments adjusted for ASC 842 leases.
2. To run the revaluation, select Lease index revaluation in the top ribbon.
3. The **Index revaluation parameters** page will appear. You can filter and select which leases, lease group, or other criteria to use when selecting the leases to revalue. The index revaluation process can also be set up to run in batch by using the **Run in the Background** tab.
4. When the desired filters are selected, select OK.
5. The **Index Rate revaluation preview** page will open. This page displays the leases that will be revalued, including the asset and liability adjustments or the variable payment adjustments. To prevent leases from being revalued, select only the leases that should be revalued. If you don't select any leases, all leases will be revalued. To revalue the lease payments, click **OK**.
6. To view the transactions created on a specific index revaluation process, select that process ID, and then select **Transactions**. A dialog will open that shows the details of the transactions that were created during processing.

> [!Note]
> Only leases with a Revaluation date on or prior to the system date are eligible to be revalued. The system will automatically ignore all leases with a revaluation date after the system date.

## ASC 842 Leases – Index Revaluation

To view the effects of the lease revaluation process on ASC 842 leases, navigate to the payment schedule for the lease. Only the variable payments on or after the revaluation date has been changed due to the index revaluation [*are displayed? Something is missing from this*]. The amortization and depreciation schedules remain unchanged. When you create an invoice with a variable payment, the variable payment will be debited to the Variable payment posting account, and the variable payment amount will also be added to the credit entry to the vendor or Lease payment posting account.

The payment schedule lines in the lease details form are automatically updated with a new line indicating the new index rate and a column showing how line was created -- either manually or through the index revaluation process.

## IFRS 16 Leases – Index Revaluation

1.	To view the effects of the lease revaluation process on IFRS 16 leases, navigate to the lease details for the adjusted lease. The Lease term and Asset useful life fields have been updated to reflect the passage of time from the Commencement date or Modification date to the Revaluation date.
2.	Additionally, the payment schedule lines have updated to reflect the new payments on the lease as well as the new index rate and how the line was created:
3.	Next, the user can view the newly generated payment schedule beginning on the date of revaluation and displaying the total updated payment amount:
4.	A new lease liability amortization and asset depreciation schedule have also been created to reflect the adjusted payment schedule.
5.	The journal entry has automatically posted the adjustment journal entry to account for the change in lease payments related to the index revaluation.
