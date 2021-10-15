---
# required metadata

title: Sell, dispose, and write-off assets (Russia)
description: This topic explains how to sell, dispose, and write-off assets in Microsoft Dynamics 365 Finance in Russia.
author: ShylaThompson
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Sell, dispose, and write-off assets (Russia)
[!include [banner](../includes/banner.md)]

## Fixed asset disposal 

You can dispose of fixed assets for any of the following reasons:

  - An asset is sold to other legal entities or private individuals.
  - An asset is transferred and used as a deposit in joint activities or as charter capital.
  - An asset is donated or used as another type of non-compensated transfer.
  - An asset is liquidated because of an accident or natural disaster.
  - An asset is exchanged through an exchange agreement.

There are three ways to create a disposal transaction:

  - **Leaving (sale)** – This transaction represents a fixed asset sale and can be entered in Accounts receivable or in the fixed assets journal. Several transactions are created in the ledger, based on the posting profile configuration. The status of the asset changes to **Written off (sale)**.

  - **Leaving (dismantlement)** – This transaction is entered in the fixed assets journal. Transactions are created in the ledger, and the remaining value of the asset after it has been dismantled is transferred to the inventory. The status of the asset changes to **Written off (dismantlement)**.

  - **Fixed Assets write-off** – This transaction is entered in the fixed assets journal, and the write-off transactions for the booked value and booked depreciation for the asset are created. The status of the asset changes to **Written off**


> [!NOTE]
> When you create a transaction for the partial write-off or disposal of a fixed asset, if the transaction accrues a loss, the transaction details are posted to a deferral account. This account contains the values of the calculated loss and the write-off time. The write-off time is calculated by using the fixed asset depreciation factor and the difference between the useful life of the depreciated asset and the actual period that the asset is used before its disposal. For more information, see [Set up the automatic creation of a deferrals account](#set-up-the-automatic-creation-of-a-deferrals-account).

You can record the sale of fixed assets in Fixed assets, or you can create a sales order or a free text invoice in Accounts receivable. When you sell a fixed asset, you must calculate its depreciation during that period.

Before creating a sales order, you should create a released product with a Service or Item product type. When you select an item with the Service product type in the sales order line, you can enter several fixed assets, related with one sales order line. When you select an item with the Item product type in the sales order line, you can only enter one fixed asset. This fixed asset needs to be related to the sales order line.

The status of an asset that is sold under a sales order or free text invoice is **Sold (waiting for posting)**, until the transaction is posted. After posting, the status of the asset is **Written off (sale)**.

> [!NOTE]
> You must set up posting profiles before you can create transactions for the sale of fixed assets.

If the invoice expenses are included in the sales order header when you sell a fixed asset or inventory asset, the sum of these miscellaneous charges is not included in the profit or loss from the sale.

However, if the invoice expenses are included in the order line that corresponds to the asset, the charges are considered when the profit or loss is calculated from the sale.



## Set up the automatic creation of a deferrals account 

1.  Click **Fixed assets** \> **Setup** \> **Depreciation group**.
2.  Click the **Deferrals** FastTab, and then set up the parameters for creating deferrals when a loss is realized.
3.  Select **Disposal** if you want to dispose of the fixed asset entirely, or **Partial dismantlement** to dispose of part of the fixed asset.
4.  Fill in  the **Model number**, **Deferrals group** and **Expense code** fields.



## Create a sales order for a fixed asset

1.  Click **Accounts receivable** \> **Common** \> **Sales orders** \> **All sales orders** and create a new sales order.
2.  Enter information about the sales order.
3.  Click the **Lines** tab in the lower pane. 
4.  In the **Item number** field, select the item number, which is related to the fixed asset group. On the **Line detail > Fixed asset** tab, enter the fixed assets (Fixed asset (Russia)). If you select an item with the Service product type in the sales line you can enter several fixed assets. In this case, the quantity of fixed assets should be equal to the quantity that is specified on the sales line. You can also enter a fixed asset on the sales line if you select the item with the Item product type. 

    > [!NOTE]
    > To create a new item, see [Create a released product for a single company](../../supply-chain/pim/tasks/create-released-product-single-company.md).
    >
    > Click **Inventory management** &gt; **Setup** &gt; **Inventory** &gt; **Item model groups**. If the **Physical negative inventory** check box is selected, then you can sell an item that is a fixed asset type without entering an inventory item. If not, you can sell an inventory asset that has a **Purchased** status.

12. Click **Posting** \> **Facture** to post the sales order.
13. Click **OK** to post the sales invoice. An invoice, facture, ledger, and fixed asset transactions are created, and the **Status** of the sales invoice changes to **Shipped**. The status of fixed asset changes to **Written off (sale)**. The **Disposal (sale)** and **Gain/Loss** fields are updated on the **FA balances** page. The **Disposal date** and **Disposal cost** fields are updated on the **FA Value models** page.

## Create a free text invoice for a fixed asset

1.  Click **Accounts receivable** \> **Common** \> **Free text invoices** \> **All free text invoices**.
2.  Press CTRL+N to create a new invoice. For more information, see [Create a free text invoice template](../accounts-receivable/create-free-text-invoice-template-new.md).
3.  In the **Customer account** field, select a customer account.
4.  In the **Date** field, enter an invoice date.
5.  In the **Currency** field, select an invoice currency.
6.  Create a new invoice line.
7.  In the **Ledger account** field, select the ledger account for posting the revenue to the current invoice line.
8.  In the **Sales tax group** field, select the sales tax group.
9.  In the **Item sales tax group** field, select the item sales tax group.
10. In the **Quantity** field, enter the quantity of fixed assets sold.
11. In the **Unit price** field, enter the sale value of the fixed asset unit.
12. In the **Measurement unit** field, select the unit of measurement unit for the fixed asset.
13. Click the **General** tab.
14. In the **FA number** field, select the fixed asset number.   
    > [!NOTE]
    > When including references to the fixed asset in an invoice line, its status changes to **Sold (waiting for posting)**.

15. Click **Posting** \> **Update facture** to open the **Post facture** page.
16. Click **OK** to post the facture. An invoice, facture, ledger, and fixed asset transactions are created, and the status changes to **Shipped**. The status of the asset is **Written off (sale)**.
17. Click **Fixed assets (Russia)** \> **Common** \> **Fixed assets** to open **FA Value Models** page. The disposal date and cost of the fixed asset are displayed in the **Disposal date** and **Disposal cost** fields.
18. Click **Balance** to open the **FA balances** page. The details are displayed in the **Leaving (sale)** and **Gain/Loss** fields.

## Reverse disposal transactions
To reverse a disposal transaction, create a credit note for the sales order or free text invoice related to the fixed asset, and then post the invoice.

## Reverse write-off and disposal transactions
By default, when you reverse a trnasaction, the reversal date is equal to the original transaction date. However, you can specify a different reversal date. 

1.	Go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
2.	On the **FA value models** page, on the Action Pane, select **Transactions**.
3.	On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**.
4.	In the **Reverse transactions** dialog box, change the transaction reversal date as needed, and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page.
5.	Select **Voucher** and on the **Voucher transactions** page, view the transactions in the ledger.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
