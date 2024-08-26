--- 
title: Create customer prepayment invoices
description: This article explains how to configure and process Customer prepayment invoices.
author: raynezou
ms.author: raynezou
ms.topic: how-to
ms.date: 08/25/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesEditLines, SysQueryForm, SysRecurrence
ms.dyn365.ops.version: Version 7.0.0 
---

# Create customer prepayment invoices

[!include [banner](../../includes/banner.md)]

This article explains how to configure and process Customer prepayment invoices.

## Customer prepayment invoices

Sellers often request a deposit (advance payment) to secure financial commitment before delivering goods or services. The customer prepayment invoice feature provides sellers with upfront funds to cover initial costs, reduce financial risk, and ensure that the buyer is committed to the transaction. 

### Types of prepayment processes 

### Prepayment as a billing invoice

In this process, the buyer makes an initial partial payment, commonly referred to as a deposit, to secure goods, services, or a contract. This deposit is a percentage of the total purchase price or a fixed amount which needs to be paid before the seller deliveries the goods or services. The prepayment invoice functions similarly to a billing document. The final invoice will be issued later, reflecting the complete amount of the order. 

### Prepayment invoice as a tax invoice 

In this type, the seller issues a real prepayment invoice (with sales tax) to the buyer before delivering goods or services. The buyer pays the invoice amount upfront, and only after this payment does the seller proceed with delivery of goods or services. Later, after goods and services are delivered, the official invoice will be sent out by deducting the amount in prepayment invoices.  

This article explains how to configure the **Customer prepayment invoice** and what the process looks like. Currently, only the Prepayment as a billing invoice process is supported. Prepayment invoice as a tax invoice process will be available in a later release.  

### Example of Customer prepayment invoice
A customer places an order for $10,000 and agrees to pay $3,000 as a prepayment. The final invoice is issued after the goods and services are fully delivered. 
The following accounting entries are recorded: 

Prepayment invoice creation: 
    Debit: Accounts Receivable 		$3,000 
    Credit: Prepayment (Deposit) 	$3,000 

Payment of prepayment invoice: 
    Debit: Cash/Bank 			    $3,000 
    Credit: Accounts Receivable 	$3,000 

Apply the prepayment on customer invoice: 
    Debit: Prepayment (Deposit)		$3,000 
    Credit: Accounts Receivable		$3,000 

Final customer invoice creation: 
    Debit: Accounts Receivable 		$10,000 
    Credit: Revenue 				$10,000 

In this example, the final invoice is issued with the total order amount ($10,000) and with corresponding tax entries. At customer side, the open amount to be paid should be total invoice amount ($10,000) minus the prepaid amount ($3,000), leaving a balance of $7,000. The entries ensure that the prepayment is properly recorded and offset against the final invoice when goods or services are delivered. 


## Set up Accounts receivable for customer prepayment invoices

To set up customer prepayment invoices, follow these steps.

1. Go to **Feature management**, and enable the **Prepayment customer invoice** feature.
2. Go to **Inventory management** \> **Setup** \> **Posting** \> **Posting** \> **Sales order** \> **Prepayment**.
3. Set up the default ledger account for posting. Set the type to **Customer prepayment**.
4. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters** \> **Updates** \> **Invoice** \> **Prepayment** > **Check mandatory sales order confirmation**. Select this parameter to create a prepayment invoice only if the sales order is confirmed.
5. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters** \> **Ledger and sales tax** \> **General** \> **Prepayment invoice** \> **Prepayment application policy**. 
 - **Notification** – Prepayments are manually applied. If the prepayment isn't applied, you'll get a notification when creating final invoice.
 - **Automatic** - Prepayments are automatically applied to the sales order if there is a full payment received and settles the prepayment invoice. 
6. Go to **Accounts receivable parameters** \> **Number sequences**, and set up number sequences for the **Prepayment invoice**, **Prepayment invoice voucher**, **Prepayment invoice reversal**, and **Prepayment invoice reversal voucher** references.
7. Go to **System administration** \> **Setup**, and select **Initialize process automations**.
8. Enable the **Automated prepayment settlement posting** background process.
9. Update the interval for the process automation to one minute.
10. Go to **Electronic reporting** \> **Reporting configurations** \> **Exchange** \> **Load from XML file**.

If you use Electronic reporting, follow these additional steps:
1. Go to **Electronic reporting workspace** /> **Reporting configurations** /> **Exchange** /> **Load from XML file**.
2. Enable Electronic reporting (ER) configurations.
3. Import the following files from Dataverse:

    - Customer prepayment invoice model xml
    - Prepayment invoice template xml
    - Customer prepayment invoice model mapping xml

4. Go to **Electronic reporting workspace** /> **Related links** /> **Electronic reporting destination**.
5. Click **New**. **Reference** /> **Prepayment invoice template** from the dropdown.
6. Click **Settings** to enable the different destinations for reports.
7. Click **OK**.
8. Select the **Convert to PDF** checkbox to print the file in PDF format.
9. Go to **Accounts receivable** /> **Accounts receivable parameters** /> **Electronic documents**.
10. Select the **Prepayment invoice** configuration from the dropdown.
11. Save the page. 

## Overview of the prepayment invoice process

The process for customer prepayment invoicing includes the following steps.

1. Define a prepayment value on the sales order.
2. Confirm and post a prepayment invoice.
3. Settle the prepayment invoice.
4. Apply the prepayment invoice to the final invoice.

## Create a prepayment proposal

When you create a sales order, you can define the prepayment amount by following these steps.

1. From the sales order, go to **Invoice** \> **Prepayment**, and select **Payment proposal**.
2. Select the prepayment type:

    - **Percentage** – If you select **Percentage**, the **Prepayment value** field is enabled. This field represents the percentage of the total sales order amount that is required as a prepayment. The **Total prepayment amount** field shows the calculated prepayment amount.
    - **Fixed** – If you select **Fixed**, the **Total prepayment amount** field is enabled, and you manually enter the prepayment amount. The amount that you enter can't exceed the sales order amount.

3. In the **Sales category** field, select the appropriate sales category that determines the revenue account according to the posting settings.

## Generate a prepayment invoice

After the prepayment proposal is confirmed, generate the prepayment invoice by following these steps.

1. Go to **Invoice** \> **Prepayment**, and select **Prepayment invoice**.
2. Review and post the prepayment invoice. The page displays the overall prepayment invoice information, including the customer invoice account, date, prepayment invoice number, prepayment status, and prepayment amount.
3. Select **Post**. The open customer transaction is created, and the status of the prepayment invoice is **Pending**.

## Settle the prepayment invoice

When you receive the payment for the prepayment, the customer payment journal is posted to settle the prepayment invoice amount. After prepayment invoice settlement, the status of the prepayment invoice is **Received**, and **Apply prepayment** is available.

## Post the final invoice and apply the prepayment

Select **Apply prepayment**. On the **Apply prepayment** page, select the prepayment in the **Select prepayments to apply** list, and then select **Apply prepayment**.

After the sales order invoice is posted, the selected prepayment is applied to the invoice when the **Automated prepayment settlement posting** background process is successfully run. The remaining amount of the sales order invoice can be settled through a customer payment journal and should display the outstanding amount to be received. 
