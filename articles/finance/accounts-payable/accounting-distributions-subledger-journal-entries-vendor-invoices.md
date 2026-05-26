---
title: Accounting distributions and journal entries for vendor invoices
description: Learn about accounting distributions, which are used to define how an amount will be accounted for on vendor invoices.
author: sunfzam
ms.author: Raynezou
ms.topic: how-to
ms.date: 05/26/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: VendEditInvoice
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 93dc608a-b5b4-4ec3-83c2-618e3d80a583
---

# Accounting distributions and journal entries for vendor invoices

[!include [banner](../includes/banner.md)]

Accounting distributions are used to define how an amount, the expense, tax, or charges are accounted for on a vendor invoice. Every amount that must be accounted for when the vendor invoice is journalized has one or more accounting distributions.

## Accounting distributions

On the **Vendor invoice** page, use the following buttons to view and, if needed, modify the accounting distributions for each amount on the vendor invoice.

- **Distribute amounts** – View and modify the accounting distributions for an individual line and any child lines. You can view and modify the accounting distributions for the child line directly from the **Sales tax transactions** page or the **Charges transactions** page.
  - Modify vendor invoice header amounts, such as charges or currency rounding amounts.
  - Modify vendor invoice line amounts.
- **View distributions** – View the accounting distributions for all lines on the document. You can't modify the accounting distributions from this view.
  - View header and line amounts.

If the vendor invoice references a purchase order, you can split and modify the accounting distributions for lines that contain an item that isn't stocked. If the vendor invoice line doesn't reference a purchase order line, you can delete an accounting distribution. You can't split or delete lines for charges, taxes, and line discounts. You can modify the ledger account, but you can't change the amounts or percentages.
> [!NOTE]
> If the parent line contains an item that's not stocked and the accounting distributions are split, the child line is automatically split to match the financial dimensions of the parent line. The accounting distributions for the child line can't be additionally split or deleted. Depending on the setup of the child line, you might be able to modify the ledger account for the accounting distributions of the child line.

## Distributing amounts

When you enter a vendor invoice, distribute each amount as follows.

| Type of vendor invoice line | Order of priority that determines where the main account is displayed from | Order of priority that determines which default financial dimension is displayed |
|---|---|---|
| Stocked product | 1. The accounting distribution for the purchase order line.<br>1. The **Main account** field when Purchase expenditure for product is selected on the **Posting** page. **Cost management > Ledger integration policies setup > Posting > Purchase order**. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the default financial dimension values on the vendor invoice. |
| A procurement category or a product that isn't stocked | 1. The accounting distribution for the purchase order line, if the vendor invoice line references a purchase order line.<br>1. The **Main account** field when Purchase expenditure for expense is selected on the **Posting** page. **Cost management > Ledger integration policies setup > Posting > Purchase order**. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. If the main account is an allocation account, use the default value from the allocation account definition.<br>1. Use the default financial dimension values on the vendor invoice.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Fixed asset | 1. The accounting distribution for the purchase order line, if the vendor invoice line references a purchase order line.<br>1. If **Acquisition** is selected in the **Transaction type** field on the **Vendor invoice** page, the **Main account** field when **Acquisition** is selected on the **Fixed asset posting profiles** page.<br>1. If **Acquisition adjustment** is selected on the **Transaction type** field, the **Main account** field when **Acquisition adjustment** is selected on the **Fixed asset posting profiles** page. | 1. Use the account distribution for the purchase order line, if the invoice line references a purchase order line.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Project defined on the vendor invoice line | 1. If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.<br>1. If you select **Balance** in the **Post costs - item** field in the **Project groups** page, the system uses the **Main account** field when you select **Cost** on the **Ledger posting setup** page.<br>1. If you select **Profit and loss** in the **Post costs - item** field in the **Project groups** page, the system uses the **Main account** field when you select **Cost - item** on the **Ledger posting setup** page. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line. |
| Line discount | 1. If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.<br>1. Use the **Main account** field when you select **Discount** on the **Posting** page.<br>1. If the posting profile doesn't define a main account for a discount, use the accounting distribution of the extended price on the purchase order line. | 1. If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.<br>1. Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.<br>1. Use the financial dimension values for the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Purchase charge, which you enter on the **Price and discount** tab of the purchase order line | 1. If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.<br>1. Use the accounting distribution of the extended price on the purchase order line. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line. |
| Line charge | 1. If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.<br>1. If you select **Ledger account** in the **Debit type** field on the **Charges code** page, use the **Debit Account** field on the **Charges code** page.<br>1. If you select **Item** in the **Debit type** field on the **Charges code** page, use the accounting distribution for the extended price on the purchase order line.<br>1. If you select **Customer/Vendor** in the **Debit type** field on the **Charges code** page, use the **Credit account** field on the **Charges code** page. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Tax, with the following condition:<br>- The **Apply U.S. taxation rules** option is selected on the **General ledger parameters** page. | 1. If the invoice line references a purchase order line, use the accounting distribution for the purchase order line.<br>1. Use the accounting distribution of the extended price or charge. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.<br>1. Use the financial dimension values from the vendor invoice line. |
| Tax, with the following conditions:<br>- The **Apply U.S. taxation rules** option is cleared on the **General ledger parameters** page.<br>- The **Use tax** field for the sales tax group is cleared on the **Sales tax groups** page. | 1. If the tax amount is recoverable, the **Sales tax receivable** field on the **Ledger posting groups** page.<br>1. If the tax amount isn't recoverable, the extended price or the accounting distribution for the charge. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the financial dimensions from the extended price or the accounting distributions for the charge on the vendor invoice line.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Tax, with the following conditions:<br>- The Apply U.S. taxation rules option is cleared on the **General ledger parameters** page.<br>- The **Use tax** field for the sales tax group is selected on the **Sales tax groups** page. | 1. If the tax amount is recoverable, the **Sales tax receivable** field on the **Ledger posting groups** page.<br>1. If the tax amount isn't recoverable, the **Use tax expense** field on the **Ledger posting groups** page. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the financial dimensions from the extended price or the accounting distributions for the charge on the vendor invoice line.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Header charge | 1. If **Ledger** account is selected in the **Debit type** field on the **Charges code** page, the **Debit account** field on the **Charges code** page.<br>1. If you select **Customer/Vendor** in the **Debit type** field on the **Charges code** page, use the **Credit account** field on the **Charges code** page. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. If the main account is an allocation account, use the default value from the allocation account definition.<br>1. Use the financial dimension default template values from the vendor invoice header.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |
| Header discount | 1. The **Main account** field for the **Vendor invoice discount posting type** on the **Accounts for automatic transactions** page. | 1. If the invoice line references a purchase order line, use the account distribution for the purchase order line.<br>1. Use the financial dimensions from the accounting distributions for the extended price on the vendor invoice line.<br>1. Use the financial dimension values from the vendor invoice line.<br>1. Use the default financial dimension values from the main account on the **Chart of accounts** page. |

