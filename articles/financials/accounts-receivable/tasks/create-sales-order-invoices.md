--- 
# required metadata 
 
title: Create sales order invoices
description: This task guide describes invoicing a sales order, including merging invoices and batch processing. 
author: ShivamPandey-msft
manager: AnnBe 
ms.date: 11/10/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Create sales order invoices

[!include[task guide banner](../../includes/task-guide-banner.md)]

This task guide describes invoicing a sales order, including merging invoices and batch processing. This procedure uses the USMF demo company.


## Create an invoice from a sales order
1. Go to Accounts receivable > Orders > Shipped but not invoiced sales orders.
2. Select a sales order in the list. 
3. On the Action Pane, click Invoice.
4. Click Invoice.
    * Note that this sales order has multiple packing slips associated with it. It will only show the word <multiple> instead of the packing slip number.  
5. Expand the Parameters section.
    * Posting must be set to Yes to post the invoice. You can also turn off posting and just print the invoice. However, you can accomplish the same result by creating a proforma invoice instead of an invoice.  
    * This option is used for batch jobs. The query is run when the batch job is run.    
6. In the Print field, select 'After'.
7. Select Yes for Print invoice.
    * Print management can print  multiple copies of the invoice and also send the invoice via email as a PDF file.  
8. In the Print charges field, select 'Summarize'.
9. In the Check credit limit field, select 'Balance'.
10. Click Cancel.

## Combine orders into a single invoice
1. Go to Accounts receivable > Orders > All sales orders.
2. Locate a customer that has multiple invoices open.
3. Select an open sales order.
4. Select another open sales order for the same customer.
5. On the Action Pane, click Invoice.
6. Click Invoice.
7. Expand the Parameters section.
8. In the Quantity field, select 'All'.
    * Note that there are two invoices listed in the overview section. Now let's merge them into a single invoice.  
9. In the Summary update for field, select 'Invoice account'.
10. Click Arrange to merge the sales orders into a single invoice.
    * The two sales orders are now merged into a single invoice.   
11. Click Cancel.
12. Click Yes.

## Post invoices in a batch
1. Go to Accounts receivable > Invoices > Batch invoicing > Invoice.
2. Click Select.
3. Click OK.
4. Click Batch.
5. Click on Yes to turn on batch processing.
6. Click Recurrence.
7. Select Days
8. Click OK.
9. Click OK.
10. Click Cancel.
11. Click Yes.

