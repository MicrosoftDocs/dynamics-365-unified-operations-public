---
# required metadata

title: Register fixed assets acquisitions (Russia)
description: This topic walks you through registering fixed assets acquisitions for Microsoft Dynamics 365 Finance in Russia.
author: ShylaThompson
ms.date: 10/12/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Register fixed assets acquisitions (Russia)

[!include [banner](../includes/banner.md)]

You can register a fixed asset acquisitios using a vendor invoice journal or a purchase order. Typically, a vendor invoice journal is used if there is no need to track inventory movement of the fixed asset. For example, a fixed asset is bought and put into operation during the same period. A purchase order might be used if several identical fixed assets are bought or it is necessary to track inventory movement of a fixed asset. 

## Register a fixed asset acquisition using an invoice journal 

Before you can register the purchase of a fixed asset, the asset must be registered on the <STRONG>Fixed assets</STRONG> page.

1.  Go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**. On the Action pane, click **Fixed asset** to create a fixed asset, or select a fixed asset record.

2.  Click **New** to create a fixed asset with a **Scheduled** status.
    
3.  Click **Accounts payable** \> **Invoices** \> **Invoice journal**.

4.  Create a new journal and in the **Name** field, select the journal name.

5.  Click **Lines** to open the **Journal voucher** page.

6.  Create a new line.
    
    > [!NOTE]
    > The posting date and voucher number are displayed in the <STRONG>Date</STRONG> and <STRONG>Voucher</STRONG> fields.

7.  In the **Account type** field, select the **Vendor** account type. 
  
8.  In the **Account** field, select a vendor code.

9. In the **Invoice** field, enter the invoice number for the fixed asset purchase.

10. In the **Description** field, enter any notes about the invoice.

11. In the **Credit** field, enter the invoice amount.

12. In the **Offset account type** field, select the account type for the current account.

13. In the **Offset account** field, select the ledger account for the fixed asset before acquisition.

14. On the **General** tab in the **Currency** field, select the current invoice currency.

15. On the **Fixed asset** tab in the **FA inventory number** field, select the fixed asset number.

16. Click **Post** \> **Post** to generate the vendor and ledger transactions.
    
    > [!NOTE]
    > After posting the invoice, the status of the fixed asset is set to **Bought** on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**). If the fixed asset number is specified in the invoice journal line and the invoice journal is not posted, you cannot use this fixed asset in another invoice journal.
    
## Register a fixed asset acquisition using a purchase order 

You can register the purchase of a fixed asset by creating a purchase order. Before creating a purchase order, you should create a released product with a **Service** or **Item** product type. When you select an item with the **Service** product type in the purchase order line, you can enter several fixed assets, related with one purchase order line. When you select an item with the **Item** product type in the purchase order line, you can only enter one fixed asset. This fixed asset needs to be related to the purchase order line.  


1.  Go to **Product information management** \> **Common** \> **Released products**.

2.  Create a new item and in the **Item type** field, select **Service** or **Item**. On the **General** tab, fill in the **FA group** field. For more information, see [Create a released product for a single company](../../supply-chain/pim/tasks/create-released-product-single-company.md).

    > [!NOTE]
    > The information provided on the purchase line determines whether the fixed asset belongs to the specified fixed asset group.
    
3.  Click **Accounts payable** \> **Common** \> **Purchase orders** \> **All purchase orders**.
4.  Click **New** to create a new purchase order. For more information, see [Create a purchase order](../../supply-chain/procurement/tasks/create-purchase-order.md).
5.  Click the **Lines** tab in the lower pane.
6.  In the **Item number** field, select the item number, which is related to the fixed asset group. On the **Line detail/ Fixed asset** tab, enter the fixed assets (**Fixed asset (Russia)**). If you select an item with the **Service** product type in the purchase line you can enter several fixed assets. In this case, the quantity of fixed assets should be equal to the quantity that is specified on the purchase line. You can also enter a fixed asset on the purchase line, if you select the item with the **Item** product type.

7. Create the invoice. After posting invoice the fixed asset, the status will change to **Bought**.

## Reverse a fixed asset acquisition transaction    
    
When you create a reverse transaction, the information and amount of the original transaction are saved. By default, the reversal date and the original transaction date are the same. However, when reversing transactions, you can specify a reversal date that is different from the original transaction date. You can also reverse an amortization transaction using this process. 

1.  Go to **Fixed assets** \> **Common** \> **Fixed assets**. Click **Value Models**\> **Transactions** to open the **FA Transactions** page.

2.  Select the fixed asset acquisition transaction, and then click **Reverse transaction** to open the **Reverse transaction** page.

3.  In the **Reverse date**, select the transaction reverse date.

4.  Click **OK**. A transaction is created on the **FA transactions** page that reverses the original transaction.

5.  Click **Voucher** to view the transaction in the ledger on the **Voucher transactions** page.

    > [!NOTE]
    > To change the status to **Scheduled**, run the reverse acquisition transaction for all value models. If the asset that was reversed was built from inventory components, transactions are created to record the return of the components to the inventory. When you reverse an acquisition transaction, the cost price of the returned components may differ from the current warehouse cost price. However, after inventory closure, the components will reflect the current pricing.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]