---
# required metadata

title: Advance invoices for Eastern Europe
description: An advance invoice is a document that you can create for a customer or vendor. It states the amount that must be prepaid on a sales order. This topic provides information about advance invoices for Eastern Europe.
author: ShylaThompson
manager: AnnBe
ms.date: 04/10/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: ShylaThompson
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 272643
ms.assetid: 00072155-f3d1-4d09-b848-5c086cac0891
ms.search.region: Czech Republic, Estonia, Hungary, Latvia, Lithuania, Poland
# ms.search.industry: 
ms.author: epopov
ms.dyn365.ops.intro: Version 1611
ms.search.validFrom: 2016-11-30

---

# Advance invoices for Eastern Europe
"[!include[banner](includes/banner.md)]"


An advance invoice is a document that you can create for a customer or vendor. It states the amount that must be prepaid on a sales order. This topic provides information about advance invoices for Eastern Europe.

Advance invoice functionality lets you perform the following tasks:

-   Issue advance invoices to customers, and track the status of those advance invoices (**Open**, **Partially paid**, or **Closed**).
-   Post advance invoice transactions and value-added tax (VAT) transactions (for Poland only).
-   Generate payment journal lines automatically, based on an advance invoice.
-   Link prepayments that are received from customers to advance invoices (either before or after you post the prepayment).
-   Change the VAT posting in posted prepayments (that is, convert a prepayment to a payment or a payment to a prepayment, or change the posting date, tax rate, or amount).
-   Create a tax document for the VAT liable delivery (for Czech Republic only).

## Advance invoices for Poland
Polish companies that receive prepayments must create an invoice for prepayments for the customer. This advance invoice is posted to the general ledger and is a mandatory document for VAT tax purposes. The tax that is calculated on the advance invoice must be reported to the tax authority. When the final sale of goods is performed, the advance invoice should be specified on the sales invoice. The total amount of sales must include prepayments. When the sales invoice is posted, the settled advance invoice will be reversed. The original advance invoice will be settled with an advance invoice reversal.

## Set up Accounts receivable for advance invoices
On the **Accounts receivable parameters** page, on the **Update** tab, specify the following parameters.

|FastTab|Parameter|Description|
|------|----------|------------|
|Advance invoice  |Posting profile|Select the posting profile to use with advance invoicing (for Poland only). **Important:** For the Czech Republic and Hungary, advance invoices aren't treated as accounting or tax documents, and they aren't posted to the general ledger. Therefore, you should leave this field blank for these countries to prevent advance invoices from being posted to the general ledger.
|
|Advance invoice  |Off|set account        |Select the default offset account to use with advanced invoicing.|
|Advance invoice  |Sales tax group        |Select the sales tax group to use when sales tax is calculated for advance invoicing.|
|Advance invoice  |Reversal as correction |Select this check box if the reversal of an advance invoice should be considered a correction.|
|Advance invoice  |Reverse on invoice date|Select this check box to reverse the prepayment on the date when the invoice is posted.|
|Payment          |Multiple prepayment dates|Select from the following options: **Accept**, **Warning**, or **Error**.|
|Payment          |Date mismatch          |Select from the following options: **Accept**, **Warning**, or **Error**.|
|Payment          |Amount mismatch        |Select from the following options: **Accept**, **Warning**, or **Error**.|
|Payment          |Linking to posted advance invoice|Select from the following options: **Accept**, **Warning**, or **Error**.|
|Payment          |(CZE), (POL) Prepayment handling|Select **Advanced**.|

On the **Number sequences** tab, set up number sequences for the following references:

-   Tax document
-   Tax credit memo
-   Advance invoice
-   Advance invoice credit note
-   Advance invoice reversal
-   Advance invoice voucher
-   Advance invoice credit note voucher
-   Advance invoice reversal voucher

