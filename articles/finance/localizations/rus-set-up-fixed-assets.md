---
# required metadata

title: Set up fixed assets (Russia)
description: This topic explains how to set up fixed assets for Russia.
author: ShylaThompson
ms.date: 02/20/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Set up fixed assets (Russia)

[!include [banner](../includes/banner.md)]

## Set up fixed asset value models

You define a value model so that you can create fixed asset transactions in the general ledger for accounting functions, such as tax and business transactions. You can also create submodels and depreciation groups for each value model.

Follow these steps to set up value models for fixed assets.

1. Select **Fixed assets (Russia)** \> **Setup** \> **Value models**.
2. Select **New** to create a value model.
3. In the **Value model** field, enter the code for the value model.
4. In the **Name** field, enter the name of the value model.
5. In the **Currency** field, select the currency code for the fixed asset value model.
6. In the **Round-off** field, enter the value that is used to round amounts.
7. In the **Posting profile** field, select the posting profile that is used to post fixed asset transactions.
8. In the **Posting profile (Shortage)** field, select the posting profile that is used to write off fixed assets.
9. In the **Posting layer** field, select a posting layer for value model transactions:

    - **Current** − The value model is used for all general business transactions and corrections (accounting purpose).
    - **Operations** – The value model is used for unique business transactions and corrections that are part of the periodic financial reporting for internal purposes.
    - **Tax** − The value model is used for tax accounting purposes.

        > [!NOTE]
        > A separate posting profile must be configured for the tax value model, because the value of the fixed asset tax account is based on off-balance accounts.

10. Optional: On the **FA value submodels** FastTab, follow these steps to create submodels or derived models for the value model:

    1. Select **Add** to create a submodel.
    2. In the **Value model** field, select a derived model for the value model.
    3. In the **Transaction type** field, select the type of transaction that the derived model is associated with.

