--- 
# required metadata 
 
title: MY-00007 Self-billed invoices
description: This article explains how to create and print a vendor self-billed invoice. 
author: EvgenyPopovMBS
ms.date: 08/01/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: LedgerParameters, DefaultDashboard, PurchTable, PurchCreateOrder, EnumLookupForm_RU, InventItemIdLookupPurchase, TaxGroupLookup, TaxTmpWorkTrans, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, SrsReportViewerForm   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Malaysia
# ms.search.industry: 
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# MY-00007 Self-billed invoices

[!include [banner](../../includes/banner.md)]

This article explains how to create and print a vendor self-billed invoice. 

## Prerequisites
Before you can complete this procedure:

 - Select the **Use self-billed invoice** option on the **General ledger parameters** page
 - Be signed in with the **Accounts payable clerk** role

## Print a self-billed invoice
1. Go to **Accounts payable** > **Purchase orders** > **All purchase orders** and select **New**.
2. In the **Vendor account** field, select a value.
3. In the **General** section, in the **Site** field, select a value.
4. In the **Warehouse** field, select a value.
5. Select **OK** and on the Action Pane, select **Options**.
6. Select **Change view** > **Header view**.
7. In the **Invoice type** field, select a value.
8. In the **Approval number** field, enter a value and then select **Save**.
9. In the list, mark the selected row.
10. In the **Item number** field, select a value
11. In the **Unit price** field, enter a number.
12. In the **Line details** section, on the **Setup** tab, in the **Item sales tax group** field, select a value. 
13. In the **Sales tax group** field, select a value and then select **Save**.
14. On the Action Pane, click **Purchase** > **Sales tax.**
15. Verify that the calculated sales tax amount for tax code is correct and then select **OK**.  
16. On the Action Pane, click **Purchase** > **Confirm**.
17. On the Action Pane, click **Invoice** > **Invoice** > **Default from: Ordered quantity**.
18. In the **Default quantity for lines** field, select an option and then select **OK**.
19. In the **Number** field, enter a value.
20. On the Action Pane, select **Process** > **Print setup** > **Print options**.
21. Select the **Print invoice** check box and then select **OK**.
22. Select **Post** and then select **OK**.
23. Review the **Self-billed invoice** report for accuracy. Verify that the report includes the GST summary section, the GST code, the Amount origin, the Quantity, and the GST amount.    



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
