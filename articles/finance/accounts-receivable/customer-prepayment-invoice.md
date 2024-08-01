--- 
title: Create customer prepayment invoices
description: This article explains how to create a prepayment invoice for a customer.
author: raynezou
ms.author: raynezou
ms.topic: how-to
ms.date: 07/25/2024
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

This article explains how to create a prepayment invoice for a customer.

## Customer prepayment invoices

Organizations often receive prepayments (advance payments) from customers for goods or services before those goods or services are delivered. These prepayments ensure that the organization has enough funds to fulfill the customer's order and effectively manage cash flow. This article explains prepayments for sales order invoices in Microsoft Dynamics 365 Finance.

## Set up Accounts receivable for customer prepayment invoices

To set up customer prepayment invoices, follow these steps.

1. Go to **Feature management**, and enable the **Prepayment customer invoice** feature.
2. Go to **Inventory management** \> **Setup** \> **Posting** \> **Posting** \> **Sales order** \> **Prepayment**.
3. Set up the default ledger account for posting. Set the type to **Customer prepayment**.
4. Go to **Accounts receivable parameters** \> **Ledger and sales tax** \> **Payment**, and complete the **Posting profile** setup with a prepayment journal voucher.
5. Go to **Accounts receivable parameters** \> **Number sequences**, and set up number sequences for the **Prepayment invoice**, **Prepayment invoice voucher**, **Prepayment invoice reversal**, and **Prepayment invoice reversal voucher** references.
6. Go to **System administration** \> **Setup**, and select **Initialize process automations**.
7. Enable the **Automated prepayment settlement posting** background process.
8. Update the interval for the process automation to one minute.
9. Go to **Electronic reporting** \> **Reporting configurations** \> **Exchange** \> **Load from XML file**.
10. Enable Electronic reporting (ER) configurations.
11. Import the following files from Dataverse:

    - Customer prepayment invoice model xml
    - Prepayment invoice template xml
    - Customer prepayment invoice model mapping xml

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
2. Review and post the prepayment invoice.
3. Select **Post**. The open customer transaction is created, and the status of the prepayment invoice is **Pending**.

## Settle the prepayment invoice

When you receive the payment for the prepayment, the customer payment journal is posted to settle the prepayment invoice amount. After prepayment invoice settlement, the status of the prepayment invoice is **Received**, and the **Apply prepayment** button becomes available.

## Post the invoice and apply the prepayment

Select **Apply prepayment**. On the **Apply prepayment** page, select the prepayment in the **Select prepayments to apply** list, and then select **Apply prepayment**.

After the sales order invoice is posted, the selected prepayment is applied to the invoice when the **Automated prepayment settlement posting** background process is successfully run.