## Create a customer advance invoice
Click **Accounts receivable** &gt; **Common** &gt; **Advance invoices** &gt; **All advance invoices**. To create a new advance invoice, on the Action Pane, on the **Advance invoice** tab, click **Advance invoice**. Enter the required information, and then click **Post** to post the advance invoice. An advance invoice can have one of the following statuses: **Opened**, **Partially paid**, or **Closed**. You can manually change the status of an advance invoice that has been posted. Click **Status**, and then, on the **Change the status of an advance invoice** page, in the **New status** field, select the new status of the advance invoice. **Note:** You can change the status of an advance invoice at any time. You can't process closed advance invoices in transactions. **Note:** For Poland, advance invoice transactions are generated if you set up a posting profile for advance invoices in the Accounts receivable parameters. To view transactions that have been posted, on the **Advance invoice** page, click **Voucher**.

## VAT on advance invoices
Companies must record VAT on prepayments from customers, even though the sale hasn't been completed. To post VAT from a prepayment, you can add a line that contains specifications of VAT to an advance invoice. An advance invoice can have several lines, and the lines can contain VAT specifications that are taken from sales order lines. Therefore, you can post VAT from a prepayment in strict accordance to sales order lines. **Note:** The VAT specifications are copied to the advance invoice lines only if the **Type of tax** field on the **Sales tax codes** page is set to **Standard VAT** or **Reduced VAT**. Otherwise, the line is copied to the advance invoice as if the VAT amount is 0 (zero).

## Link an advance invoice to a sales order or a free text invoice
Each advance invoice can be linked with only one sales order or free text invoice at a time. You can reassign an existing advance invoice to another sales order or free text invoice, provided that no prepayments are linked to the advance invoice. To link an advance invoice to a sales order, on the **All advance invoices** page, select the advance invoice. On the Action Pane, click **Advance invoice**, and then click **Sales order**. Then select the sales order to link to the advance invoice, and click **OK**. To link an advance invoice to a free text invoice, on the **All advance invoices** page, select the advance invoice. On the Action Pane, click **Advance invoice**, and then click **Free text invoice**. Then select the free text invoice to link to the advance invoice, and click **OK**.

## Create a customer advance invoice from a sales order
Create a sales order, or select an existing sales order. Click **Invoice**, and then click **Generate** &gt; **Advance invoice**. On the **Create advance invoice** page, set following fields.

| Field                                           | Description                                                                                                                                                                                                                               |
|-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Percent                                         | Specify the percentage of the prepayment for the sales order.                                                                                                                                                                             |
| Offset account                                  | Select the default offset account to use with advanced invoicing.                                                                                                                                                                         |
| Update order                                    | Select from the following options: **All**, **Deliver now**, **Picked**, **Packing slip**, or **Picked quantity and non-stocked products**. The advance invoice amount will be calculated based on the Sales order amounts for the items. |
| Post VAT                                        | Specify whether VAT should be posted during advance invoice posting.                                                                                                                                                                      |
| Post VAT date                                   | Specify the date for posting VAT.                                                                                                                                                                                                         |
| Posting profile with prepayment journal voucher | Specify the posting profile for the prepayment.                                                                                                                                                                                           |
| Create tax document                             | Specify whether a tax document should be created.                                                                                                                                                                                         |

> [!NOTE}
>For Poland, advance invoice transactions are generated if you set up a posting profile for advance invoices in the Accounts receivable parameters.

## Create a customer advance invoice from a free text invoice
Create a free text invoice, or select an existing free text invoice. On **Invoice** tab, in the **New** section, click **Advance invoice**. You can then create a new advance invoice that will be linked to the free text invoice. **Note:** For Poland, advance invoice transactions are generated if you set up a posting profile for advance invoices in the Accounts receivable parameters.

## Print an advance invoice
To print an advance invoice, on the **Advance invoice** page, click **Print**. For Poland, you can print an advance invoice document of the fiscal document. Select an option during advance invoice posting. For Poland, the layout of the sales invoice and free text invoice documents should include the following information about the advance invoice that is settled:

-   Number of the advance invoice
-   Date of the advance invoice
-   Amount without VAT, VAT amount, amount with VAT, and currency
-   Tax percentage

The summary of VAT amounts should include **Tax from Advance Invoice**. The amount that is due should be reduced by the amount of the advance invoice.

