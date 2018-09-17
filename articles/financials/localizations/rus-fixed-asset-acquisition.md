---
# required metadata

title: Fixed asset acquisitions for Russia
description: This topic provides information about fixed assets acquisitions for Russia.
author: anasyash
manager: AnnBe
ms.date: 09/14/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
# ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Fixed asset acquisitions

[!include [banner](../includes/banner.md)]

The following depreciated property assets can be acquired (putting into operation):

-   Purchased assets
-   Assets obtained as a deposit in charter capital
-   Assets obtained under a gift agreement (obtained without compensation)
-   Assets obtained in exchange for other property
-   Unaccounted fixed assets discovered during inventory
-   Leased fixed assets, funds redeemed from a lessor

A credit account is used in all the above scenarios, which provides several options for creating correction transactions in the ledger. You can specify an account by creating a transaction manually in the Fixed asset journal, or by configuring the posting profiles for transactions for various types of fixed assets in the **Posting profiles** form (**Fixed asset (Russia) \> Setup \> Posting profiles)**.

The cost of an acquired fixed asset may differ from the purchase cost. For example, the cost might be increased by the addition of miscellaneous charges per acquisition, such as, testing and commissioning work.

Before you post a fixed asset acquisitions voucher, the depreciation parameters, such as service life and depreciation method, must be set up in the **Fixed asset value models** form (**Fixed assets \> Fixed assets \> Value models**).

The following updates take place when you post a **Putting into operation** transaction:

-   Fixed asset model transaction with **Putting into operation** type is created.
-   Voucher transactions with **Fixed assets (Russia)** transaction type and **Fixed assets (Russia), debit** posting type is created.
-   Inventory transactions in the case of fixed asset assembly with **Sold** issue status are created
-   FA balance is change for each value model in **Balance by FA** form (**Fixed assets \> Value models \> Balance button**)

You can put into operation one fixed asset, a group of fixed assets, or all fixed assets that have a **Bought** or **Scheduled** status.

There are two ways of acquiring (putting into operation) fixed assets:

-   A transaction for a single asset is created manually.
-   A transaction for one fixed asset, a fixed asset group, or all fixed assets with a **Bought** or **Scheduled** status is created automatically.

## Acquire a fixed asset 

Use the Fixed asset journal to create transactions for one fixed asset.

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Click **New** to create a fixed asset journal.
3.  In the **Name** and **Description** fields, select a journal name and enter a description for the journal.
4.  Click **Lines** button to open the **Journal voucher** form.
5.  Click the New button to create the journal voucher. The **Add to journal** form is open.
6.  In the **Add to journal** form, in the **Transaction date** field, set the transaction date.
7.  In the **Transaction type** field, select **Putting into operation**.
8.  In the **FA inventory number** field, select the inventory number of the fixed asset.
9.  In the **Depreciation bonus** and **Reason code** fields, select the reason code and depreciation bonus code (if needed).
  > [!NOTE]
  > You cannot modify the Value model field in this form, because the **Putting into operation** transactions are created for all value models at the same time.*
10.  Click **OK**. The lines with **Putting into operation** transaction type for the value models, registered in the fixed asset account, are created in the **Journal voucher** form.
11. Click **Validate** \> **Validate** to validate the transactions.
12. Click **Post** \> **Post** to post the transactions.
  >   Fixed asset and ledger transactions will be created. The fixed asset s tatus is updated to **In operation**.

  > [!NOTE] 
  > You can modify the text in the Transaction text field and the fixed asset amount acquired in the Amount field, if necessary. The suggested purchase price is displayed by default.

  > Information is displayed in the Offset account type and Offset account fields, based on the posting profile setting. You can change this information, if necessary.

Execute following steps to create transactions for several fixed assets at the same time,

