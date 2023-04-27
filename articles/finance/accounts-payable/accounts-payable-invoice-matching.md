---
# required metadata

title: Accounts payable invoice matching overview
description: Accounts payable invoice matching is the process of matching vendor invoice, purchase order, and product receipt information.
author: sunfzam
ms.date: 07/25/2019
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendInvoicePostingHistory
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["27361", "intro-internal"]
ms.assetid: 9f3dace7-05d8-4974-8f85-aca2e224876c
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Accounts payable invoice matching overview

[!include [banner](../includes/banner.md)]

Accounts payable invoice matching is the process of matching vendor invoice, purchase order, and product receipt information.

When matching documents, differences among these documents are called matching discrepancies. Matching discrepancies are compared with the tolerances that are specified. If a matching discrepancy exceeds the tolerance percentage or amount, match variance icons are displayed on the Vendor invoice page and on the Invoice history and matching details page. 

For example, you enter a purchase order with one line item for 1,000 batteries at a price of 1.00 each. The purchase order is approved and submitted to the vendor. The vendor ships 1,000 batteries, and you enter a product receipt for 1,000 batteries at a price of 1.00 each. The inventory cost for the batteries is updated with this price. 

An invoice arrives for 1,000 batteries at a price of 1.10 each. Your legal entity policy allows a 5 percent net unit price tolerance for this category of item. A price of 1.05 would be acceptable, but 1.10 is not. When you enter the invoice information, a price matching discrepancy is identified and you can save the invoice until the discrepancy is resolved.

You can use the following types of **Accounts payable invoice matching**:

-   **Invoice totals matching** – Match the total amounts on the invoice to the total amounts on the purchase order. This type of invoice matching includes the least amount of detail, so you can use this option to set up controls that minimize the staff time that is required to review invoice matching information.
-   **Two-way matching** – Match the price information on the invoice to the price information on the purchase order.
-   **Three-way matching** – Match the price information on the invoice to the price information on the purchase order. Also match the quantity information on the invoice to the quantity information on the product receipts that are selected for the invoice.
-   **Charges matching** – Match the charges information (amounts) on the invoice to the charges information (amounts) on the purchase order.

> [!NOTE]
> Other forms of invoice validation can be done using vendor invoice policies. 

Two-way matching and three-way matching always match price information by the unit price. You can also configure these matching policies to match price information by the price total.
-   **Net unit price matching** – Match price information for two-way matching or three-way matching by comparing the net unit price for each line on the invoice with the corresponding net unit price on the purchase order. The net unit price is determined by the following formula: Net amount of the line / Quantity of the line
-   **Price totals matching** – Match price information for two-way matching or three-way matching by comparing the net amount (price total) for each line on the invoice with the corresponding net amount on the purchase order. The net amount is determined by the following formula: *(Unit price \* Line quantity) + Line charges - Line discounts*. When matching price totals by percentage, the transaction currency values are compared. When matching price totals by amount, the accounting currency values are compared. When you partially invoice a purchase order line, the validation of price-total matching occurs on the last invoice for that line. 

Typically, invoice matching calculations are automatically performed when you edit vendor invoices on the **Vendor invoice** page. Alternatively, invoice matching can be performed on demand, as needed. Invoice matching on demand is controlled for the legal entity by the **Automatically update invoice** header status on the **Accounts payable parameters** page on the **Invoice validation** tab. Invoice matching can also be performed as part of an invoice review process. You can view the results of invoice matching on the **Vendor invoice** page and related invoice matching pages.

## Invoice totals matching
You can use invoice totals matching to help make sure that total invoice amounts do not deviate from expected amounts by more than an acceptable variance. Six totals are compared on the **Invoice totals matching details** page, as shown in the following table. If the allowable tolerance for invoice totals matching is 20%, the 100% variance percentage for the total discount amount is considered a matching discrepancy.

