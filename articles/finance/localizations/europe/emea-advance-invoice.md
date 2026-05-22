---
title: Advance invoices for Eastern Europe
description: Learn about advance invoices for Eastern Europe, which are documents that you create for customers or vendors. It states the amount that must be prepaid.
author: prabhatb
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/21/2026
ms.reviewer: johnmichalak
ms.search.form: CustParameters
audience: Application User
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland
ms.dyn365.ops.version: Version 1611
ms.search.validFrom: 2016-11-30
---

# Advance invoices for Eastern Europe

[!include [banner](../../includes/banner.md)]

This article provides information about advance invoices for Eastern Europe. An advance invoice is a document that you can create for a customer or vendor. It states the amount that must be prepaid on a sales order. 

> [!NOTE]
> Another option is to use the prepayment invoice functionality. As of Microsoft Dynamics 365 Finance version 10.0.28, you can use this functionality by going to **Accounts payable** &gt; **Setup** &gt; **Parameters** &gt; **Ledger and sales tax** and setting the **Use prepayment invoice** option on the **Prepayment invoice** FastTab to **Yes**. For more information, see [Prepayment invoices vs. prepayments](../../accounts-payable/prepayments-invoices-vs-prepayments.md).

Advance invoice functionality lets you perform the following tasks:

- Issue advance invoices to customers, and track the status of those advance invoices (**Open**, **Partially paid**, or **Closed**).
- *For Poland only:* Post advance invoice transactions and value-added tax (VAT) transactions.
- Automatically generate payment journal lines, based on an advance invoice.
- Link prepayments that are received from customers to advance invoices (either before or after you post the prepayment).
- Change the VAT posting in posted prepayments (that is, convert a prepayment to a payment or a payment to a prepayment, or change the posting date, tax rate, or amount).
- *For the Czech Republic only:* Create a tax document for the VAT liable delivery.

This article contains the following sections:

