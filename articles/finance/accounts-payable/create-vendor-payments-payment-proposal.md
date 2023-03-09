---
# required metadata

title: Create vendor payments by using a payment proposal
description: This article provides an overview of the payment proposal options and includes some examples that show how payment proposals work. 
author: abruer
ms.date: 04/04/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: LedgerJournalTransVendPaym
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 14312
ms.assetid: 585d5b0b-1b79-4a03-ab18-528918070377
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Create vendor payments by using a payment proposal

[!include [banner](../includes/banner.md)]

This article provides an overview of the payment proposal options and includes some examples that show how payment proposals work. Payment proposals are often used to create vendor payments, because the query can be used to quickly select vendor invoices for payment, based on criteria such as the due date and cash discount. 

Organizations often use payment proposals to create vendor payments, because the payment proposal query can be used to quickly select vendor invoices for payment, based on the due date, cash discount, and other criteria. 

The payment proposal query contains various tabs, each of which has different options for selecting invoices to pay. The **Parameter** tab contains options that a majority of organization use most often. On the **Records to include** FastTab, you can specify which invoices or vendors to include for payment by defining ranges for various characteristics. For example, if you want to pay only a specific range of vendors, you can define a filter for the vendor range. This functionality is often used to select invoices for a specific of method of payment. For example, if you define a filter where **Method of payment** = **Check**, only invoices that have that method of payment are selected for payment, provided that they also meet other criteria that are specified in the query. The **Advanced parameters** tab contains additional options, some of which might not be relevant to your organization. For example, this tab contains the options for paying invoices for centralized payments.

## Parameters
-   **Select invoices by** – Invoices within the date range that is specified by the **From date** and **To date** fields can be selected by due date, cash discount date, or both. If you use the cash discount date, the system first looks for invoices that have a cash discount date between the from date and to date. The system then determines whether the invoice is eligible for the cash discount by using the session date to make sure that the cash discount date hasn’t already passed.
-   **From date** and **To date** – Invoices that have a due date or cash discount date within this date range are selected for payment.
-   **Minimum payment date** – Enter the minimum payment date. For example, the **From date** and **To date** fields specify a range from September 1 to September 10, and the minimum payment date is September 5. In this case, all invoices that have a due date from September 1 to September 5 have a payment date of September 5. However, all invoices that have a due date from September 5 to September 10 have a payment date that is equal to the due date of each invoice.
-   **Amount limit** – Enter the maximum total amount for all payments.
-   **Create payments without invoice preview** – If this option is set to **Yes**, payments will be created immediately on the **Vendor payments** page. The **Payment proposal** page will be skipped. Therefore, payments will be created more quickly. Payments can still be modified from the **Vendor payments** page. Alternatively, you can return to the **Payment proposal** page by using the **Edit invoices for select payment** button.

## Advanced options
- **Check vendor balance** – If this option is set to **Yes**, the system verifies that a vendor doesn’t have a debit balance before any invoice is paid. If a vendor does have a debit balance, no payment is created. For example, the vendor might have credit memos, or payments that have been posted but haven't been settled yet. In these cases, the vendor should not be paid. Instead, the credit memos or payments should be settled against the outstanding invoices.
- **Delete negative payments** – This option works differently, depending on whether payments are made for individual invoices or for the sum of invoices that meet the payment criteria. This behavior is defined on the method of payment.
- **Payment for each invoice** – If the **Delete negative payments** option is set to **Yes**, and an unsettled invoice and payment exist for a vendor, only the invoice is selected for payment. The existing payment isn't settled against the invoice. If the **Delete negative payments** option is set to **No**, and an invoice and a payment aren't settled, both the invoice and the payment are selected for payment. A payment is created for the payment, and a refund (negative payment) is created for the payment.
- **Payment for sum of invoices** – If the **Delete negative payments** option is set to **Yes**, and an unsettled invoice and payment exist for a vendor, both the unsettled invoice and the payment are selected for payment, and the amounts are added together to produce the total payment amount. The only exception occurs if the sum results in a refund. In this case, neither the invoice nor the payment is selected. If the **Delete negative payments** option is set to **No**, and an invoice and a payment aren't settled, both the invoice and the payment are selected for payment, and the amounts are added together to produce the total payment amount.
- **Print report only** – Set this option to **Yes** to see the results of the payment proposal on a report, but without creating any payments.
- **Include vendor invoices from other legal entities** – If your organization has a centralized process for payment, and the payment proposal should include invoices from other legal entities that are included in the search criteria, set this option to **Yes**.
- **Propose separate vendor payment per legal entity** – If this option is set to **Yes**, a separate payment is created for each legal entity per vendor. The vendor on the payment is the vendor from the invoice from each legal entity. If this option is set to **No**, and the same vendor has invoices in multiple legal entities, one payment is created for the total amount of the selected invoices. The vendor on the payment is the vendor in the current legal entity. If the vendor account doesn’t exist in the current legal entity, the vendor account of the first invoice that must be paid is used.
- **Payment currency** – This field specifies the currency that all payments are created in. If a currency isn’t defined, each invoice is paid in the currency of the invoice.
- **Payment weekday** – Enter the day of the week when the payment should be made, this field is used only if the method of payment is set to **Week**. The amount of invoices for payment are totaled on the specified day of the week for payment.
- **Offset account type** and **Offset account** – Set these fields to define a specific account type (such as **Ledger** or **Bank**) and offset account (such as a specific bank account). The method of payment for the invoice defines the default offset account type and offset account, but you can use these fields to override the default values.
- **Summarized payment date** – This is only used when the **Period** field on the method of payment is set to **Total**. If a date is defined, all payments are created on this date. The **Minimum payment date** field is ignored.
- **Additional filters** – On the **Records to include** FastTab, you can define additional ranges of criteria. For example, if you want to pay only a range of vendors, you can define a filter for the vendor range. This functionality is often used to select invoices for a specific of method of payment. For example, if you define a filter where **Method of payment** = **Check**, only invoices that have that method of payment are selected for payment, provided that they also meet other criteria that are specified in the query.

