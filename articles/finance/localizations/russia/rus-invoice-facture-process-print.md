---
title: Invoice factures processing and printing
description: Learn about working with invoice factures, including outlines on setting up number sequences for factures and processsing and printing invoice-factures.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/10/2024
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2019-06-28
ms.dyn365.ops.version: 10.0.0
---

# Invoice factures processing and printing

[!include [banner](../../includes/banner.md)]


An invoice-facture is a document that certifies the actual shipment of goods or services, and their cost. An invoice-facture is issued (sent) by the seller (contractor or performer) to the buyer (customer) after the buyer has accepted all the goods or services. An invoice-facture has two purposes. 

- Confirmation that the order or work has been completed
- Confirmation of the amount of value-added tax (VAT) that was paid, so that the amount can be credited later

An invoice-facture can be processed in the following ways:

- Based on a purchase order or sales order
- Based on a posted vendor or customer invoice
- Based on a purchase product receipt
- Based on a sales packing slip
- Based on a sales free-text invoice

## Setup

### Set up a number sequence for factures

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
2. On the **Number sequences** tab, select a number sequence code for the facture reference, and then assign the number sequence in the **Number sequence code** field.

> [!NOTE]
> Verify that the selected number sequence for factures is continuous (the **Continuous** flag on the **General** FastTab is selected). 

3. To override existing number sequence groups, select **Group**, and then select **New** to create a number sequence group. Then, in the lower part of the page, define the number sequence for facture.

On the **All customers** page, you can override number sequence groups in the **Number sequence** field on the **Invoice and delivery** FastTab.

### Set up a tax settlement period

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**.
2. On the **Period intervals** FastTab, verify that the required period is included.

## Process and print invoice-factures for purchase orders
A purchase is completed when the invoice and facture are registered. Typically, transactions are created when the invoice is registered, and then the facture, which is the basis for VAT deduction, is created.

### Process a facture without posting a purchase order invoice
You can process a facture before an invoice is posted. In this case, the invoice is automatically posted when the facture is processed.

1. On the **All purchase orders** page, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Facture**.
2. In the upper part of the **Update facture** page, set the following fields:

  - **Facture** – Enter the facture number.
  - **Date of the registration** – Select the facture registration date.
  - **Facture date** – Select the facture creation date.

> [!NOTE]
> The facture creation date is the same as the facture registration date. You can change the value of this field only if you set the **Same as** option to **No**.

3. In the lower part of the page, mark the invoices that should be included in the facture processing.
4. On the Action Pane, select **Posting** \> **Update and print** to post and print the facture.
–or–
Select **Posting** \> **Update** to update the facture without printing it.
–or–
Select **Posting** \> **Print** to print the facture without posting it.
5. To review the posted facture, on the Action Pane, on the **Invoice** tab, in the **Journals** group, select **Facture**.

> [!NOTE]
> To post a facture for several purchase orders, on the **Update facture** page, select **Select**, and then select the orders that should be processed.

### Process a facture based on the posted purchase order invoice
The steps in this procedure are basically the same as the steps in the previous procedure, Process a facture without posting a purchase order invoice. However, in step 1, you post the invoice from the purchase order in the standard way.

### Process a facture based on the product receipt of a purchase order
You can post factures that are based on product receipts that include different types of order lines.

1. Post the product receipt from the purchase order in the standard way.
2. On the **Purchase order** page, on the Action Pane, on the **Invoice** tab, in the** Generate** group, select **Facture**.
3. In the lower part of the page, mark the product receipt invoice or invoices that should be included, and then select **OK** to post the facture.

## Process factures from the purchase invoice journal
You can process purchase factures from the list of all posted invoices.

1. Go to **Accounts payable** \> **Inquiries and reports** \> **Invoice** \> **Invoice journal**.
2. Select the posted invoice to update the facture for, and then, on the **Overview** tab, select **Create facture** > **Update facture**.
3. In the upper part of the **Update facture** page, on the **Overview** tab, in the **Facture** field, enter the facture number.
4. In the **Date of the registration** field, select the facture registration date.
5. In the **Facture date** field, select the facture creation date.

> [!NOTE]
> The facture creation date is the same as the facture registration date. You can change the value of this field only if you set the Same as option to No.

6. In the lower part of the page, on the **Invoice** tab, select the **To facture** check box for the invoice or invoices for the facture.

> [!NOTE]
> If you don't want to create a facture for an invoice line, clear the **To facture** check box for that line on the **Invoice lines** tab.

7. On the Action Pane, select **Posting** \> **Update and print** to post and print the facture.
–or–
Select **Posting** \> **Update** to update the facture without printing it.
–or–
Select **Posting** \> **Print** to print the facture without posting it.

8. You can view the facture that is created by selecting Facture on the **Overview** tab of the **Invoice journal** page.

## View factures in the purchase facture journal
You can view and print factures on the **Facture journal** page (**Accounts payable** \> **Inquiries and reports** \> **Facture**). Select the facture, and then, on the Action Pane, select **Print** \> **Original** to print the original facture select **Print** \> **Copy** to print a copy, or select **Delete** to delete the facture.

The upper part of the page shows information about the facture information. This information includes the facture number, date of the registration, facture date, amount (including and excluding tax), sales tax amount, currency, and invoice account.