- [Advance invoices for Poland](#advance-invoices-for-poland)
- [Set up Accounts receivable for advance invoices](#set-up-accounts-receivable-for-advance-invoices)
- [Create a customer advance invoice](#create-a-customer-advance-invoice)
- [VAT on advance invoices](#vat-on-advance-invoices)
- [Link an advance invoice to a sales order or a free text invoice](#link-an-advance-invoice-to-a-sales-order-or-a-free-text-invoice)
- [Create a customer advance invoice from a sales order](#create-a-customer-advance-invoice-from-a-sales-order)
- [Create a customer advance invoice from a free text invoice](#create-a-customer-advance-invoice-from-a-free-text-invoice)
- [Print an advance invoice](#print-an-advance-invoice)
- [Create a payment proposal from an advance invoice](#create-a-payment-proposal-from-an-advance-invoice)
- [Link a prepayment to an advance invoice](#link-a-prepayment-to-an-advance-invoice)
- [Link an advance invoice to a prepayment](#link-an-advance-invoice-to-a-prepayment)
- [Advance invoice credit notes](#advance-invoice-credit-notes)
- [Tax documents for the Czech Republic](#tax-documents-for-the-czech-republic)
- [Set up Accounts payable for advance invoices](#set-up-accounts-payable-for-advance-invoices)
- [Create a vendor advance invoice](#create-a-vendor-advance-invoice)
- [Use the Advance invoice and Prepayment handling functionality](#use-the-advance-invoice-and-prepayment-handling-functionality)
- [Reversing sales tax amounts for Czech Republic](#reversing-sales-tax-amounts-for-czech-republic)

## Advance invoices for Poland

Polish companies that receive prepayments must create an invoice for prepayments for the customer. Post this advance invoice to the general ledger. It's a mandatory document for VAT tax purposes. Report the tax calculated on the advance invoice to the tax authority.

When you perform the final sale of goods, specify the advance invoice on the sales invoice. Include prepayments in the total amount of sales.

When you post the sales invoice, reverse the settled advance invoice. Settle the original advance invoice with an advance invoice reversal.

## Set up Accounts receivable for advance invoices

1. On **Accounts receivable parameters**, on the **Updates** tab, on the **Advance invoice** FastTab, set the following fields.

    | Field | Description |
    |-------|-------------|
    | Posting profile | <p>*For Poland only:* Select the posting profile to use with advance invoicing.</p><p>**Important:** For the Czech Republic and Hungary, advance invoices aren't treated as accounting or tax documents, and they aren't posted to the general ledger. Therefore, you should leave this field blank for those countries/regions, to prevent advance invoices from being posted to the general ledger.</p> |
    | Offset account | Select the offset account. |
    | Sales tax group | Select the sales tax group to use when sales tax is calculated for advance invoicing. |
    | Reversal as correction | Select this checkbox if the reversal of an advance invoice should be considered a correction. |
    | Reverse on invoice date | Select this checkbox to reverse the prepayment on the date when the invoice is posted. |

1. On the **Payment** FastTab, set the following fields.

    | Field | Description |
    |-------|-------------|
    | Multiple prepayment dates | Select **Accept**, **Warning**, or **Error**. |
    | Date mismatch | Select **Accept**, **Warning**, or **Error**. |
    | Amount mismatch | Select **Accept**, **Warning**, or **Error**. |
    | Linking to posted advance invoice | Select **Accept**, **Warning**, or **Error**. |
    | (CZE), (POL) Prepayment handling | Select **Advanced**. |

1. On the **Number sequences** tab, set up number sequences for the following references:

    - Tax document
    - Tax credit memo
    - Advance invoice
    - Advance invoice credit note
    - Advance invoice reversal
    - Advance invoice voucher
    - Advance invoice credit note voucher
    - Advance invoice reversal voucher

## Create a customer advance invoice

1. Go to **Accounts receivable** &gt; **Common** &gt; **Advance invoices** &gt; **All advance invoices**.
1. On the Action Pane, on the **Advance invoice** tab, select **Advance invoice** to create an advance invoice.
1. Enter the required information, and then select **Post** to post the advance invoice.

An advance invoice can have one of the following statuses: **Opened**, **Partially paid**, or **Closed**. You can manually change the status of an advance invoice that you already posted. Select **Status**, and then, on the **Change the status of an advance invoice** page, in the **New status** field, select the new status of the advance invoice.

> [!NOTE]
> You can change the status of an advance invoice at any time. You can't process closed advance invoices in transactions.
> 
> *For Poland only:* Advance invoice transactions are generated if you set up a posting profile for advance invoices in **Accounts receivable parameters**. To view transactions that you posted, select **Voucher** on the **Advance invoice** page.

## VAT on advance invoices

Companies must record VAT on prepayments from customers, even though the sale isn't complete. To post VAT from a prepayment, add a line that contains specifications of VAT to an advance invoice. An advance invoice can have several lines, and those lines can contain VAT specifications that are taken from sales order lines. Therefore, you can post VAT from a prepayment in strict accordance with sales order lines.

> [!NOTE]
> The VAT specifications are copied to the advance invoice lines only if the **Type of tax** field on the **Sales tax codes** page is set to **Standard VAT** or **Reduced VAT**. Otherwise, they're copied to the advance invoice lines as if the VAT amount is 0 (zero).

## Link an advance invoice to a sales order or a free text invoice

You can link each advance invoice to only one sales order or free text invoice at a time. You can reassign an existing advance invoice to another sales order or free text invoice, as long as no prepayments are linked to the advance invoice.

To link an advance invoice to a sales order, follow these steps:

1. On the **All advance invoices** page, select the advance invoice.
1. On the Action Pane, select **Advance invoice**, and then select **Sales order**.
1. Select the sales order to link to the advance invoice, and then select **OK**.

To link an advance invoice to a free text invoice, follow these steps:

1. On the **All advance invoices** page, select the advance invoice.
1. On the Action Pane, select **Advance invoice**, and then select **Free text invoice**.
1. Select the free text invoice to link to the advance invoice, and then select **OK**.

## Create a customer advance invoice from a sales order

1. Create a sales order, or select an existing sales order.
1. Select **Invoice**, and then select **Generate** > **Advance invoice**.
1. On **Create advance invoice**, set the following fields.

    | Field | Description |
    |-------|-------------|
    | Percent | Specify the percentage of the prepayment for the sales order. |
    | Offset account | Select the default offset account to use with advance invoicing. |
    | Update order | Select **All**, **Deliver now**, **Picked**, **Packing slip**, or **Picked quantity and non-stocked products**. The advance invoice amount is calculated based on the sales order amounts for the items. |
    | Post VAT | Specify whether VAT should be posted during advance invoice posting. |
    | Post VAT date | Specify the date when VAT should be posted. |
    | Posting profile with prepayment journal voucher | Enter the posting profile for the prepayment. |
    | Create tax document | Specify whether a tax document should be created. |

> [!NOTE]
> *For Poland only:* Advance invoice transactions are generated if you set up a posting profile for advance invoices in **Accounts receivable parameters**.

## Create a customer advance invoice from a free text invoice

1. Create a free text invoice, or select an existing free text invoice.
1. On the **Invoice** tab, in the **New** section, select **Advance invoice**.

    You can now create a new advance invoice that links to the free text invoice.

> [!NOTE]
> *For Poland only:* Advance invoice transactions are generated if you set up a posting profile for advance invoices in **Accounts receivable parameters**.

## Print an advance invoice

- On **Advance invoice**, select **Print**. 

*For Poland only:* You can print an advance invoice document of the fiscal document. Select an option during advance invoice posting.

*For Poland only:* The layout of the sales invoice and free text invoice documents should include the following information about the advance invoice that is settled:

- Number of the advance invoice
- Date of the advance invoice
- Amount without VAT, VAT amount, amount with VAT, and currency
- Tax percentage

The summary of VAT amounts should include the **Tax from Advance Invoice** field. The amount that's due should be reduced by the amount of the advance invoice.

## Create a payment proposal from an advance invoice

When you create a new payment journal, you can automatically generate payment journal lines, based on an advance invoice.

1. On **Payment journal**, select the **Prepayment journal voucher** option, and then select **Lines**.
1. On **Journal voucher**, select **Payment proposal** > **Payment proposal from advance invoice** to create a payment proposal from advance invoices. Information such as the posting profile and sales tax groups is taken from the advance invoice.

> [!NOTE]
> New prepayments automatically link to advance invoices if you select the **Link prepayments** and **Change status** options on **Create payment proposal from advance invoices**.

## Link a prepayment to an advance invoice

To link a prepayment to an advance invoice from the payment journal, follow these steps:

1. Open the payment journal, select the line that has the prepayment, and then select **Functions** &gt; **Link to advance invoices**.

To link a prepayment to an advance invoice from the **Customer transactions** page, follow these steps:

1. Select **All customers** &gt; **Customer** &gt; **Transactions**.
1. Select the payment journal, select the line that has the prepayment, and then select **Functions** &gt; **Link to advance invoices**.

## Link an advance invoice to a prepayment

To link an advance invoice to a prepayment line, follow these steps:

1. On the **All advance invoices** page, select the advance invoice.
1. On the Action Pane, select **Advance invoice**, and then select **Prepayment**.
1. Select the prepayment line to link to the advance invoice, and then select **OK**.

## Advance invoice credit notes

- *For Poland only:* To cancel an advance invoice, create an advance invoice credit note and post it to the general ledger.
- To create a credit note, create a new advance invoice and then select **Credit note**. You can then select the advance invoice to cancel.
- You can also create a credit note for a sales invoice that has advance invoice settlement.
- The layout of advance invoice credit note invoices contains information about the lines both before and after correction.
- *For Poland only:* General ledger transactions are created after the advance invoice credit note is posted.

## Tax documents for the Czech Republic

For the Czech Republic, you can create a tax document that is based on prepayment information for the VAT liable delivery. You can create, create and show, or create and print the tax document from the prepayment page by selecting **Functions** &gt; **Tax document** and then selecting one of the options. The tax document contains detailed information about the VAT, such as the VAT type, the value, and its basis in the accounting currency and the transaction currency.

## Set up Accounts payable for advance invoices

- On the **Accounts payable parameters** page, on the **Number sequences** tab, specify a number sequence for advance invoices.

## Create a vendor advance invoice

You can manually create an advance invoice. Alternatively, the new advance invoice can be based on an existing purchase order.

### Manually create a vendor advance invoice

1. Go to **Accounts payable** &gt; **Common** &gt; **Advance invoices** &gt; **All advance invoices**.
1. On the Action Pane, on the **Advance invoice** tab, select **Advance invoice** to create an advance invoice.
1. Enter the required information, and then select **Post** to post the advance invoice.

An advance invoice can have one of the following statuses: **Opened**, **Partially paid**, or **Closed**. You can manually change the status of an advance invoice that you already posted. Select **Status**, and then, on the **Change the status of an advance invoice** page, in the **New status** field, select the new status of the advance invoice.

> [!NOTE]
> You can change the status of an advance invoice at any time. You can't process closed advance invoices in transactions.
>
> The VAT specifications are copied to the advance invoice lines only if the **Type of tax** field on the **Sales tax codes** page is set to **Standard VAT** or **Reduced VAT**. Otherwise, they're copied to the advance invoice lines as if the VAT amount is 0 (zero).

### Link an advance invoice to a purchase order

You can link each advance invoice to only one purchase order at a time. You can reassign an existing advance invoice to another purchase order, as long as no prepayments are linked to the advance invoice.

To link an advance invoice to a purchase order, follow these steps:

1. On the **All advance invoices** page, select the advance invoice.
1. On the Action Pane, select **Advance invoice**, and then select **Purchase order**.
1. Select the purchase order to link to the advance invoice, and then select **OK**.

### Create a vendor advance invoice from a purchase order

1. Create a purchase order, or select an existing purchase order.
1. Select **Invoice**, and then select **Generate** > **Advance invoice**.
1. On **Create advance invoice**, set the following fields.

    | Field | Description |
    |-------|-------------|
    | Percent | Enter the percentage of the prepayment for the purchase order. |
    | Update purchase | Select an option. The system calculates the advance invoice amount based on the purchase order amount for the items. |
    | Posting profile with prepayment journal voucher | Enter the posting profile for the prepayment. |

## Use the Advance invoice and Prepayment handling functionality

You can use the **Advance invoice** and **Prepayment handling** functionality in the business process. Here's an example:

1. A user submits an advance invoice that has VAT to a customer for a prepayment. The advance invoice isn't posted in the ledger.
1. The user creates and posts the prepayment without VAT.
1. The user creates a prepayment handling and relates it to the advance invoice. The user then posts the prepayment handling and creates the tax document. The system posts the VAT to the ledger and relates the VAT to the prepayment.

> [!NOTE]
> Clear the value in the **Posting profile** field on the **Advance invoice** FastTab on the **Update** tab of the **Account receivable parameters**. When you create the advance invoice, set the **Post tax** option to **Yes**.

To create a prepayment handling and link it to an advance invoice, follow these steps:

1. Go to **Accounts receivable** \> **Customers**, and find and open the customer record.
1. On the Action Pane, select **Customer** \> **Transactions**, select the prepayment transaction, and then select **Prepayment handling**.
1. Set the **Transform to payment** option to **No**.
1. Select **Advance invoice** to link the prepayment handling to the advance invoice. The system automatically creates VAT lines from the advance invoice.
1. Post the prepayment handling. The system automatically creates sales tax transactions for the prepayment.

## Reversing sales tax amounts for Czech Republic

To manually define the reversal of sales tax amounts, based on a prepayment handling, enable the **(Czech) Enable manual input sales tax amounts** feature. For information about how to enable features, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

> [!NOTE]
> This functionality is available only for Accounts payable.

When you mark an invoice transaction for settlement against a payment, you can update the sales tax amounts for reversal on the **Reverse sales tax amounts** tab of the **Settle transaction** page. As required, you can update tax amounts in the **Tax amount for settlement** field.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
