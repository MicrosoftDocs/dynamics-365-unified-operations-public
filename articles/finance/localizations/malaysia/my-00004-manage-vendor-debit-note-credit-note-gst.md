--- 
title: MY-00004 Manage vendor debit notes and credit notes for GST
description: Learn how to create and print vendor debit note and credit note tax invoices for Lithuania in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.reviewer: johnmichalak   
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: PurchTable, PurchCreateOrder, InventItemIdLookupPurchase, VendInvoiceJourLookup_MY, TaxGroupLookup, TaxTmpWorkTrans, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, SrsReportViewerForm, DefaultDashboard 
ms.custom: 
  - bap-template
---

# MY-00004 Manage vendor Debit note and Credit note for GST

[!include [banner](../../includes/banner.md)]

This article explains how to create and print vendor debit note and credit note tax invoices for Lithuania in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to create and print vendor debit note and credit note tax invoices. You must be in the accounting receivable clerk role to complete the procedures.

The procedures use the demo data company MYMF.

## Create and print a vendor debit note

To create and print a vendor debit note, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand or collapse the **General** section.
1. In the **Site** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Warehouse** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**.
1. In the **Reason** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Line** view.
1. In the list, mark the selected row.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. In the **Original invoice number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Line details** section.
1. Select **Save**.
1. Select the **Setup** tab.
1. In the **Item sales tax group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Sales tax group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. On the Action Pane, select **Purchase**.
1. Select **Sales tax**.
1. Validate the calculated tax amount for the tax code "AJP".  
1. Select **OK**.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. On the Action Pane, select **Invoice**.
1. In the **Number** field, enter a value.
1. On the Action Pane, select **Process**.
1. Select **Print setup**.
1. Select **Print options**.
1. Select or clear the **Print invoice** checkbox.
1. Select **OK**.
1. Select **Default from: Ordered quantity** to open the drop dialog.
1. In the **Default quantity for lines** field, select an option.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Verify that the debit note report printed with GST looks correct.  

## Create and print a vendor credit note

To create and print a vendor credit note, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable \> Purchase orders \> All purchase orders**.
1. Select **New**.
1. In the **Vendor account** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand or collapse the **General** section.
1. In the **Site** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Warehouse** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**.
1. In the **Reason** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Line** view.
1. In the list, mark the selected row.
1. In the **Item number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. In the **Original invoice number** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Line details** section.
1. Select the **Setup** tab.
1. In the **Item sales tax group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Sales tax group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. Select **Save**.
1. On the Action Pane, select **Purchase**.
1. Select **Sales tax**.
1. Validate the calculated sales tax.  
1. Select **OK**.
1. On the Action Pane, select **Purchase**.
1. Select **Confirm**.
1. On the Action Pane, select **Invoice**.
1. In the **Number** field, enter a value.
1. Select **Post**.
1. Select **OK**.
1. Verify that everything looks correct on the credit note report with GST.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
