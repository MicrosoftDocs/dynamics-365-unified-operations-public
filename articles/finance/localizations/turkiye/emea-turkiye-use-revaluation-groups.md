---
title: Perform fixed asset revaluation
description: Learn how to perform fixed asset revaluation for Türkiye.
author: v-omerorhan
ms.author: v-omerorhan
ms.topic: article
ms.date: 02/17/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Türkiye
ms.search.validFrom: 2022-11-03
ms.dyn365.ops.version: AX 10.0.45
---

# Perform fixed asset revaluation
[!INCLUDE[banner](../../includes/banner.md)]

This article explains how to perform fixed asset revaluation in Microsoft Dynamics 365 Finance for Türkiye.

You can perform fixed asset revaluation by using predefined revaluation groups or by specifying revaluation parameters directly in the fixed asset book or revaluation journal.
This article covers the use of revaluation groups, posting profile configuration, revaluation proposals, and how to review revaluation results in the Fixed assets module.

The following example shows how the factor affects the revalued amount and the resulting adjustment transaction:  

| Acquisition amount | Factor | Revalued amount (Acquisition × Factor) | Transaction (Revalued – Acquisition) |
|--------------------|--------|---------------------------------------|---------------------------------------|
| 100,000            | 1.00   | 100,000                               | 0 (No transaction)                    |
| 100,000            | 1.10   | 110,000                               | +10,000 (Debit)                       |
| 100,000            | 0.50   | 50,000                                | –50,000 (Credit)                      |

In this example:  
- If the acquisition cost is 100,000 TRY and the factor is **1.10**, the revalued amount becomes 110,000 TRY, and the system posts a **debit** adjustment of 10,000 TRY.  
- If the factor is **0.50**, the revalued amount becomes 50,000 TRY, and the system posts a **credit** adjustment of 50,000 TRY.  

## Create a revaluation group  

This section explains how to create a revaluation group.

Revaluation groups are optional. Use them to standardize and reuse revaluation parameters, such as the factor and revaluation date, across multiple fixed assets.

To configure a revaluation group, follow these steps:

1. Go to **Fixed assets > Setup > Revaluation groups**.  
1. Select **New**.  
1. Enter a unique **Group ID** and description.  
1. Specify the **Factor** or **Revaluation date** to apply.  
1. Save the group.

## Set up revaluation posting profiles

This section explains how to set up revaluation posting profiles.

When you post a fixed asset revaluation in Finance, the system generates ledger entries based on the **Fixed asset posting profiles** setup. For Türkiye, additional transaction types are available as follows:   

- **Revaluation – Acquisition**: Adjusts the acquisition cost of the fixed asset.  
- **Revaluation – Depreciation**: Adjusts the accumulated depreciation according to the revaluation factor.
- **Revaluation – Depreciation past**: Adjusts the accumulated depreciation according to the revaluation factor.  

To define ledger accounts for these types, follow these steps: 

1. Go to **Fixed assets > Setup > Posting profiles**.
1. Select the posting profile where you want to define revaluation ledger accounts.
1. In the **Ledger accounts** FastTab, select **Revaluation – Acquisition**.
1. Select **Add**.
1. In the **Book** field, enter or select a value.
1. In the **Grouping** field, select an option. The **Groupings** field allows you to define the posting profile down to the **Table** (one account set up for each fixed asset) or **Group** (one account set up for each fixed asset group).
1. In the **Account relation** field, select the fixed asset or fixed asset group.
1. In the **Main account** field, specify the desired values.
1. In the **Offset account** field, specify the desired values.
1. In the **Ledger accounts** FastTab, select **Revaluation – Depreciation**.
1. Select **Add**.
1. In the **Book** field, enter or select a value.
1. In the **Grouping** field, select an option.
1. In the **Account relation** field, select the fixed asset or fixed asset group.
1. In the **Main account** field, specify the desired values.
1. In the **Offset account** field, specify the desired values.
1. In the **Ledger accounts** FastTab, select **Revaluation – Depreciation past**.
1. Select **Add**.
1. In the **Book** field, enter or select a value.
1. In the **Grouping** field, select an option.
1. In the **Account relation** field, select the fixed asset or fixed asset group.
1. In the **Main account** field, specify the desired values.
1. In the **Offset account** field, specify the desired values.  
1. Select **Save**. Learn more in [Set up fixed asset posting profiles](../../../finance/fixed-assets/tasks/set-up-fixed-asset-posting-profiles.md).

## Create a revaluation proposal

This section explains how to create a revaluation proposal for fixed assets in Finance. 

To create a revaluation proposal, complete the following steps:  

