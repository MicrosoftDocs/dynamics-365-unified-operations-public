--- 
# required metadata 
 
title: Record vendor invoice and match against received quantity
description: When you receive an invoice from a vendor for goods or services on a purchase order, the business processes might require that the goods or services be received before the invoice can be approved for payment. 
author: ShivamPandey-msft
ms.date: 02/11/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PurchTable, PurchCreateOrder, PurchEditLines, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog,  VendJournalMatch_PackingSlip, VendInvoiceMatchingDetails   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Record vendor invoice and match against received quantity

[!include [banner](../../includes/banner.md)]

When you receive an invoice from a vendor for goods or services on a purchase order, the business processes might require that the goods or services be received before the invoice can be approved for payment. Before you begin, make sure that the Invoice matching configuration key is selected. 

In the **Accounts payable parameters** page, ensure that the **Enable invoice matching validation** option is selected, the **Post invoice with discrepancies** field is set to **Require approval**, and the **Line matching policy** field is set to **Three-way matching**.

This procedure uses the USMF demo company. The accounts payable manager or accounting manager role would perform these steps.


## Create a purchase order
1. Go to **All purchase orders**.
2. Click **New**.
3. In the **Vendor account** field, click the drop-down button to open the lookup.
4. In the **Vendor account** field, type a value.
5. Click **OK**.
6. Click **Add line**.
7. In the **Item number** field, type a value.
8. On the Action Pane, click **Purchase**.
9. Click **Confirm**.

## Post a product receipt
1. On the Action Pane, click **Receive**.
2. Click **Product receipt**.
3. In the list, mark the selected row.
4. In the **Product receipt** field, type a value.
5. Click **OK**.

## Record and match a vendor invoice to a product receipt
1. On the Action Pane, click **Invoice**.
2. Click **Invoice**.
3. In the **Number** field, type a value.
4. Click **Default from: Ordered quantity** to open the drop dialog.
5. In the **Default quantity for lines** field, select an option.
6. Click **OK**.
7. Click **Yes**.
8. Click **Match product receipts**.
9. Click **OK**.
10. On the Action Pane, click **Review**.
11. Click **Matching details**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
