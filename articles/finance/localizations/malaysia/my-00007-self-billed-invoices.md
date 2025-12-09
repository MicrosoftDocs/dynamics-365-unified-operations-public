--- 
title: MY-00007 Self-billed invoices
description: Learn how to create and print a vendor self-billed invoice for Malaysia in Microsoft Dynamics 365 Finance. 
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/09/2025
ms.reviewer: johnmichalak 
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: LedgerParameters, DefaultDashboard, PurchTable, PurchCreateOrder, EnumLookupForm_RU, InventItemIdLookupPurchase, TaxGroupLookup, TaxTmpWorkTrans, VendEditInvoice, VendEditInvoiceDefaultQuantityForLinesDropDialog, SrsReportViewerForm
ms.custom: 
  - bap-template
---

# MY-00007 Self-billed invoices

[!include [banner](../../includes/banner.md)]

This article explains how to create and print a vendor self-billed invoice for Malaysia in Microsoft Dynamics 365 Finance.

## Prerequisites

Before you print a self-billed invoice, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger parameters** and select the **Use self-billed invoice** option.
1. Sign in with the **Accounts payable clerk** role.

## Print a self-billed invoice

To print a self-billed invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts payable** \> **Purchase orders** \> **All purchase orders** and select **New**.
1. In the **Vendor account** field, select a value.
1. In the **General** section, in the **Site** field, select a value.
1. In the **Warehouse** field, select a value.
1. Select **OK**.
1. On the Action Pane, select **Options**.
1. Select **Change view** \> **Header view**.
1. In the **Invoice type** field, select a value.
1. In the **Approval number** field, enter a value, and then select **Save**.
1. In the list, mark the selected row.
1. In the **Item number** field, select a value.
1. In the **Unit price** field, enter a number.
1. In the **Line details** section, on the **Setup** tab, in the **Item sales tax group** field, select a value.
1. In the **Sales tax group** field, select a value and then select **Save**.
1. On the Action Pane, select **Purchase** \> **Sales tax.**
1. Verify that the calculated sales tax amount for tax code is correct, and then select **OK**.  
1. On the Action Pane, select **Purchase** \> **Confirm**.
1. On the Action Pane, select **Invoice** \> **Invoice** \> **Default from: Ordered quantity**.
1. In the **Default quantity for lines** field, select an option, and then select **OK**.
1. In the **Number** field, enter a value.
1. On the Action Pane, select **Process** \> **Print setup** \> **Print options**.
1. Select the **Print invoice** checkbox and then select **OK**.
1. Select **Post**, and then select **OK**.
1. Review the **Self-billed invoice** report for accuracy. Verify that the report includes the GST summary section, the GST code, the amount origin, the quantity, and the GST amount.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
