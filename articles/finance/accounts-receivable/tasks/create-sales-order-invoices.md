--- 
title: Create sales order invoices
description: Learn about how to invoice a sales order, including merging invoices and batch processing. A step-by-step process for creating invoices from sales orders is provided.
author: JodiChristiansen
ms.author: jchrist
ms.topic: how-to
ms.date: 03/25/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesEditLines,  SysQueryForm, SysRecurrence
ms.dyn365.ops.version: Version 7.0.0 
---

# Create sales order invoices

[!include [banner](../../includes/banner.md)]

This article describes how to invoice a sales order, including merging invoices and batch processing. This procedure uses the USMF demo company.


## Create an invoice from a sales order
1. Go to **Accounts receivable > Orders > Shipped but not invoiced sales orders**.
2. Select a sales order in the list. 
3. On the **Action Pane**, click **Invoice > Generate > Invoice**. This sales order has multiple packing slips associated with it and will show the **Multiple** instead of the packing slip number.  
4. Expand the **Parameters** section.
    - Posting must be set to **Yes** to post the invoice. You can also turn off posting and just print the invoice. However, you can accomplish the same result by creating a proforma invoice instead of an invoice.  
    - This option is used for batch jobs. The query is run when the batch job is run.
5. In the **Print** field, select **After**.
6. Select **Yes** for **Print invoice**. Print management can print multiple copies of the invoice and also send the invoice via email as a PDF file.  
7. In the **Print charges** field, select **Summarize**.
8. In the **Check credit limit** field, select **Balance**.
9. Click **Cancel**.

## Combine orders into a single invoice
1. Go to **Accounts receivable > Orders > All sales orders**.
2. Locate a customer that has multiple invoices open.
3. Select multiple open sales orders from the same customer.
4. On the **Action Pane**, click **Invoice > Generate > Invoice**.
5. Expand the **Parameters** section.
6. In the **Quantity** field, select **All**. Note that there are two invoices listed in the **Overview** section. Now let's merge them into a single invoice.  
7. In the **Summary update for** field, select **Invoice account**.
8. Click **Arrange** to merge the sales orders into a single invoice. The two sales orders are now merged into a single invoice.   
9. Click **Cancel**.
10. Click **Yes**.

## Post invoices in a batch
1. Go to **Accounts receivable > Invoices > Batch invoicing > Invoice**.
2. Click **Select**.
3. Click **OK**.
4. Click **Batch**.
5. Select **Yes** in **Batch processing**.
6. Click **Recurrence**.
7. Select **Days**.
8. Click **OK**.
9. Click **OK**.
10. Click **Cancel**.
11. Click **Yes**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
