---
title: Validate store transactions for statement calculation
description: This article provides an overview of the functionality for validating store transactions in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 01/30/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: Global
ms.author: shajain
ms.search.validFrom: 2019-01-15
ms.custom: 
  - bap-template
---

# Validate store transactions for statement calculation

[!include [banner](includes/banner.md)]

This article provides an overview of the functionality for validating store transactions in Microsoft Dynamics 365 Commerce. The validation process identifies and marks transactions that cause posting errors, before the statement posting process.

When you try to post a statement, the validation process can fail because of inconsistent data in the commerce transaction tables. Here are some examples of factors that cause these inconsistencies:

- The transaction total in the header table doesn't match the transaction total on the lines.
- The number of items that the header table specifies doesn't match the number of items in the transaction table.
- Taxes in the header table don't match the tax amount on the lines. 

If the statement posting process picks up inconsistent transactions, sales invoices and payment journals that you create can cause statement posting to fail. The **Validate store transactions** process prevents these problems by ensuring that only transactions that pass the transaction validation rules go to the transaction statement calculation process.

The following illustration shows the recurring daytime processes for uploading transactions, validating transactions, and calculating and posting transaction statements. It also shows the end of day processes for financial statement calculation and posting.

:::image type="content" source="./media/valid-checker-statement-posting-flow.png" alt-text="Screenshot of the recurring daytime processes for uploading transactions, validating transactions, and calculating and posting transaction statements.":::

## Store transaction validation rules

The **Validate store transactions** batch process checks the consistency of the commerce transaction tables, based on the following validation rules.

> [!NOTE]
> Validation rules will continue to be added in subsequent releases.

### Transaction header validation rules

The following table lists the transaction header validation rules that the system checks against the header of retail transactions before it passes those transactions to statement posting.

| Rule | Description |
|-------|-------------|
| Business date | This rule checks that the business date of the transaction is associated with an open fiscal period in the ledger. |
| Currency rounding | This rule checks that the transaction amounts are rounded according to the currency rounding rule. |
| Customer account | This rule checks that the customer you use in the transaction exists in the database. |
| Discount amount | This rule checks that the discount amount on the header equals the sum of discount amounts of the lines. |
| Fiscal document posting status (Brazil) | This rule checks that the fiscal document can be successfully posted. |
| Gross amount | This rule checks that the gross amount on the transaction header matches the net amount, including tax, of the transaction lines plus charges. |
| Net | This rule checks that the net amount on the transaction header matches the net amount, excluding tax, of the transaction lines plus charges. |
| Net + tax | This rule checks that the gross amount on the transaction header matches the net amount, excluding tax, of the transaction lines plus all taxes and charges. |
| Number of items | This rule checks that the number of items that is specified on the transaction header matches the sum of quantities on the transaction lines. |
| Payment amount | This rule checks that the payment amount on the transaction header matches the sum of all payment transactions. |
| Tax exempt calculation | This rule checks that the sum of the calculated amount and the exempted tax amount of charge lines equals the original calculated amount. |
| Tax included pricing | This rule checks that the **Tax is included in price** flag is consistent across the transaction header and the tax transactions. |
| Transaction not empty | This rule checks that the transaction contains lines, and that at least one line isn't voided. |
| Under/over payment | This rule checks that the difference between the gross amount and the payment amount isn't more than the maximum underpayment/overpayment configuration. |

### Transaction line validation rules

The following table lists the transaction line validation rules that the system checks against the line details of retail transactions before it passes those transactions to statement posting.

| Rule | Description |
|-------|-------------|
| Barcode | This rule checks that all item bar codes that the transaction lines use exist in the database. |
| Charge lines | This rule checks that the sum of the calculated amount and the exempted tax amount of charge lines equals the original calculated amount. |
| Gift card returns | This rule checks that the transaction doesn't include returns of gift cards. |
| Item variant | This rule checks that all items and all variants that the transaction lines use exist in the database. |
| Line discount | This rule checks that the line discount amount matches the sum of the discount transactions. |
| Line tax | This rule checks that the line tax amount matches the sum of the tax transactions. |
| Negative price | This rule checks that the transaction lines don't use negative prices. |
| Serial number controlled | This rule checks that the serial number is present on the transaction line for items that are serial number controlled. |
| Serial number dimension | This rule checks that the transaction doesn't provide a serial number if the item's serial number dimension is inactive. |
| Sign contradiction | This rule checks that the sign of the quantity and the sign of the net amount are the same on all transaction lines. |
| Tax exempt | This rule checks that the sum of the line item price and the exempted tax amount equals the original price. |
| Tax group assignment | This rule checks that the combination of the sales tax group and the item tax group produces a valid tax intersection. |
| Unit of measure conversions | This rule checks that the unit of measure of all lines has a valid conversion to the inventory unit of measure. |

## Enable the store transaction validation process

Configure the **Validate store transactions** job for periodic runs in Commerce headquarters (**Retail and Commerce \> Retail and Commerce IT \> POS posting**). The system schedules the batch job based on the store's organization hierarchy. Configure this batch process to run at the same frequency as your **P-Job** and **Transactional statement calculation** batch jobs.

## Results of the validation process

You can view the results of the **Validate store transactions** batch process on each retail store transaction. The process sets the **Validation status** field on the transaction record to **Successful**, **Error**, or **None**. The **Last validation time** field shows the date of the last validation run.

The following table describes each validation status.

| Validation status | Description |
|-------------------|-------------|
| Successful | All enabled validation rules pass. |
| Error | An enabled validation rule identifies an error. You can view more details about the error by selecting **Validation errors** on the Action Pane. |
| None | The transaction type doesn't require that validation rules be applied. |

:::image type="content" source="./media/valid-checker-validation-status-errors.png" alt-text="Screenshot of the Store transactions page showing the Validation status field and the Validation errors button.":::

Only transactions that have a validation status of **Successful** are included in the transactional statements. To view transactions that have a status of **Error**, review the **Cash and carry validation failures** tile in the **Store financials** workspace.

:::image type="content" source="./media/valid-checker-cash-carry-validation-failures.png" alt-text="Screenshot of tiles in the Store financials workspace.":::

For more information about how to fix cash and carry validation failures, see [Edit and audit cash and carry and cash management transactions](edit-cash-trans.md).

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
