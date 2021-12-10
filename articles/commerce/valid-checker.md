---
# required metadata

title: Validate store transactions for statement calculation
description: This topic describes the store transaction validation functionality in Microsoft Dynamics 365 Commerce.
author: analpert
ms.date: 12/10/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgriffin
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: analpert
ms.search.validFrom: 2019-01-15
ms.dyn365.ops.version: 10.0

---
# Validate store transactions for statement calculation

[!include [banner](includes/banner.md)]

This topic describes the store transaction validation functionality in Microsoft Dynamics 365 Commerce. The validation process identifies and marks transactions that will cause posting errors before they are picked up by the statement posting process.

When attempting to post a statement the validation process can fail due to inconsistent data in the commerce transaction tables. Examples of how these inconsistencies can be caused include:

- The transaction total on the header table does not match the transaction total on the lines.
- The number of items specified on the header table does not match the number of items in the transaction table.
- Taxes on the header table do not match the tax amount on the lines. 

If inconsistent transactions are picked up by the statement posting process, sales invoices and payment journals can be created that will cause statement posting to fail. The **Validate store transactions** process prevents such issues by ensuring that only transactions that pass our transaction validation rules are passed to the transaction statement calculation process.

The following chart illustrates the posting processes including the **Validate store transactions** process.

![Statement posting process with retail transaction consistency checker](./media/valid-checker-statement-posting-flow.png)

## Store transaction validation rules

The **Validate store transactions** batch process checks the consistency of the commerce transaction tables based on the following validation rules.

### Transaction header validation rules

The following table lists transaction header validation rules that are checked against the header of retail transactions in advance of being passed to statement posting.

| Title             | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| Business date     | Validates that the transaction business date is associated to an open fiscal period in the ledger. |
| Currency rounding | Validates that the transaction amounts are rounded as per currency rounding rule.                       |
| Customer account  | Validates that the customer used in the transaction exists in the database.                        |
| Discount amount   | Validates that the discount amount on the header is equal to the sum of discount amount of the lines. |
| Fiscal document posting status (Brazil) | Validates that the fiscal document can be successfully posted. |
| Gross amount | Validates that the gross amount on the transaction header matches the net amount including tax of the transaction lines plus charges. |
| Net | Validates that the net amount on the transaction header matches the net amount excluding tax of the transaction lines plus charges. |
| Net + tax | Validates that the gross amount on the transaction header matches the net amount excluding tax of the transaction lines plus all taxes and charges. |
| Number of items | Validates that the number of items specified in the transaction header matches the sum of quantities in the transaction lines. |
| Payment amount | Validates that the payment amount in the transaction header matches the sum of all payment transactions. |
| Tax exempt calculation | Validates that the sum of the charge line calculated amount and exempted tax amount is equal to the original calculated amount. |
| Tax included pricing | Validates that the **Tax is included in price** flag is consistent across the transaction header and the tax transactions. |
| Transaction not empty | Validates that the transaction contains lines and that at least one of them is not voided. |
| Under/over payment | Validates that the difference between the gross amount and the payment amount is not greater than the maximum under/over payment configuration. |

### Transaction header validation rules

The following table lists transaction header validation rules that are checked against the line details of retail transactions in advance of being passed to statement posting.

| Title             | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| Barcode | Validates that all item barcodes used in the transaction lines exist in the database. |
| Charge lines | Validates that the sum of the charge lines calculated amount and exempted tax amount is equal to the original calculated amount. |
| Gift card returns | Validates that there are no return of gift cards in the transaction. |
| Item variant | Validates that all items and all variants used in the transaction lines exist in the database. |
| Line discount | Validates that the line discount amount matches the sum of the discount transactions. |
| Line tax | Validates that the line tax amount matches the sum of the tax transactions. |
| Negative price | Validates that no negative prices are used in the transaction lines. |
| Serial number controlled | Validates that the serial number is present in the transaction line for items that are serial number controlled. |
| Serial number dimension | Validates that if the items serial number dimension is inactive, then the serial number should not be provided. |
| Sign contradiction | Validates that the sign of the quantity and the net amount are the same in all transaction lines. |
| Tax exempt | Validates that the sum of the line item price and exempted tax amount is equal to the original price. |
| Tax group assignment | Validates that the sales tax group and the item tax group combination results in a valid tax intersection. |
| Unit of measure conversions | Validates that the unit of measure of all lines have valid conversions to the inventory unit of measure. |

## Enable the store transactions validation process

Configure the **Validate store transactions** job located in Commerce headquarters at **Retail and Commerce \> Retail and Commerce IT \> POS posting** for periodic runs. The batch job is scheduled based on store organization hierarchy. It is recommended that you configure this batch process to run at the same frequency as your **P-Job** and **Transactional statement calculation** batch jobs.

## Results of the validation process

The results of the **Validate store transactions** batch process can be viewed on each retail store transaction. The **Validation status** field on the transaction record is set to **Successful**, **Error**, or **None** and the date of the last validation run appears on the **Last validation time** field.

The following table lists and describes each validation status state.

| Validation Status | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| Successful | All enabled validation rules passed. |
| Error | An enabled validation rule has identified an error. You can view additional details of the error by opening the **Validation errors** form. |
| None | Transaction type does not require validation rules to be applied. |

![Retail transactions form showing validation status and the validation errors function](./media/valid-checker-validation-status-errors.png)

Only transactions that have a validation status of **Successful** will be pulled into the transactional statements. To view transactions that are in a state of **Error**, review the **Cash and carry validation failures** tile on the **Store financials** workspace.

![Store financials workspace tiles](./media/valid-checker-cash-carry-validation-failures.png)

For more information on how to resolve cash and carry validation failures, see [Edit and audit cash and carry and cash management transactions](edit-cash-trans.md).

> [!NOTE]
> Additional validation rules will continue to be added in subsequent releases.

## Additional resources

[Edit and audit cash and carry and cash management transactions](edit-cash-trans.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