1. Click **Group operations** \> **Putting into operation** button in the FA journal lines. The **Putting into operation** form is open.
2. Click the **Records to include**/ **Filter** to open the **Asset** form, where you can specify the values for one fixed asset, a fixed asset list, or a group of fixed assets, and then click **OK** button.
3. Fill in **Transaction date** field and **Depreciation bonus** and **Reason code** fields (if needed)
4. Click **OK** button. The lines with **Putting into operation** transaction type for the value models, registered in the fixed asset account, are created in the **Journal voucher** form.
5. Click **Validate** \> **Validate** to validate the transactions.
6. Click **Post** \> **Post** to post the transactions.

You may check posted transactions in the journal lines, if click **Inquiries \> Transactions** button or from the **Value models** form for each value model (**Fixed assets \> Value models \> Transactions**).

## Create standard printing forms
To create standard printing forms, complete the following steps.
1. Click **Documents \> Documents** in the fixed asset card and select one of the printing forms:
  -   **Inventory card** (\#FA-6)
  -   **Equipment acceptance statement** (№ FA-14)
2.  in the FA transaction form (**Fixed assets \> Value model \> Transactions**, transaction with **Putting into operation** type) click **Documents \> Documents**:
  -   Acceptance report (\#FA-1) and Transference statement (\#FA-1) – acceptance of fixed assets except buildings and encroachments
  -   Acceptance report (\#FA-1a) and Transference statement (\#FA-1a) – acceptance of buildings and structures
3.  Click **New** button to create the document record.
4.  Click **Print** button to create the document as excel file.
You may review all created document records in **Fixed assets** \> **Inquiries \>Documents**.

## Fixed asset assembly
You can assemble a fixed asset from the inventory items, and then to put the fixed asset into operation. When an assembled asset is put into operation, components are issued from the inventory based on their current cost.
1. Click **Fixed asset (Russia)** \> **Fixed assets \> Componentry** to open the **Componentry** form (if the fixed asset has **Bought** or **Scheduled** status)
2. In the upper pane, press **Add** button on the **Componentry** tab.
3. In the **Item** field, select an item which the fixed asset is assembled from.
4. In the **Quantity** field, enter the quantity of items that will be used to assemble the fixed asset.
  > The date of the transaction is displayed in the **Transaction date** field after putting the fixed asset into operation..
5. On the **Inventory dimension** tab, specify the warehouse dimensions, configuration (if needed) etc. that are used to write off the item from the inventory
  > If a fixed asset is built from items bought in one purchase, click the **From purchase** button and select the purchase with items for assembly in the **Requisition** form.
6. Click the **Add** button. All items included in the purchase are added to the **Componentry** form
7. Put the fixed asset into operation using **FA journal** (**Fixed asset (Russia) \> Journals \> FA journal**).
  > [!NOTE]
  > By default, the cost of acquiring the fixed asset is determined as the cost price amount of all components. Where necessary, you can modify the cost amount.

## Reverse acquisition transactions
When reversing transactions, you can specify a reversal date if it is different from the original transaction date. By default, the reversal date is equal to the original transaction date.
1.  Select **Fixed Assets \> Fixed Assets** *\>* **Value models** *\>* **Transactions**. 
2.  Click the **Reverse transaction** button.
  >   If needed, you can change the transaction reversal date in the **Reverse transaction** form**.**
3.  Click **OK**. A transaction to reverse the original transaction is created in the **FA transactions** form.
4.  Click the **Voucher** button to open the **Voucher transaction** form, where you can view the transactions in the ledger.
When reverse transactions are posted for all value models the fixed asset status is change to **Scheduled** or **Bought** depending on initial status of the fixed asset
If a reversed fixed asset was put into operation with components, then when posting reverse operations, the items are returned to inventory with the same cost price that they were issued from inventory when posting **Putting into operation** transaction. The inventory transactions are marked and, after inventory closing have the same cost price.
  > [!NOTE]
  > It is possible to reverse **Putting into operation** transaction via FA journal (**Fixed asset (Russia) \> Journals \> FA journal**)
