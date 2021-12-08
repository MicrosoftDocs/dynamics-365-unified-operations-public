---
# required metadata

title: Retail transaction consistency checker
description: This topic describes the transaction consistency checker functionality in Dynamics 365 Commerce.
author: analpert
ms.date: 12/09/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: ed0f77f7-3609-4330-bebd-ca3134575216
ms.search.region: global
ms.search.industry: Retail
ms.author: josaw
ms.search.validFrom: 2019-01-15
ms.dyn365.ops.version: 10.0

---
# Validate store transactions for statement calculation

[!include [banner](includes/banner.md)]

This topic describes the store transaction validation functionality in Microsoft Dynamics 365 Commerce. The validation process identifies and marks transactions that will cause posting errors before they are picked up by the statement posting process.

When attempting to post a statement the process can fail due to inconsistent data in the commerce transaction tables. Examples of how these inconsistencies may be caused include:

- The transaction total on the header table does not match the transaction total on the lines.
- The number of items specified on the header table does not match with the number of items in the transaction table.
- Taxes on the header table do not match the tax amount on the lines. 

If inconsistent transactions are picked up by the statement posting process, sales invoices and payment journals can be created that will cause statement posting to fail. The **Validate store transactions** process prevents such issues by ensuring that only transactions that pass our transaction validation rules are passed to the transaction statement calculation process.

The following chart illustrates the posting processes including the **Validate store transactions** process.

![Statement posting process with transaction consistency checker.](./media/valid-checker-statement-posting-flow.png "Statement posting process with retail transaction consistency checker")

## Store transaction validation rules

The **Validate store transactions** batch process checks the consistency of the commerce transaction tables based on the following validation rules.

### Transaction header validation rules
Rules and validations checked against the header of retail transactions in advance of being passed to statement posting.
| Title             | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| Business date     | Validates the transaction business date is associated to an open fiscal period in the ledger. |
| Currency rounding | Validates the transaction amounts are rounded as per currency rounding rule.                       |
| Customer account  | Validates that the customer used in the transaction exists in the database.                        |
| Discount amount   | Validates the discount amount on the header is equal to the sum of discount amount of the lines. |
| Fiscal document posting status (Brazil) | Validates the fiscal document can be successfully posted. |
| Gross amount | Validates the gross amount on the transaction header matches the net amount including tax of the transaction lines plus charges. |
| Net | Validates the net amount on the transaction header matches the net amount excluding tax of the transaction lines plus charges. |
| Net + tax | Validates the gross amount on the transaction header matches the net amount excluding tax of the transaction lines plus all taxes and charges. |
| Number of items | Validates the number of items specified in the transaction header matches the sum of quantities in the transaction lines. |
| Payment amount | Validates the payment amount in the transaction header matches the sum of all payment transactions. |
| Tax exempt calculation | Validates the sum of the charge line calculated amount and exempted tax amount is equal to the original calculated amount. |
| Tax included pricing | Validates the **Tax is included in price** flag is consistent across the transaction header and the tax transactions. |
| Transaction not empty | Validates the transaction contains lines and that at least one of them is not voided. |
| Under/over payment | Validates the difference between the gross amount and the payment amount is not greater than the maximum under/over payment configuration. |

### Transaction line validation rules
Rules and validations checked against the line details of retail transactions in advance of being passed to statement posting.
| Title             | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| Barcode | Validates all item barcodes used in the transaction lines exist in the database. |
| Charge lines | Validates the sum of the charge lines calculated amount and exempted tax amount is equal to the original calculated amount. |
| Gift card returns | Validates there are no return of gift cards in the transaction. |
| Item variant | Validates all items and all variants used in the transaction lines exist in the database. |
| Line discount | Validates the line discount amount matches the sum of the discount transactions. |
| Line tax | Validates the line tax amount matches the sum of the tax transactions. |
| Negative price | Validates no negative prices are used in the transaction lines. |
| Serial number controlled | Validates the serial number is present in the transaction line for items that are serial number controlled. |
| Serial number dimension | Validates if the items serial number dimension is inactive, then the serial number should not be provided. |
| Sign contradiction | Validates sign of the quantity and the net amount are the same in all transaction lines. |
| Tax exempt | Validates the sum of the line item price and exempted tax amount is equal to the original price. |
| Tax group assignment | Validates the sales tax group and the item tax group combination results in a valid tax intersection. |
| Unit of measure conversions | Validates the unit of measure of all lines have valid conversions to the inventory unit of measure. |

## Enabling the store transactions validation process

Configure the **Validate store transactions** job located at **Retail and Commerce > Retail and Commerce IT > POS posting** for periodic runs. The batch job is scheduled based on store organization hierarchy. It is recommended that you configure this batch process to run at the same frequency as your **P-Job** and **Transactional statement calculation** batch jobs.

## Results of validation process

The results of the **Validate store transactions** batch process can be viewed on each retail store transaction. The **Validation status** field on the transaction record is set to **Successful**, **Error**, or **None** and the date of the last validation run appears on the **Last validation time** field.

| Validation Status | Description                                                                                        |
|-------------------|----------------------------------------------------------------------------------------------------|
| Successful | All enabled validation rules passed. |
| Error | An enabled validation rule has identified an error. View additional details by opening the **Validation errors** form. |
| None | Transaction type does not require validation rules to be applied. |

![Screenshot showing validation status and validation errors form.](./media/valid-checker-validation-status-errors.png "Retail transactions form showing validation status and the validation errors function.")

Only transactions that have a validation status of **Successful** will be pulled into the transactional statements. To view transactions that are in a state of **Error**, review the **Cash and carry validation failures** tile on the **Store financials** workspace.

![Screenshot showing store financials workspace.](./media/valid-checker-cash-carry-validation-failures.png "Store financials workspace tiles.")

For more information on how to resolve the Cash and carry validation failures, refer to the Edit and audit cash and carry transactions document.

> [!NOTE]
> Additional validation rules will continue to be added in subsequent releases.

## Additional resources
[Edit and audit cash and carry and cash management transactions](https://docs.microsoft.com/en-us/dynamics365/commerce/edit-cash-trans)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