## Scenarios

| Vendor | Invoice | Invoice date | Invoice amount | Due date | Cash discount date | Cash discount amount |
|--------|---------|--------------|----------------|----------|--------------------|----------------------|
| 3050   | 1001    | June 15      | 500.00         | July 15  | June 29            | 10.00                |
| 3050   | 1002    | June 20      | 600.00         | July 20  | July 4             | 12.00                |
| 3075   | 1003    | June 15      | 250.00         | June 29  |                    | 0.00                 |
| 3100   | 1004    | June 17      | 100.00         | July 17  | July 1             | 1.00                 |

On July 1, April pays vendors and uses a payment proposal to complete this task more efficiently.

### Option 1: By cash discount

April selects **Cash discount** as the proposal type and enters a date range of June 26 to July 10. The following invoices are included in the proposal:

-   1002, because the discount date of July 4 is in the range of payment dates.
-   1004, because the discount date of July 1 is in the range of payment dates.

The following invoices aren't included in the proposal:

-   1001, because the discount date of June 29 has already expired, so this invoice is no longer eligible for the cash discount.
-   1003, because this invoice doesn't have a discount date.

### Option 2: By due date

April selects **Per due date** as the proposal type and enters a date range of June 26 to July 10. The following invoices are included in the proposal:

-   1003, because the due date of June 29 is in the range of payment dates.

The following invoices aren't included in the proposal:

-   1001, because the due date of July 15 is outside the range of payment dates.
-   1002, because the due date of July 20 is outside the range of payment dates.
-   1004, because the due date of July 17 is outside the range of payment dates.

### Option 3: By due date and cash discount

April selects **Due date and cash discount** as the proposal type and enters a date range of June 26 to July 10. The following invoices are included in the proposal:

-   1003, because the due date of June 29 is in the range of payment dates.
-   1002, because the discount date of July 4 is in the range of payment dates.
-   1004, because the discount date of July 1 is in the range of payment dates.

The following invoices aren't included in the proposal:

-   1001, because the discount date of June 29 has already expired, so this invoice is no longer eligible for the cash discount, and the due date of July 15 is also outside the date range.

## Country specific considerations
### Norway

#### Dimension control

Dimension control allows you to control grouping of generated lines by payment proposal and set default dimensions based on financial dimensions used for the applied invoices. Under Norwegian country context for each method of payment there is financial dimension tab where you can activate dimension control as well as enable grouping for each dimension. Possible options are:

-   **Dimension control** field is disabled. The payment proposal behaves as for any other country.
-   **Dimension control** field is activated without further defining the dimensions. The payment proposal will be created without taking dimensions into consideration. The created transaction inherits no dimensions from the applied entry.
-   **Dimension control** field is activated and the further dimensions are enabled. Now you define how the dimensions will be copied to the journal. For example: • Select the **BusinessUnit** check box to create a payment proposal per business unit for the method of payment, • Select the **CostCenter** check box to create a payment proposal per cost center for the method of payment

>[!NOTE]
> If you select more than one dimension in the third option, a payment proposal is created for the dimension combination.

#### Bank account selection

You can define a standard debiting payment account per method of payment regardless country context. This will be set in payment lines generated by a proposal. With the bank account feature, you can define multiple debiting bank accounts managed by dimension and currency or a combination of these to use different debiting bank accounts, depending on each combination. You can set up these combinations in **Methods of payments** page by using the **Bank accounts** button available for each method of payment with **Posting account type** = **Bank**.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]