## Distributing taxes

You can't create accounting distributions for taxes until you calculate the taxes. To calculate sales taxes, complete one of the following tasks on the **Vendor invoice** page:

- View the invoice total.
- View the sales tax.
- View the subledger journal.
- View accounting distributions for the complete vendor invoice.
- Place the vendor invoice on hold.
- Post the vendor invoice.

## Post document with distribution process splitting

When you process long invoice documents, you can optimize memory usage by activating the **Batch processing** feature.

1. To enable this feature, go to **Pending vendor invoice list**.
1. Select **Process > Setup > Batch**.
1. After you select **Post**, the **Post document with distribution process splitting** post job starts. This process is enabled when the **Enable vendor invoice posting to split distribution steps** feature is activated.

## Subledger journals for vendor invoices

Before you post a vendor invoice, view the full accounting entry of the invoice, which includes debits and credits, to verify that the invoice is going to the correct accounts. This view of the full accounting entry is called a subledger journal.

If the subledger journal entry is incorrect when you preview it before you journalize the vendor invoice, you can't modify the subledger journal entry. Instead, modify the accounting distributions or the posting profile. Use the accounting distributions to define one side of the accounting entry, the debit, or the credit. Create the offsetting subledger journal account entry by using the posting profiles, such as from the vendor account or tax.

## Split vendor invoice posting

During the posting of pending vendor invoices, the posting process involves a substantial transaction flowing into the source document account framework first and the General ledger subsequently. When the invoice data flows into the source document account framework, massive derivations and validations are applied before the subledger is updated. A performance and memory overflow issue might occur with invoices that contain a lot of lines.

The **Enable the vendor invoice to be posted in two stages** feature creates two batches for pending vendor invoice posting. The first batch post uses the original invoice posting except creating the subledger journals. The second batch posting creates subledger journals to generate accounting. After the second batch is posted, transferring the subledger to general ledger can be done. This reduces the likelihood of memory overflow and enhance overall performance when the invoice contains thousands of lines. When posting pending vendor invoices has dependencies on other modules or subsequent processes, the original invoice posting process is used.

The following situations use the original posting process:

- Prepayment invoice posting
- Invoice posting with prepayment application
- Invoice posting with budget control enabled
- Project invoice posting
- PO/invoice with Terms of payment of cash
- Invoice posting with Accounts payable parameter autosettlement enabled

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