| Total field    | Actual invoice total | Expected invoice total | Variance percentage | Match status |
|----------------|----------------------|------------------------|---------------------|--------------|
| Balance        | 495.00               | 495.00                 | 0%                  | Passed       |
| Total discount | 0.00                 | 9.90                   | 100%                | Failed       |
| Charges        | 64.90                | 64.90                  | 0%                  | Passed       |
| Sales tax      | 139.98               | 137.50                 | 2%                  | Passed       |
| Round-off      | 0.00                 | 0.00                   | 0%                  | Passed       |
| Invoice amount | 699.88               | 687.50                 | 2%                  | Passed       |

Invoice totals matching is controlled for the legal entity by the **Match invoice totals** toggle on the **Accounts payable parameters** page. Matching is performed on the expected invoice totals and the actual invoice totals. The expected invoice totals are calculated based on the prices, charges, and sales tax information from the purchase order and the quantities from the invoice.

## Two-way, price totals matching
Use two-way matching to help make sure that the variance between the price information on the purchase order and the invoice is within acceptable tolerances. You can compare price information for the net amount of each line on the invoice, and all pending and previously posted invoice lines, with the net amount of the corresponding purchase order line. This is called price totals matching. 

Price totals matching can be based on a percentage, an amount, or a percentage and amount. 

If a purchase price total tolerance percentage is specified, five fields are compared, as shown in the following table. Because the purchase price total tolerance percentage is 10%, the price total variance percentage of 50% represents a matching discrepancy.

| Match status | Invoice net amount | Expected net amount | Unmatched purchase price total (variance amount) | Unmatched purchase price total percentage (variance percentage) | Purchase price total tolerance percent |
|--------------|--------------------|---------------------|-----------------------------------------|--------------------------------|---------------------------|
| Passed       | 105.00             | 100.00              | 5.00                                             | 5%                             | 10%                 |
| Failed       | 150.00             | 100.00              | 50.00                                            | 50%                            | 10%              |

If a purchase price total tolerance amount is specified, five fields are compared, as shown in the following table. Because the purchase price total tolerance amount is 100.00, the price total variance amount of 105.00 represents a matching discrepancy.

| Match status | Invoice net amount | Expected net amount | Unmatched purchase price total (variance amount) | Unmatched purchase price total in accounting currency (variance amount) | Purchase price total tolerance |
|--------------|--------------------|---------------------|---------------------------------------|-------------------------------|--------------------------------|
| Passed       | 150.00             | 100.00              | 50.00                                            | 50.00                    | 100.00                 |
| Failed       | 205.00             | 100.00              | 105.00                                           | 105.00                  | 100.00                 |

If price totals matching is set up with a percentage tolerance and a tolerance amount, sometimes referred to as a not-to-exceed amount, both tolerances are considered when evaluating whether a line has a matching discrepancy. If either the percentage or the amount exceeds the tolerance, as shown in the 150.00 and 205.00 lines in the following table, the line has a matching discrepancy.

| Match status | Invoice net amount | Expected net amount | Unmatched purchase price total percentage (variance percentage) | Purchase price total tolerance percent | Unmatched purchase price total in accounting currency (variance amount) | Purchase price total tolerance |
|--------------|--------------------|---------------------|-----------------------------|------------------|-------------------------|--------------------------------|
| Passed       | 105.00             | 100.00              | 5%                     | 10%                         | 5.00           | 100.00                         |
| Failed       | 150.00             | 100.00              | 50%                   | 10%                     | 50.00            | 100.00                         |
| Failed       | 205.00             | 100.00              | 105%                 | 10%                      | 105.00                                  | 100.00       |

Two-way matching is controlled for the legal entity by the **Line matching policy** field on the **Accounts payable parameters** page. Depending on the selection in the **Allow matching policy override** field, you can select two-way matching for a specific vendor, item, or item and vendor combination on the **Matching policy** page, and for a specific purchase order on the **Purchase order** page.

Price totals matching is controlled for the legal entity by the **Match price totals** field on the **Accounts payable parameters** page. The purchase price total tolerance percentage and tolerance amount (not-to-exceed amount) are also specified on that page.