## Create a payment proposal from an advance invoice
You can generate payment journal lines automatically, based on an advance invoice. When you create a new payment journal, on the **Payment journal** page, select the **Prepayment journal voucher** option, and then click **Lines**. On the **Journal voucher** page, you can click **Payment proposal** &gt; **Payment proposal from advance invoice** to create a payment proposal from advance invoices. Information such as the posting profile and sales tax groups is taken from the advance invoice. **Note:** New prepayments will be linked automatically to advance invoices if the **Link prepayments** and **Change status** options are selected on the **Create payment proposal from advance invoices** page.

## Link a prepayment to an advance invoice
To link a prepayment to an advance invoice from the payment journal, open the payment journal, select the line that has the prepayment, and then click **Functions** &gt; **Link to advance invoices**. To link a prepayment to an advance invoice from the **Customer transactions** page, click **All customers** &gt; **Customer** &gt; **Transactions**. Select the payment journal, select the line that has the prepayment, and then click **Functions** &gt; **Link to advance invoices**.

## Link an advance invoice to a prepayment
To link an advance invoice to a prepayment line, on the **All advance invoices** page, select the advance invoice. On the Action Pane, click **Advance invoice**, and then click **Prepayment**. Then select the prepayment line to link to the advance invoice, and click **OK**.

## Advance invoice credit note
-   (POL) To cancel an advance invoice you can create an advance invoice credit note and post it to the general ledger.
-   To create a credit note, you can create a new advance invoice and then click **Credit note**. You can then select the advance invoice to cancel.
-   You can also create a credit note of a sales invoice that has advance invoice settlement.
-   The layout of advance invoice credit note invoices contains information about the lines both before and after correction.
-   (POL) General ledger transactions are created after the advance invoice credit note is posted.

## (CZE) Tax documents
For the Czech Republic, you can create a tax document that is based on prepayment information for the VAT liable delivery. You can create, create and show, or create and print the tax document from the prepayment page. Click **Functions** &gt; **Tax document**, and select one of the options. The tax document contains detailed information about the VAT, such as the VAT type, the value, and its basis in the accounting currency and the transaction currency.

## Set up Accounts payable for advance invoices
On the **Accounts payable parameters** page, on the **Number sequences** tab, specify a number sequence for advance invoices.

## Create a vendor advance invoice
You can manually create an advance invoice. Alternatively, the new advance invoice can be based on an existing purchase order.

## Manually create a vendor advance invoice
Click **Accounts payable** &gt; **Common** &gt; **Advance invoices** &gt; **All advance invoices**. To create a new advance invoice, on the Action Pane, on the **Advance invoice** tab, click **Advance invoice**. Then enter the required information, and click **Post** to post the advance invoice. An advance invoice can have one of the following statuses: **Opened**, **Partially paid**, or **Closed**. You can manually change the status of an advance invoice that has been posted. Click **Status**, and then, on the **Change the status of an advance invoice** page, in the **New status** field, select the new status of the advance invoice. **Note:** You can change the status of an advance invoice at any time. You can't process closed advance invoices in transactions. **Note:** The VAT specifications are copied to the advance invoice lines only if the **Type of tax** field on the **Sales tax codes** page is set to **Standard VAT** or **Reduced VAT**. Otherwise, the line is copied to the advance invoice as if the VAT amount is 0 (zero).

## Link an advance invoice to a purchase order
Each advance invoice can be linked with only one purchase order at a time. You can reassign an existing advance invoice to another purchase order, provided that no prepayments are linked to the advance invoice. To link an advance invoice to a purchase order, on the **All advance invoices** page, select the advance invoice. On the Action Pane, click **Advance invoice**, and then click **Purchase order**. Then select the purchase order to link to the advance invoice, and click **OK**.

## Create a vendor advance invoice from a purchase order
Create a purchase order, or select an existing purchase order. Click **Invoice**, and then click **Generate** &gt; **Advance invoice**. On the **Create advance invoice** page, set following fields.

| Field                                           | Description                                                                                                              |
|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| Percent                                         | Specify the percentage of the prepayment for the purchase order.                                                         |
| Update purchase                                 | Select from the options. The advance invoice amount will be calculated based on the Purchase order amount for the items. |
| Posting profile with prepayment journal voucher | Specify the posting profile for the prepayment.                                                                          |




