---
# required metadata

title: Set up lease books
description: This article describes the information that is maintained in lease books. Lease books contain the accounting policies that determine how a lease is accounted for.
author: moaamer
ms.date: 03/28/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: AssetLeaseBookMaster
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.custom: 4464
ms.assetid: 5f89daf1-acc2-4959-b48d-91542fb6bacb
ms.search.region: Global
# ms.search.industry: 
ms.author: moaamer
ms.search.validFrom: 2020-10-28
ms.dyn365.ops.version: 10.0.14


---

# Set up lease books

[!include [banner](../includes/banner.md)]

Lease books contain the accounting policies that determine how a lease is accounted for. In addition to cash basis accounting, Asset leasing supports the following standards:

- Generally Accepted Accounting Principles in the United States (US GAAP)
- Accounting Standards Codification Topic 842 (ASC 842)
- ASC 840
- International Financial Reporting Standard 16 (IFRS 16)
- International Accounting Standard 17 (IAS 17)

To create a lease book, follow these steps.

1. Go to **Asset leasing \> Setup \> Lease books**.
2. Select **New** to add a book.
3. Set the following fields.

    | Name                                     | Description |
    |------------------------------------------|-------------|
    | **Posting layer**                            | Select the posting layer to use. Each book that is attached to a lease is set up for a specific posting layer. Each posting layer has different posting purposes. |
    | **Lease type**        | Select whether the lease should be classified automatically, or whether it should be predefined as a finance or operating lease. |
    | **Accounting framework**                     | Select the framework that is associated with the book. |
    | **Lease term/Useful life setup**          | The lease will be classified as a finance lease if the lease type is set to **Automatic**, and if the lease term over useful life of the asset is greater than or equal to the percentage entered in this field.  |
    | **Present value / Asset fair value setup**   | Enter a whole number to define the threshold that will determine the lease type. If the present value of future minimum lease payments is more than the user-defined value from the book setup, and if the book's lease classification is set to automatic, the system will classify the lease as a finance lease. |
    | **Short-term threshold**    | Enter the number of months to use as a threshold for short-term leases. If the lease term is less than or equal to the number of months that you enter here, the lease will be classified as a short-term lease, and the deferred rent treatment will be applied. |
    | **Low value threshold**      | Enter an amount to use as a threshold for low-value leases. If the fair value of the asset is less than or equal or the value that you enter here, the lease will be classified as a low-value lease, and the deferred rent treatment will be applied. |
    | **Pay to vendor**           | Set this option to **Yes** to allow lease payments to be posted, as an invoice, to the vendor account that is specified on each lease. When a lease payment is posted, the vendor account will be credited. If this option is set to **No**, the account that is specified for the **Lease payment** posting type on the **Lease posting parameters** page will be credited instead. |
    | **Leasing convention**                       | Select the convention for the commencement date of the lease:<ul><li><b>None</b> – Use the lease's start date as the commencement date.</li><li><b>Full month</b> – Use the first day of the month that the lease's start date falls in as the commencement date.</li></ul><p>If you select <b>None</b>, there is a risk that the liability amortization and asset depreciation schedules will accrue and post expenses in the middle of the month instead of at the end of the month. By selecting <b>Full month</b>, you ensure that the system will start to account for the lease on the first day of the month, and that the whole month's expense will be accrued and posted on the last day of the month.</p><p><strong>Note:</strong> The feature for leasing conventions must be turned on through **Feature management**. In the <b>Feature management</b> workspace, find and select the feature that is named <b>Leasing convention for asset leasing</b> feature, and then select <b>Enable now</b>.</p> |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
