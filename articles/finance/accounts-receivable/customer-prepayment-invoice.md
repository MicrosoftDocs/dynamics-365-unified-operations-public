--- 
title: Create customer prepayment invoice
description: This article describes how to create a prepayment invoice for a customer.
author: prabhatb-ship-it
ms.author: prabhatb
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

Organizations often receive prepayments (advance payments) from customers for goods or services before those goods or services are delivered. These prepayments help ensure that the organization has sufficient 
funds to fulfill the customer's order and manage cash flow effectively. This article explains prepayments for sales order invoices in Dynamics 365 Finance.  

## Set up Accounts receivable for prepayment customer invoices 

You need to firstly enable the **Prepayment customer invoice feature** feature under feature management. Meanwhile, the following settings have to be ensured before starting the prepayment invoice process.  

Go to Inventory Management >> Setup >> Posting >> Posting >> Sales Order >> Prepayment, maintain the default ledger account for the posting with the type “Customer prepayment”. 

Complete the setup for Posting profile with prepayment journal voucher under Accounts receivable parameters >> Ledger and sales tax >> Payment. 

Setup the number sequence for Prepayment invoice, Prepayment invoice voucher, Prepayment invoice reversal and Prepayment invoice reversal voucher under Accounts receivable parameters >> Number sequences.  

Enable the background process “Automated prepayment settlement posting” under System administration > Setup by clicking the button “Initialize process automations” if the task is not listed under tab background
processes. Update the interval for this process automation to 1 minute. 

Enable the electronic reporting configurations by going to the Electronic Reporting Tile >> Reporting Configuations tile >> Exchange >> Load from XML file. 

Import the Customer Prepayment Invoice Model xml file 

Import the Prepayment Invoice template xml file 

Import the Customer Prepayment Invoice Model Mapping xml file   

The above files can be fetched from Dataverse. 

### Overview of the prepayment invoice process 

The basic process of customer prepayment invoicing feature contains the steps: 
1. Define a prepayment value on the sales order
2. Confirm and post a prepayment invoice.
3. Settle the prepayment invoice.
4. Apply the prepayment invoice to the final invoice.  

### Create prepayment proposal 

When you create the sales order, you can define the prepayment amount by following these steps: 

1. Access prepayment proposal: Navigate to the sales order and click on the "Payment proposal" under the tab "Invoice" >> "Prepayment".
2. Select prepayment type: There are two types of prepayment type, percentage and fixed. When the prepayment type is set to percentage, the "Prepayment value" field is enabled. This field represents the percentage
of the total sales order amount that will be required as the prepayment. The calculated prepayment amount will be displayed in the "Total prepayment amount" field. When the prepayment type is set to fixed, only the
field “Total prepayment amount” is enabled and it requires you to enter the prepayment amount directly. A value which is higher than the sales order amount will not be accepted.   
3. Select sales category: The "Sales category" field requires you to select the appropriate sales category, which will determine the revenue account according to the posting settings. 

### Generate prepayment invoices 

Once the prepayment proposal is confirmed, you can generate the prepayment invoice by: 
1. Access prepayment invoice: Click on the "Prepayment invoice" button under the tab "Invoice" > "Prepayment."
2. Review and post prepayment Invoice: The page displays the overall prepayment invoice information, including the customer invoice account, date, prepayment invoice number, prepayment status, and prepayment amount.
3. By clicking the "Post" button, the open customer transaction will be generated, and the prepayment invoice status will change to "Pending. 

### Settle the prepayment invoice 

When you receive the payment for the prepayment, the customer payment journal will be posted to settle the prepayment invoice amount. After prepayment invoice settlement, the status of the prepayment invoice will
be changed to “Received” and the “Apply prepayment” action will be enabled.  

### Post the invoice with prepayment application 

By clicking the button “Apply prepayment”, it will open the form “Apply prepayment”. You can apply the prepayment by selecting the prepayment entry from the list “Select prepayments to apply” first and clicking the
button “Apply prepayment”. 

After posting the sales order invoices, the selected prepayment will be applied to the invoice when the process automation job “Automated prepayment settlement posting” is successfully executed. Then you just need
to pay the remaining amount of the sales order invoices with the customer payment journal, which should only show up the outstanding open amount to be received. 

 