## Two-way, net unit price matching
Use two-way matching to help make sure that the variance between the price information on the purchase order and the invoice is within acceptable tolerances. You can compare price information for the net unit price of each item on the invoice. This is called net unit price matching. 

Nine line amounts are compared on the **Invoice matching details** page, as shown in the following table. If the allowable price tolerance for net unit price matching is 10%, the 22.61% variance for the net unit price is considered a matching discrepancy.

| Line field                    | Invoice value | Purchase order value | Variance percentage | Match status |
|-------------------------------|---------------|----------------------|---------------------|--------------|
| Unit price                    | 55.40         | 55.38                | 0%                  | Passed       |
| Price unit                    | 1.00          | 1.00                 | 0%                  | Passed       |
| Charges on purchases          | 50.00         | 0.00                 | 100%                | Failed       |
| Discount                      | 0.00          | 0.00                 | 0%                  | Passed       |
| Discount percent              | 0.00          | 0.00                 | 0%                  | Passed       |
| Multiline discount            | 0.00          | 0.00                 | 0%                  | Passed       |
| Multiline discount percentage | 0.00          | 0.00                 | 0%                  | Passed       |
| Net amount                    | 271.60        | 221.52               | 22.61%              | Failed       |
| Net unit price                | 67.9000       | 55.3800              | 22.61%              | Failed       |

Two-way matching is controlled for the legal entity by the **Line matching policy** field on the **Accounts payable parameters** page. Depending on the selection in the **Allow matching policy override** field, you can select two-way matching for a specific vendor, item, or item and vendor combination on the **Matching policy** page, and for a specific purchase order on the **Purchase order** page. 

Net unit price matching is controlled for the legal entity by the **Enable invoice matching validation** field on the **Accounts payable parameters** page. The net unit price tolerance percentages can be configured for items, item groups, vendors, vendor groups, item and vendor combinations, or legal entity by using the **Price tolerances** page.

## Two-way, price totals matching and net unit price matching
You can use price totals matching and net unit price matching together. This example assumes the following configuration:

-   The net unit price tolerance for the USB Drive item is 10%.
-   The price totals matching tolerance for the legal entity is 15% or 500.00.

The purchase order contains the following line.

| Item number | Quantity | Unit price | Net amount |
|-------------|----------|------------|------------|
| USB Drive   | 1,000    | 10.00      | 10,000.00  |

Three invoices are entered, as shown in the following table. There is an invoice matching discrepancy for Invoice 3 because the variance of 1,880.00 exceeds the purchase price total tolerance amount of 500.00. For price totals matching, the invoice net amount includes all previously posted invoices in addition to the invoice that you are currently working with.

| Item number          | Quantity | Unit price | Net amount | Price match | Price total match |
|----------------------|----------|------------|------------|-------------|-------------------|
| Invoice 1: USB Drive | 800      | 10.80      | 8,640.00   | Passed      | Passed            |
| Invoice 2: USB Drive | 100      | 10.80      | 1,080.00   | Passed      | Passed            |
| Invoice 3: USB Drive | 200      | 10.80      | 2,160.00   | Passed      | Failed            |
| Total                |          |            | 11,880.00  |             |                   |

## Three-way matching

Use three-way matching to help make sure that the variance between the price information on the purchase order and the invoice is within acceptable tolerances, and to make sure that the quantity on the invoice matches the quantity on the corresponding product receipts.

The same line amounts are compared on the Invoice matching details page as for two-way matching. In addition, the quantity on the invoice is matched to product receipt quantities that have been received. If the invoice quantity differs from the matched product receipt quantity, a quantity matching error exists.

