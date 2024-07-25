--- 
title: Create customer prepayment invoice
description: This article describes how to create a prepayment invoice for a customer.
author: raynezou
ms.author: raynezou
ms.topic: how-to
ms.date: 07/25/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesEditLines,  SysQueryForm, SysRecurrence
ms.dyn365.ops.version: Version 7.0.0 
---

# Create customer prepayment invoice

[!include [banner](../../includes/banner.md)]

This article describes how to create a prepayment invoice for a customer.

## Customer prepayment invoice 

Organizations often receive prepayments (advance payments) from customers for goods or services before those goods or services are delivered. These prepayments ensure that the organization has sufficient 
funds to fulfill the customer's order and manage cash flow effectively. This article explains prepayments for sales order invoices in Dynamics 365 Finance.  

## Set up Accounts receivable for prepayment customer invoices 

To set up prepayment customer invoices, follow these steps:
1. Enable the **Prepayment customer invoice** feature under **Feature management**.
2. Go to **Inventory management** > **Setup** > **Posting** > **Posting** > **Sales order** > **Prepayment**.
3. Set up the default ledger account for posting with the **Customer prepayment** type.
4. Go to **Accounts receivable parameters** > **Ledger and sales tax** > **Payment** and complete the **Posting profile** setup with prepayment journal voucher.
5. Go to **Accounts receivable parameters** > **Number sequences** and set up the number sequence for **Prepayment invoice**, **Prepayment invoice voucher**, **Prepayment invoice reversal** and **Prepayment invoice reversal voucher**.
6. Go to **System administration** > **Setup** and click **Initialize process automations**.
7. Enable the **Automated prepayment settlement posting** background process.
8. Update the interval for this process automation to 1 minute.
9. Go to **Electronic reporting** > **Reporting configuations** > **Exchange** > **Load from XML file**.
10. Enable electronic reporting configurations.
11. Import the following files from Dataverse:
 - Customer prepayment invoice model xml
 - Prepayment invoice template xml
 - Customer prepayment invoice model mapping xml    

### Overview of the prepayment invoice process 

The overview process of customer prepayment invoicing includes: 
1. Define a prepayment value on the sales order.
2. Confirm and post a prepayment invoice.
3. Settle the prepayment invoice.
4. Apply the prepayment invoice to the final invoice.  

### Create prepayment proposal 

When you create a sales order, you can define the prepayment amount by following these steps: 
1. Go to the sales order, **Invoice** > **Prepayment** and click **Payment proposal**.
2. Select the prepayment type.
 - **Percentage** - If you select **Percentage**, the **Prepayment value** field is enabled. This field represents the percentage of the total sales order amount that is required as the prepayment. The calculated prepayment amount is displayed in the **Total prepayment amount** field.
 - **Fixed** - If you select **Fixed**, the **Total prepayment amount** field is enabled and you enter the prepayment amount directly. A value higher than the sales order amount isn't allowed.    
3. In the **Sales category** field, select the appropriate sales category that determines the revenue account according to the posting settings. 

### Generate prepayment invoices 

After the prepayment proposal is confirmed, generate the prepayment invoice by: 
1. Go to **Invoice** > **Prepayment**, click **Prepayment invoice**.
2. Review and post prepayment invoice.
3. Click **Post**. The open customer transaction is created, and the prepayment invoice status is **Pending**. 

### Settle the prepayment invoice 

When you receive the payment for the prepayment, the customer payment journal is posted to settle the prepayment invoice amount. After prepayment invoice settlement, the status of the prepayment invoice is **Received** and **Apply prepayment** is available.  

### Post the invoice with prepayment application 

Click **Apply prepayment**. The **Apply prepayment page opens. Apply the prepayment by selecting the prepayment from **Select prepayments to apply** list and click **Apply prepayment**. 

After posting the sales order invoices, the selected prepayment is applied to the invoice when **Automated prepayment settlement posting** is successfully executed. 

 
