---
title: Tax interest and free-hand interest for Poland
description: Learn how to set up and calculate tax interest for Poland in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/19/2025
ms.reviewer: johnmichalak
ms.search.region: Poland
ms.search.validFrom: 2016-05-31
---

# Tax interest and free-hand interest for Poland

[!include[banner](../../includes/banner.md)]

This article explains how to set up and calculate tax interest for Poland in Microsoft Dynamics 365 Finance.

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

To define the parameters for interest calculation, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Collections** tab, on the **Interest and fees** FastTab, in the **Interest calculation** field, select the transactions that interest should be calculated for.

### Set up interest codes

Interest codes contain settings that determine when interest is charged, and how it's calculated on overdue accounts.

To set up and maintain interest codes, follow these steps.

1. In Dynamics 365 Finance, go to **Credit and collections** \> **Interest** \> **Set up interest codes**.
1. On the **Interest** page, in the **Interest code** field, enter a unique code that should be used to calculate interest.
1. Enter a description of the interest code.
1. In the **Grace period** field, enter the number of days before interest is calculated.
1. On the **Earnings** FastTab, in the **Ledger posting account** field, select the ledger account number for interest earnings.
1. On the **Payments** FastTab, in the **Ledger posting account** field, select the ledger account number for interest payments.

    > [!NOTE]
    > The interest is calculated from the payment date.

1. On the **Earnings** FastTab, in the **Calculate interest based on** field, select either **Percentage** or **Amount**. If you select **Percentage**, enter the tax interest rate in the **Monthly interest %** field.
1. Repeat step 7 on the **Payments** FastTab.

### Set up a number sequence code for the interest note and voucher

When you create an interest note, the document number is automatically assigned in a sequence.

To set up the number sequence used for interest notes, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Number sequences** tab, select a number sequence code for the **Interest note** reference.
1. Select a number sequence code for the **Interest note voucher** reference.

### Set up customer posting profiles

For more information, see [Customer posting profiles](../../accounts-receivable/customer-posting-profiles.md).

## Calculate tax interest and free-hand interest

In Poland, the tax interest rates are determined by the Ministry of Finance. The vendor calculates the interest if the payment settlement is made after the due date. If the payment period is shorter than 30 days, the vendor can calculate the tax interest from the due date through the payment date. Free-hand interest rates apply when payments are settled between the thirty-first day after the posting and the due date.

To calculate tax interest and free-hand interest, follow these steps.

1. In Dynamics 365 Finance, go to **Credit and collections** \> **Interest** \> **Create interest notes**.
1. In the **Interest calculation** dialog, set the **Invoice** option to **Yes** to calculate interest on invoices.
1. Set the **Credit note** option to **Yes** to deduct customer credit notes before the interest calculation.
1. Set the **Payment** option to **Yes** to deduct customer payments before the interest calculation.
1. Set the **Interest** option to **Yes** to calculate compound interest on previous interest notes.
1. In the **From date** field, select the start date for the interest calculation. The calculation includes transactions that are due on or after this date.
1. In the **To date** field, select the end date for the interest calculation.
1. In the **Round-off** field, specify the units to round off the interest amount to.
1. In the **Use posting profile from** field, select the posting profile that should be used:

    - **Account** – Use the posting profile from the relevant customer account for each interest note.
    - **Select** – Use the posting profile that is specified in the **Posting profile** field.
    
1. If you selected **Select** in the **Use posting profile from** field, in the **Posting profile** field, select the posting profile for the calculation.
1. Set the **Tax interest** option to **Yes** to calculate the free-hand interest and tax interest.
1. On the **Records to include** FastTab, select **Filter** to find and select records for the interest calculation.
1. Select **OK**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