| Line field                    | Invoice value | Purchase order value | Variance percentage | Match status |
|-------------------------------|---------------|----------------------|---------------------|--------------|
| Unit price                    | 55.40         | 55.38                | 0%                  | Passed       |
| Price unit                    | 1.00          | 1.00                 | 0%                  | Passed       |
| Charges on purchases          | 50.00         | 0.00                 | 100%                | Failed       |
| Discount                      | 0.00          | 0.00                 | 0%                  | Passed       |
| Discount percent              | 0.00          | 0.00                 | 0%                  | Passed       |
| Multiline discount            | 0.00          | 0.00                 | 0%                  | Passed       |
| Multiline discount percentage | 0.00          | 0.00                 | 0%                  | Passed       |
| Net amount                    | 271.60        | 221.52               | 22.61%              | Failed       |
| Net unit price                | 67.9000       | 55.3800              | 22.61%              | Failed       |

| Line field                     | Invoice value | Match status |
|--------------------------------|---------------|--------------|
| Invoice quantity               | 4.00          |              |
| Total product receipts matched | 0.00          | Failed       |

Three-way matching is controlled for the legal entity by the **Line matching policy** field on the **Accounts payable parameters** page. Depending on the selection in the **Allow matching policy override** field, you can select three-way matching for a specific vendor, item, or item and vendor combination on the **Matching policy** page, and for a specific purchase order on the **Purchase order** page.

## Charges matching
You can use charges matching to help make sure that charges amounts do not deviate from expected amounts by more than an acceptable variance percentage. The total amounts for each charges code that applies to the invoice and purchase order are compared in the **Compare charges values - Invoice:** page, as shown in the following table. If the allowable tolerance for the charges code is 25%, the 99,999,999,999.99% variance percentage for the **License charges code** is considered a matching discrepancy.

> [!NOTE] 
> A variance percentage of 99,999,999,999.99% means that the expected amount based on the purchase order is zero and the actual amount on the invoice is a positive value. 

| Charges match status | Invoice charges code | Actual total calculated value | Expected total calculated value | Variance amount | Variance percentage | Tolerance percentage |
|----------------------|----------------------|-------------------------|-------------------------|-----------------|---------------------|----------------------|
| Failed               | License              | 25                            | 0                               | 25              | 99,999,999,999.99%  | 25%       |
| Passed               | Freight              | 200                           | 200                             | 0               | 0%                  | 25%       |
| Failed               | Expedite             | 4                             | 2                               | 2               | 100%                | 25%       |

Charges matching is controlled for the legal entity by the **Match charges** toggle on the **Accounts payable parameters** page. You can set up variance tolerance percentages for charges on the **Charges tolerances** page.

> [!NOTE]
> Charges matching is performed only on charges codes for which the **Compare purchase order and invoice values** toggle is selected on the **Charges code** page.

## Related functionality
Vendor invoices are often based on product receipts that represent actual shipments, instead of on purchase orders. Sometimes, the invoiced amounts don't match the purchase order amounts, and sometimes the shipped quantities don't match the invoiced quantities. You can help manage this information in the following ways:
-   Create a vendor invoice based on product receipts. Product receipts are automatically suggested for invoices, and you can select which product receipts to use. You can also select specific product receipt line items from multiple purchase orders, if you have to.
-   View and approve quantity differences between the invoiced quantity on the invoice and the received quantity on the product receipt. If there is a difference, you can save the invoice and later match it to a different product receipt, or change the invoiced quantity to match the received quantity.
-   Enter invoice amounts that were not included on the original purchase order, so that the invoice information matches the invoice that you received from the vendor. You can compare the charges for purchase orders with the charges for invoices. If necessary, you can add charges to invoices and allocate them to invoice lines.
-   View and approve price match discrepancies between the invoice net unit price and the purchase order net unit price. You can set up price tolerance percentages for legal entities, vendors, and items. If the vendor invoice line price isn't in the acceptable price tolerance, you can save the invoice until it's approved for posting, or until you receive a correction from the vendor.

For more information, see [Three-way matching policies](three-way-matching-policies.md) and [Set up Accounts payable invoice matching validation](tasks/set-up-accounts-payable-invoice-matching-validation.md). 






[!INCLUDE[footer-include](../../includes/footer-banner.md)]