The lower part of the page shows information about the invoice lines on two tabs:
-	**Overview** – This tab shows the item code, product name, price unit quantity, amount in the transaction currency, price, and sales tax amount per line.
-	**Product dimensions** – This tab shows the site, warehouse, and product dimensions.

## Process and print invoice-factures for sales orders
When an invoice is registered, transactions are created, and then the facture is generated. This process completes the sale.

### Process a facture without posting the invoice for a sales order
You can process a facture without posting an invoice. In this case, the invoice is automatically posted when the facture is processed.

1. On the **All sales orders** page, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Facture**.
2. In the upper part of the **Update facture** page, set the following fields:

  - **Date of the registration** – Select the facture registration date.
  - **Facture date** – Select the facture creation date.

  > [!NOTE]
  > The facture creation date is the same as the facture registration date. You can change the value of this field only if you set the **Same as** option to **No**.

  - **Number sequence group** – Select the number sequence group to allocate different number sequences to different customers or vendors.
  
  > [!NOTE]
  > The reference is used if alternative document numbering is applied for the facture.

  - **Facture** – (Optional) Select the free facture number if you previously deleted a facture. If you don't select the free facture number, the lowest free facture number will be assigned to the new facture. This behavior is standard for continuous numbering of number sequences.

  > [!NOTE]
  > If you didn't previously delete any factures, the Facture field isn't editable.
  
3. In the lower part of the page, mark the invoice or invoices that should be included in the facture processing.
4. On the Action Pane, select **Posting** \> **Update and print** to post and print the facture.
–or–
Select **Posting** \> **Update** to update the facture without printing it.
–or–
Select **Posting** \> **Print** to print the facture without posting it.

5. You can review the posted facture by selecting **Facture** in the **Journals group** on the **Invoice** tab of the Action Pane.

> [!NOTE]
> To post a facture for several sales orders, on the **Update facture** page, select **Select**, and then select the orders that should be processed.

### Process a facture based on a posted invoice for a sales order
The steps in this procedure are basically the same as the steps in the previous procedure, Process a facture without posting the invoice for a sales order. However, in step 1, you post the invoice from the sales order in the standard way.

### Process a facture based on packing slips for sales orders
You can post factures that are based on packing slips that include different types of order lines.

1. Post the packing slip from the sales order in the standard way.
2. On the **Sales order** page, on the Action Pane, on the **Invoice** tab, in the **Generate** group, select **Facture**.
3. In the lower part of the page, mark the packing slip invoice or invoices that should be included, and then select **OK** to post the facture.

> [!NOTE]
> Sales order lines that are based on categories contain the customs cargo declaration (GTD) number, and the country or region of origin. These details are transferred to the facture journal when you update a facture for a sales order.
> As a result of facture posting, the system processes the invoice and posts the facture.

### Process a facture based on recurring invoices
To run periodic facture creation, go to **Accounts receivable** \> **Invoices** \> **Batch invoicing** \> **Facture**.

### Process invoice-factures for a free text invoice

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
2. Select **New** to create a free text invoice, and enter the required details.
3. Select **Post** to post the free text invoice.
4. On the Action Pane, on the **Invoice** tab, in the **Post** group, select **Update facture** to create the facture.

> [!NOTE]
> You can process a facture without posting a free text invoice. In this case, the invoice is automatically posted when the facture is processed.**

### Process invoice-factures from sales invoice journal
You can process sales factures from the list of all posted invoices.

1. Go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**.
2. Select the invoice that is associated with the facture that must be updated, and then, on the Action Pane, on the **Invoice** tab, select **Create facture** \> **Update facture**.
3. In the **Number sequence group** field, select the number sequence group to allocate different number sequences to different customers or vendors.

> [!NOTE]
> The reference is used if an alternative document numbering is applied for the facture.

4. In the **Date of the registration** field, select the facture registration date.
5. In the **Facture date** field, select the facture creation date.

> [!NOTE]
> The facture creation date is the same as the facture registration date. You can change the value of this field only if you set the **Same as** option to **No**.

6. In the lower part of the page, on the **Invoice** tab, use the **To facture** check box to select the invoice or invoices for the facture.

> [!NOTE]
> If you don't want to create a facture for an invoice line, clear the **To facture** check box for the line on the **Invoice lines** tab.

7.	On the Action Pane, select **Posting** \> **Update and print** to update and print the facture.
–or–
Select **Posting** \> **Update** to update the facture without printing it.
–or–
Select **Posting** \> **Print** to print the facture without posting it.

8.	You can view the facture that is created by selecting **Facture** on the **Overview** tab of the **Invoice journal** page.

### View factures in the sales facture journal
You can view and print all factures on the **Facture journal** page (**Accounts receivable** \> **Inquiries and reports** \> **Facture**). Select the facture, and then, on the Action Pane, select **Print** \> **Original** to print original facture, select **Print** \> **Copy** to print a copy, or select **Delete** to delete the facture.

The upper part of the page shows information about the facture. This information includes, the facture number, date of the registration, facture date, amount (including and excluding tax), tax amount, currency, and invoice account.

The lower part of the page shows information about the invoice lines. This information includes the invoice number, item code, category, product name, price, unit quantity, amount in the transaction currency, and price. The **Overview** tab shows the sales tax amount per line, and the **Product dimensions** tab shows the site, warehouse, and other product dimension information.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
