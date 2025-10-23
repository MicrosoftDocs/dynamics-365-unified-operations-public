--- 
title: Audit invoices and key data in accounts payable
description: Learn how to audit invoices and key data in accounts payable.
author: kweekley
ms.author: kweekley
ms.topic: how-to
ms.date: 09/05/2025
ms.custom:
ms.reviewer: twheeloc   
audience: Application User  
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: PurchTable, PurchCreateOrder, PurchEditLines, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog,  VendJournalMatch_PackingSlip, VendInvoiceMatchingDetails
ms.dyn365.ops.version: Version 7.0.0 
---

# Audit invoices and key data in accounts payable

[!include [banner](../../includes/banner.md)]

When you receive an invoice from a vendor for goods or services on a purchase order, the business processes might require that the goods or services be received before the invoice can be approved for payment. Before you begin, make sure that the Invoice matching configuration key is selected. 

In the **Accounts payable parameters** page, select **Enable invoice matching validation**, set the **Post invoice with discrepancies** field to **Require approval**, and the **Line matching policy** field is set to **Three-way matching**.

This procedure uses the USMF demo company. The accounts payable manager or accounting manager role would perform these steps.


## Create a purchase order
1. Go to **All purchase orders**.
2. Click **New**.
3. In the **Vendor account** field, type a value.
4. Click **OK**.
5. Click **Add line**.
6. In the **Item number** field, type a value.
7. On the Action Pane, click **Purchase**.
8. Click **Confirm**.

## Post a product receipt
1. On the Action Pane, click **Receive**.
2. Click **Product receipt**.
3. In the **Product receipt** field, type a value.
4. Click **OK**.

## Record and match a vendor invoice to a product receipt
1. On the Action Pane, click **Invoice > Invoice**.
2. In the **Number** field, type a value.
3. Click **Default from: Ordered quantity** to open the drop dialog.
4. In the **Default quantity for lines** field, select an option.
5. Click **OK**.
6. Click **Yes**.
7. Click **Match product receipts**.
8. Click **OK**.
9. On the Action Pane, click **Review**.
10. Click **Matching details**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
