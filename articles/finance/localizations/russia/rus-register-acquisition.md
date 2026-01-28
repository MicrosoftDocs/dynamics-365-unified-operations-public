---
title: Register fixed assets acquisitions (Russia)
description: Learn how to register fixed assets acquisitions in Russia with Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/29/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Register fixed assets acquisitions (Russia)

[!include [banner](../../includes/banner.md)]

This article explains how to register fixed assets acquisitions in Russia with Microsoft Dynamics 365 Finance.

You can register a fixed asset acquisitios using a vendor invoice journal or a purchase order. Typically, a vendor invoice journal is used if there is no need to track inventory movement of the fixed asset. For example, a fixed asset is bought and put into operation during the same period. A purchase order might be used if several identical fixed assets are bought or it is necessary to track inventory movement of a fixed asset. 

## Register a fixed asset acquisition using an invoice journal 

Before you can register the purchase of a fixed asset, you must register the asset on the **Fixed assets** page.

To register a fixed asset acquisition using an invoice journal, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**. On the Action pane, select **Fixed asset** to create a fixed asset, or select a fixed asset record.
1. Select **New** to create a fixed asset with a **Scheduled** status.
1. Select **Accounts payable** \> **Invoices** \> **Invoice journal**.
1. Create a new journal and in the **Name** field, select the journal name.
1. Select **Lines** to open the **Journal voucher** page.
1. Create a new line.
    
    > [!NOTE]
    > The posting date and voucher number are displayed in the **Date** and **Voucher** fields.

1. In the **Account type** field, select the **Vendor** account type. 
1. In the **Account** field, select a vendor code.
1. In the **Invoice** field, enter the invoice number for the fixed asset purchase.
1. In the **Description** field, enter any notes about the invoice.
1. In the **Credit** field, enter the invoice amount.
1. In the **Offset account type** field, select the account type for the current account.
1. In the **Offset account** field, select the ledger account for the fixed asset before acquisition.
1. On the **General** tab in the **Currency** field, select the current invoice currency.
1. On the **Fixed asset** tab in the **FA inventory number** field, select the fixed asset number.
1. Select **Post** \> **Post** to generate the vendor and ledger transactions.
    
    > [!NOTE]
    > After posting the invoice, the status of the fixed asset is set to **Bought** on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**). If the fixed asset number is specified in the invoice journal line and the invoice journal is not posted, you cannot use this fixed asset in another invoice journal.
    
## Register a fixed asset acquisition using a purchase order 

You can register the purchase of a fixed asset by creating a purchase order. Before creating a purchase order, you should create a released product with a **Service** or **Item** product type. When you select an item with the **Service** product type in the purchase order line, you can enter several fixed assets, related with one purchase order line. When you select an item with the **Item** product type in the purchase order line, you can only enter one fixed asset. This fixed asset needs to be related to the purchase order line.  

To register a fixed asset acquisition using a purchase order, follow these steps:

1. In Dynamics 365 Finance, go to **Product information management** \> **Common** \> **Released products**.
1. Create a new item and in the **Item type** field, select **Service** or **Item**. On the **General** tab, fill in the **FA group** field. For more information, see [Create a released product for a single company](../../../supply-chain/pim/tasks/create-released-product-single-company.md).

    > [!NOTE]
    > The information provided on the purchase line determines whether the fixed asset belongs to the specified fixed asset group.
    
1. Select **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.
1. Select **New** to create a new purchase order. For more information, see [Create a purchase order](../../../supply-chain/procurement/tasks/create-purchase-order.md).
1. Select the **Lines** tab in the lower pane.
1. In the **Item number** field, select the item number, which is related to the fixed asset group. On the **Line detail/ Fixed asset** tab, enter the fixed assets (**Fixed asset (Russia)**). If you select an item with the **Service** product type in the purchase line you can enter several fixed assets. In this case, the quantity of fixed assets should be equal to the quantity that is specified on the purchase line. You can also enter a fixed asset on the purchase line, if you select the item with the **Item** product type.
1. Create the invoice. After posting invoice the fixed asset, the status will change to **Bought**.

## Reverse a fixed asset acquisition transaction    
    
When you create a reverse transaction, the information and amount of the original transaction are saved. By default, the reversal date and the original transaction date are the same. However, when reversing transactions, you can specify a reversal date that is different from the original transaction date. You can also reverse an amortization transaction using this process. 

To reverse a fixed asset acquisition transaction, follow these steps:

1. In Dynamics 365 Finance, go to **Fixed assets** \> **Common** \> **Fixed assets**. Select **Value Models**\> **Transactions** to open the **FA Transactions** page.
1. Select the fixed asset acquisition transaction, and then select **Reverse transaction** to open the **Reverse transaction** page.
1. In the **Reverse date**, select the transaction reverse date.
1. Select **OK**. A transaction is created on the **FA transactions** page that reverses the original transaction.
1. Select **Voucher** to view the transaction in the ledger on the **Voucher transactions** page.

    > [!NOTE]
    > To change the status to **Scheduled**, run the reverse acquisition transaction for all value models. If the asset that was reversed was built from inventory components, transactions are created to record the return of the components to the inventory. When you reverse an acquisition transaction, the cost price of the returned components may differ from the current warehouse cost price. However, after inventory closure, the components will reflect the current pricing.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
