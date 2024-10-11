--- 
title: Create customer prepayment invoices
description: This article explains how to configure and process customer prepayment invoices.
author: raynezou
ms.author: raynezou
ms.topic: how-to
ms.date: 10/20/2024
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

This article explains how to configure and process customer prepayment invoices.

## Customer prepayment invoices

Sellers can request a deposit or advance payment to secure a commitment from the customer before they deliver goods or services. The customer prepayment invoice feature provides up-front funds to cover initial costs, reduce financial risk, and ensure that the buyer is committed to the transaction.

### Types of prepayment processes

#### Prepayment as a deposit

In this process, the buyer makes an initial partial payment, commonly referred to as a deposit, to secure goods, services, or a contract. This deposit is either a percentage or a fixed amount of the total value of the sales order. The prepayment invoice functions similarly to a billing document. The final invoice will be issued later, reflecting the complete amount of the sales order. 

#### Prepayment invoice as a tax invoice

In this type, the seller issues a real prepayment invoice (with sales taxes, if applicable) to the buyer. The buyer pays the invoice amount upfront and upon completion of payment, the seller may proceed with delivery of goods or services. Later, the official invoice will be sent out where the invoice value will be the total outstanding amount, which is the difference between the total sales order value and the total prepaid amount. 

This article explains how the feature “Customer prepayment invoice” should be configured and how the process looks like. As first release, only scenario A is supported. Scenario B is planned on the product roadmap and will be available in a later release.  

### Example of a customer prepayment invoice

A customer places an order for $10,000 and agrees to pay $3,000 as a prepayment. The final invoice is issued after the goods and services are fully delivered.

The following accounting entries are recorded:

- Prepayment invoice creation:

    - **Debit:** Accounts receivable: $3,000
    - **Credit:** Prepayment (Deposit): $3,000

- Payment of prepayment invoice:

    - **Debit:** Cash/Bank: $3,000
    - **Credit:** Accounts receivable: $3,000

- Apply the prepayment on customer invoice:

    - **Debit:** Prepayment (Deposit): $3,000
    - **Credit:** Accounts receivable: $3,000

- Final customer invoice creation:

    - **Debit:** Accounts receivable: $10,000
    - **Credit:** Revenue: $10,000

In this example, the final invoice includes the total order amount ($10,000) and corresponding tax entries. The customer should pay the open amount, which is the total invoice amount ($10,000) minus the prepaid amount ($3,000), or $7,000. The entries ensure that the prepayment is correctly recorded and offset against the final invoice when the goods or services are delivered.

## Set up Accounts receivable for customer prepayment invoices

To set up customer prepayment invoices, follow these steps.

1. Go to **Feature management**, and enable the **Prepayment customer invoice** feature.
2. Go to **Inventory management** \> **Setup** \> **Posting** \> **Posting** \> **Sales order** \> **Prepayment**.
3. Set up the default ledger account for posting. Set the type to **Customer prepayment**.
4. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
5. On the **Updates** tab, on the **Invoice** FastTab, in the **Prepayment** section, select the **Check mandatory sales order confirmation** parameter to create a prepayment invoice only if the sales order is confirmed.
6. On the **Ledger and sales tax** tab, on the **General** FastTab, in the **Prepayment invoice** section, in the **Prepayment application policy** field, select one of the following values: 

     - **Notification** – Prepayments are manually applied. If the prepayment isn't applied, you receive a notification when you create the final invoice.
    - **Automatic** – Prepayments are automatically applied to the sales order if full payment is received and settles the prepayment invoice. 

7. On the **Number sequences** tab, set up number sequences for the **Prepayment invoice**, **Prepayment invoice voucher**, **Prepayment invoice reversal**, and **Prepayment invoice reversal voucher** references.
8. Go to **System administration** \> **Setup**, and select **Process automations**.
9. Click **Initialize process automations**.
10. Update the interval for the process automation to one minute.

If you use Electronic reporting (ER), follow these additional steps.

1. Open the **Electronic reporting** workspace, and select the **Reporting configurations** tile. Then, on the **Configurations** pages, on the Action Pane, select **Exchange** \> **Load from XML file**.
2. Enable ER configurations.
3. Import the following files from Dataverse:

    - Customer prepayment invoice model xml
    - Prepayment invoice template xml
    - Customer prepayment invoice model mapping xml

4. In the **Electronic reporting** workspace, in the **Related links** section, select **Electronic reporting destination**.
5. Select **New**. Then, in the **Reference** field, select **Prepayment invoice template**.
6. Select **Settings** to enable the different destinations for reports.
7. Select **OK**.
8. Select the **Convert to PDF** checkbox to print the file in PDF format.
9. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
10. On the **Electronic documents** tab, select the **Prepayment invoice** configuration in the dropdown list.
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
2. Review and post the prepayment invoice. The page shows information about the overall prepayment invoice, including the customer invoice account, date, prepayment invoice number, prepayment status, and prepayment amount.
3. Select **Post**. The open customer transaction is created, and the status of the prepayment invoice is **Pending**.

## Settle the prepayment invoice

When you receive the payment for the prepayment, the customer payment journal is posted to settle the prepayment invoice amount. After prepayment invoice settlement, the status of the prepayment invoice is **Received**, and **Apply prepayment** is available.

## Post the final invoice and apply the prepayment

1. On the **Apply prepayment** page, in the **Select prepayments to apply** list, select the prepayment.
2. Select **Apply prepayment**.

    After the sales order invoice is posted, the selected prepayment is applied to the invoice when the **Automated prepayment settlement posting** background process is successfully run.

3. The remaining amount of the sales order invoice can be settled through a customer payment journal and shows the outstanding amount.