11. Select **Depreciation groups** to define depreciation groups for the value model. For more information, see [Set up depreciation groups](rus-depreciation-setup.md#set-up-depreciation-groups).

## Set up fixed asset posting profiles

You can set up posting profiles for fixed assets. Posting profiles define the ledger accounts that are used for each fixed asset transaction.

1. Select **Fixed assets (Russia)** \> **Setup** \> **Posting profiles**.
2. Select **New** to create a fixed asset posting profile.
3. In the **Posting profile** field, enter the name of the posting profile.
4. In the **Description** field, enter a description of the posting profile.
5. On the **Ledger accounts** FastTab, in the drop-down list, select the type of transactions that the posting profile is used for:

    - **Depreciation** – Depreciation is calculated for a fixed asset.
    - **Depreciation revaluation** – The depreciation that is calculated for a fixed asset is revaluated.
    - **Major repairs** – Major repairs are done for a fixed asset.
    - **Putting into operation** – A fixed asset is put into operation.
    - **Cost revaluation** – The cost of a fixed asset is revaluated.
    - **Disposal (sale)** – A fixed asset is disposed of through sale.
    - **Disposal (dismantlement)** – A fixed asset is disassembled.
    - **Partial take-down** – A fixed asset is partially disposed of.
    - **Currency cost revaluate** – A fixed asset is revaluated based on the currency cost.
    - **Currency depreciation revaluate** – The depreciation that was calculated for a fixed asset is revaluated in accounting currency.
    - **Others** – Select this option for other fixed asset transactions.

6. In the **Groupings** field, select the grouping to use for the posting profile:

    - **Table** – Select this option to retrieve fixed asset data (values) from the table.
    - **Group** – Select this option to retrieve a defined depreciation group from the fixed asset group.
    - **All** – Select this option to retrieve all fixed asset transactions.
    - **Accounting** – Select this option to retrieve a defined value model.

7. In the **Account/Group number** field, select the value model, group, or fixed asset object that the posting profile should be used for.
8. In the **Ledger account** field, select the account number of the ledger account (debit) for the transactions.
9. In the **Offset account** field, select the account number of the offset account (credit) for the transactions.
10. Select **Options**, and then select a transaction type:

    - Disposal (sale)
    - Disposal (dismantlement)
    - Partial dismantlement
    - Lease
    - Return from lease
    - Writing-off
    - Receipt
    - Transference
    - Depreciation bonus

    A page appears, where you can define the posting for different types of amounts for the selected transaction type.

11. Select **New** to create a line. For example, for the **Disposal (sale)** fixed asset transaction type, you can create lines to define the following posting.

    | Valid for | FA relation | Amount to post      | Gain/loss | Main account | Offset account |	
    |-----------|-------------|---------------------|-----------|--------------|----------------|
    | All	    |             | Net book value      | All       | 01.300	   | 91.200	        |
    | All	    |             | Balance cost	    | All       | 01.100	   | 01.300	        |
    | All	    |             | Booked depreciation | All       | 02.010	   | 01.300	        |
    | All	    |             | Gain/Loss		    | Loss      | 99.100	   | 91.200	        |
    | All	    |             | Gain/Loss		    | Gain	    | 91.100	   | 99.100	        |

12. In the **Valid for** field, select the grouping to use for the posting profile:

    - **Table** – Select this option to retrieve fixed asset data (values) from the table.
    - **Group** – Select this option to retrieve a defined depreciation group from the fixed asset group.
    - **All** – Select this option to retrieve all fixed asset transactions.
    - **Accounting** – Select this option to retrieve a defined value model.

13. In the **FA relation** field, select the value model, group, or fixed asset object that should be used for the posting profile.
14. In the **Amount to post** field, select the type of amount to post to the specified account.
15. In the **Gain/loss** field, select the type of amount to post:

    - **All** – Any amount
    - **Loss** – The amount of loss
    - **Gain** – The amount of gain

16. In the **Ledger account** field, select the account number of the ledger account (debit) for the transactions.
17. In the **Offset account** field, select the account number of the offset account (credit) for the transactions.
18. Select the **Don't show in journal** check box if gain/loss transactions should not be shown in a fixed asset journal.

## Set up fixed asset groups

Fixed asset groups are used to group fixed assets. By defining fixed asset groups, you accomplish the following goals:

- Simplify the setup of fixed assets and posting profiles for fixed assets.
- Simplify the creation of queries and reports.
- Create a template, so that default shared information is copied into the records for new and similar fixed assets that the company acquires.

Use the **FA groups** list page to define fixed asset groups for accounting of fixed assets, working clothes, special rigging, and not-valuable fixed assets (NVFAs). To each group that you define, you assign an appropriate type by using the **Type of group** field. You can also use the **FA group value models** page to set up value models for the fixed asset groups that you define, and can specify the duration of an asset's wear or usage period.

1. Select **Fixed assets (Russia)** \> **Setup** \> **FA groups**.
2. Select **New** to create a fixed asset group.
3. In the **FA group** field, enter the code for the fixed asset group.
4. In the **Name** field, enter the name for the fixed asset group.
5. In the **Type of group** field, select **Fixed assets**, **Working clothes**, **Special rigging**, or **NVFA** as the type of fixed asset group.
6. In the **VAT refunding** field, select the start date for refunding value-added tax (VAT) for the fixed assets in the group:

    - **Acquisition date** – Start to refund VAT from the acquisition date.
    - **Depreciation run date** – Start to refund VAT from the date of depreciation.

7. Select the **Autonumeration FA** check box to automatically generate fixed asset numbers when fixed assets are created for the group on the **Fixed assets** page.
8. In the **FA autonumbering sequence** field, select a number sequence for automatic number generation.
9. Select the **Barcodes autonumeration** check box to automatically generate bar codes for the fixed assets in the group.
10. In the **Barcode autonumeration sequence** field, select a number sequence for automatic bar code generation.
11. Select **Value models** to open the **FA group value models** page.
12. In the **Value model** field, select a value model for the fixed asset group.
13. In the **Depreciation group** field, select a depreciation group for the fixed asset group.

    > [!NOTE]
    > When you create a fixed asset for a specific fixed asset group, the value model and depreciation group that you define on this page are entered by default on the **Value models** page and can't be changed.

14. Set the **Service life by rate** option to **Yes** to specify the wear or usage period for the asset, based on the lifetime that is specified on the **Working clothes/Special rigging/NVFA issue journal** page during the issue process. If this option is set to **No**, the usage period is determined by the depreciation group.

    > [!NOTE]
    > The **Service life by rate** option is available only when you select **Working clothes**, **Special rigging**, or **NVFA** in the **Type of group** field on the **FA groups** page. If you set this option to **Yes**, the lifetime that is specified on the **Issue and usage rates** page is entered in the **Lifetime** field on the **Working clothes/Special riggings/NVFA issue journal lines** page when you create an issue journal for the asset. The lifetime is updated on the working clothes or special rigging card.

## Set up fixed asset parameters

1. Select **Fixed assets (Russia)** \> **Setup** \> **Parameters**.
2. On the **Fixed assets** tab, on the **General** FastTab, in the **Base value model** field, select the value model for accounting.
3. In the **Tax value model** field, select the value model for tax accounting.
4. In the **Minimal depreciation** field, enter the minimum depreciation amount when a fixed asset is depreciated by using the **Reducing remainder** method.
5. Set the **Allow multiple putting into operation** option to **Yes** to allow multiple acquisitions to be entered (put into operation).

    > [!NOTE]
    > If this option is set to **Yes**, you can register multiple acquisition transactions for a fixed asset. Therefore, you can register changes in the cost of the asset over time.

6. Set the **Autonumeration FA** option to **Yes** to activate automatic numbering.
7. Set the **Barcode equals FA number** option to **Yes** to automatically assign bar codes for fixed asset numbers.

    > [!NOTE]
    > If this option is set to **Yes**, a bar code number that is the same as the fixed asset number is automatically generated for a fixed asset. This bar code number will be shown on the **Fixed assets** page.

8. Set the **Barcodes autonumeration** option to **Yes** to automatically number bar codes by using a number sequence.

    > [!NOTE]
    > This option is available only if the **Barcode equals FA number** option is set to **No**.

9. In the **Round-off** field, enter the value that transaction amounts must be rounded by for accounting purposes.
10. In the **Posting profile** field, select the default posting profile that should be used if no posting profile is specified for the value models.
11. In the **Language** field, select a language for the fixed asset documents.
12. In the **Reservation** field, select **Manual**, **Automatic**, or **Explosion** to specify the type of reservation that is done for items during assembly or disassembly of a fixed asset.
13. On the **Reason codes** FastTab, set the **Require reasons for asset changes** option to **Yes** if a reason must be entered for the fixed asset transactions that you will select in the next step.
14. In the **Not required** list, select the fixed asset transactions that reason codes must be entered for, and move them to the **Required** list.
14. On the **Tax reporting** tab, in the **Assessed tax**, **Transport tax**, and **Land tax** sections, in the **Sales tax code** field, select a sales tax code. Then, in the **Compression** field, select the level of compression:

    - **Tax** – When you create a fixed asset tax journal in the ledger, the details of the journal lines are generated according to the tax codes.
    - **Total** – When you generate transactions in the fixed asset tax journal in the ledger, the total of the transactions is generated. The details of the journal lines aren't generated according to the tax codes.

15. On the **Document** tab, select the analysis code, and set up the number sequences for fixed asset documents.
16. On the **Financial dimensions** tab, select the financial dimension codes for the fixed asset transactions.
17. On the **Number sequences** tab, select a number sequence for **FA inventory number**, **Bar code**, **FA revaluation**, **FA counting**, **FA transfer**, **Writing off on condition**, and **Assessed tax register journal number**.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]