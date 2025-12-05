---
title: Post vouchers from other modules, like sales invoices
description: This article describes how to post Chinese vouchers from the general ledger, inventory movement journals, sales invoices, and purchase invoices for China in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 12/05/2025
ms.reviewer: johnmichalak
ms.search.region: China (PRC)
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - InventJournalMovement, InventJournalCreate, InventItemIdLookupSimple, InventLocationIdLookup, InventProductDimensionLookup, DimensionLookup, InventTrans, SalesTableListPage, SalesCreateOrder, SalesTable, SalesEditLines
  - CustInvoiceJournal, CustTrans
ms.custom: 
  - bap-template
---

# Post vouchers from other modules, like sales invoices

[!include [banner](../../includes/banner.md)]

This article describes how to post Chinese vouchers from the general ledger, inventory movement journals, sales invoices, and purchase invoices for China in Microsoft Dynamics 365 Finance.

You can post Chinese vouchers from the general ledger, inventory movement journals, sales invoices, and purchase invoices. When you post from these sources, the system assigns the default Chinese voucher type and Chinese voucher number to those financial vouchers.

The following procedures walk you through posting Chinese vouchers from the Inventory movement journal and from a sales invoice.

Before you can complete these procedures, you must add the current fiscal year to the current fiscal calendar. This procedure uses the demo data company CNMF.

## Post Chinese vouchers from an inventory movement journal

To post Chinese vouchers from an inventory movement journal, follow these steps.

1. In Dynamics 365 Finance, go to **Inventory management \> Journal entries \> Items \> Movement**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **OK**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Date** field, enter a date.
1. In the **Item number** field, enter or select a value.
1. Close the page.
1. In the **Quantity** field, enter a number.
1. In the **Offset account** field, enter the desired values.
1. Select the **Inventory dimensions** tab.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. Close the page.
1. In the **Size** field, enter or select a value.
1. Select the **Financial dimension** tab.
1. Close the page.
1. In the **BusinessUnit** field, enter or select a value.
1. In the **CostCenter_CN** field, enter or select a value.
1. In the **Department_CN** field, enter or select a value.
1. Select **Save**.
1. Select **Validate**.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Select **Inventory**.
1. Select **Transactions**.
1. On the Action Pane, select **Ledger**.
1. Select **Financial** voucher. For example, the Chinese voucher type **Tran** is assigned.  

## Post Chinese vouchers from a sales invoice

To post Chinese vouchers from a sales invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Expand the **General** section.
1. Expand the **Administration** section.
1. Select **OK**.
1. In the list, mark the selected row.
1. In the **Item number** field, enter or select a value.
1. Close the page.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. Select the **Product** tab.
1. In the **Size** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. Close the page.
1. Select the **Price and discount** tab.
1. Select the **Financial dimensions** tab.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. In the **Deliver now** field, enter a number.
1. Select **Save**.
1. On the Action Pane, select **Invoice**.
1. Select **Invoice**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select an option.
1. Select **OK**.
1. Select **Invoice**.
1. Select **Transactions**.
1. Select **Voucher**. For example, you can see that the Chinese voucher type **Tran** is assigned.  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