- Set up the **Fixed asset book** for each asset.  
- Define a **Revaluation group** and factor on the **Revaluation groups** page if you want to retrieve revaluation factors from the book.  
- Configure ledger accounts for revaluation adjustments in **Fixed asset posting profiles**.  

The following table describes the fields that are available in the **Revaluation proposal** dialog in Dynamics 365 Finance.  

| Field | Description |
|-------|-------------|
| To date | Specifies the end date for the revaluation period. Transactions up to this date are included. |
| Get from transaction date | Indicates whether the system should use the transaction date instead of the **To date** value. |
| Transaction date | Defines the posting date for revaluation journal lines. If left blank, the **To date** value is used. |
| Factor | Coefficient used to revalue acquisition cost and accumulated depreciation. Editable only if **Get factor from book** is set to No. |
| Get factor from book | When set to **Yes**, retrieves the revaluation factor defined in the fixed asset book. |
| Intra-year transaction | Indicates whether multiple revaluations can be applied within the same fiscal year. |
| Fixed asset number | Limits the proposal to a specific fixed asset. Leave blank to include all eligible assets. |
| Fixed asset group | Limits the proposal to assets in a selected fixed asset group. |
| Book | Specifies the fixed asset book that will be revalued. |
| Posting layer | Defines the posting layer where revaluation transactions are recorded. In Türkiye, usually **Current** is used for statutory reporting. |
| Calculate depreciation | If **Yes**, revaluation also updates accumulated depreciation based on the new acquisition value. |
| Revaluation group | Optionally links the revaluation to a predefined revaluation group with a factor and date. |

To create a revaluation proposal, follow these steps: 

1. Go to **Fixed assets > Journal entries > Fixed assets > Fixed asset journal**.  
1. Select a journal for the revaluation process.  
1. On the **Lines** FastTab, select **Proposals > Revaluation proposal**.

   - The **Revaluation proposal** dialog opens.

1. In the **Parameters** section, enter the following information:
  
   - **To date** – Select the revaluation date.  
   - **Get from transaction date** – Select **Yes** to override the “To date.”  
   - **Transaction date** – If required, specify the posting date of revaluation entries.
  
1. In the **Calculation** section, choose one of the following options:
  
   - Enter a **Factor** manually.  
   - Select **Get factor from book = Yes** to pull the factor from the fixed asset book.  
   - If required, mark **Intra-year transaction** to allow multiple revaluations in the same fiscal year.
  
1. In the **Records to include** section, filter which assets are included:
  
   - **Fixed asset number** – Select a single asset.  
   - **Fixed asset group** – Select a group of assets.  
   - **Book** – Select the book that you want to revalue.
  
1. In the **Fixed asset book setup** section:
 
   - **Posting layer** – Select the appropriate posting layer (for statutory books in Türkiye, typically **Current**).  
   - **Calculate depreciation** – Set to **Yes** if accumulated depreciation should be recalculated.  
   - **Revaluation group** – Select a group if a predefined revaluation group is used.
  
1. Select **OK** to generate the proposal.
  
   - The system creates journal lines in the **Fixed asset journal** with revaluation acquisition and revaluation depreciation entries.
 
1. Post the journal to update the asset values in the general ledger and fixed asset module.  

## Review results of a fixed asset revaluation

This section explains how to review results of fixed asset revaluation.

When you post a fixed asset journal for revaluation, you can review the results in both the **Fixed assets** module and the **General ledger** module. For this step, 

- Configure posting profiles for revaluation transactions.
- Post a revaluation journal.

### Review in the Fixed asset valuations

To review in the Fixed asset valuations, follow these steps:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. Select the asset that you revalued.
1. Select **Valuations** on ActionPane.
1. Select **Balances**.

   - Verify that the **Revaluation – Acquisition** is updated.
   - Check that the **Revaluation – Depreciation** is adjusted.
   - Confirm that the **Revaluation – Depreciation past** reflects the new balance.

### Review in the Fixed asset book

To review in the Fixed asset book, follow these steps:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. Select the asset that you revalued.
1. Select **Books** on ActionPane.
1. Select **Balances** and review the revaluations results.

   - Verify that the **Revaluation – Acquisition** is updated.
   - Check that the **Revaluation – Depreciation** is adjusted.

### Review in Fixed asset transactions

To review in Fixed asset transactions, follow these steps:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. Select the asset that you revalued.
1. Select **Books** on ActionPane.
1. Select **Transactions** on ActionPane in **Books** page.
1. In the **Transaction type** field, filter by:

   - Revaluation – Acquisition
   - Revaluation – Depreciation
   - Revaluation – Depreciation past

1. Review the transaction amounts, dates, and vouchers.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
