---
# required metadata

title: Tax interest and free-hand interest for Poland
description: This topic walks you through the process of setting up and calculating tax interest for Poland.
author: ShylaThompson
ms.date: 05/18/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Poland
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Tax interest and free-hand interest for Poland

[!include[banner](../includes/banner.md)]

In Poland, two types of interest rates are used:

- **Tax interest rates** are specified by the Ministry of Finance. These interest rates are also referred to as *statutory interest rates*.
- **Free-hand interest rates** are negotiated between the vendor and the customer.

> [!NOTE]
> Free-hand interest might not be calculated, depending on the agreement between the customer and the vendor. However, tax interest must be calculated.

Usually, the vendor sets a settlement period that is no longer than 30 days. However, the following situations can arise:

- The vendor and customer agree on a settlement period that is longer than 30 days, or the settlement period isn't set. In this case, free-hand interest can be calculated from the thirty-first day until the due date. Alternatively, tax interest can be calculated until the date of payment.
- The settlement period is shorter than 30 days. In this case, the vendor can calculate tax interest from the due date until the date of payment.

## Setup

Before you can calculate tax interest and free-hand interest, you must complete the following setup tasks.

### Set up the Accounts receivable parameters to calculate interest

Use this procedure to define the parameters for interest calculation in Accounts receivable. 

1. Select **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters**.
2. On the **Accounts receivable parameters** page, on the **Collections** tab, on the **Interest and fees** FastTab, in the **Interest calculation** field, select the transactions that interest should be calculated for.

### Set up interest codes

Use this procedure to set up and maintain interest codes. Interest codes contain settings that determine when interest is charged, and how it's calculated on overdue accounts.

1. Select **Credit and collections** &gt; **Interest** &gt; **Set up interest codes**.
2. On the **Interest** page, in the **Interest code** field, enter a unique code that should be used to calculate interest.
3. Enter a description of the interest code.
4. In the **Grace period** field, enter the number of days before interest is calculated.
5. On the **Earnings** FastTab, in the **Ledger posting account** field, select the ledger account number for interest earnings.
6. On the **Payments** FastTab, in the **Ledger posting account** field, select the ledger account number for interest payments.

    > [!NOTE]
    > The interest is calculated from the payment date.

7. On the **Earnings** FastTab, in the **Calculate interest based on** field, select either **Percentage** or **Amount**. If you select **Percentage**, enter the tax interest rate in the **Monthly interest %** field.
8. Repeat step 7 on the **Payments** FastTab.

### Set up a number sequence code for the interest note and voucher

Use this procedure to set up the number sequence that is used for interest notes. When you create an interest note, the document number is automatically assigned in a sequence.

1. Select **Accounts receivable** &gt; **Setup** &gt; **Accounts receivable parameters**.
2. On the **Accounts receivable parameters** page, on the **Number sequences** tab, select a number sequence code for the **Interest note** reference.
3. Select a number sequence code for the **Interest note voucher** reference.

### Set up customer posting profiles

For more information, see [Customer posting profiles](../accounts-receivable/customer-posting-profiles.md).

## Calculate tax interest and free-hand interest

In Poland, the tax interest rates are determined by the Ministry of Finance. The vendor calculates the interest if the payment settlement is made after the due date. If the payment period is shorter than 30 days, the vendor can calculate the tax interest from the due date through the payment date. Free-hand interest rates apply when payments are settled between the thirty-first day after the posting and the due date.

1. Select **Credit and collections** &gt; **Interest** &gt; **Create interest notes**.
2. In the **Interest calculation** dialog box, set the **Invoice** option to **Yes** to calculate interest on invoices.
3. Set the **Credit note** option to **Yes** to deduct customer credit notes before the interest calculation.
4. Set the **Payment** option to **Yes** to deduct customer payments before the interest calculation.
5. Set the **Interest** option to **Yes** to calculate compound interest on previous interest notes.
6. In the **From date** field, select the start date for the interest calculation. The calculation will include transactions that are due on or after this date.
7. In the **To date** field, select the end date for the interest calculation.
8. In the **Round-off** field, specify the units to round off the interest amount to.
9. In the **Use posting profile from** field, select the posting profile that should be used:

    - **Account** – Use the posting profile from the relevant customer account for each interest note.
    - **Select** – Use the posting profile that is specified in the **Posting profile** field.
    
10. If you selected **Select** in the **Use posting profile from** field, in the **Posting profile** field, select the posting profile for the calculation.
11. Set the **Tax interest** option to **Yes** to calculate the free-hand interest and tax interest.
12. On the **Records to include** FastTab, select **Filter** to find and select records for the interest calculation.
13. Select **OK**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]