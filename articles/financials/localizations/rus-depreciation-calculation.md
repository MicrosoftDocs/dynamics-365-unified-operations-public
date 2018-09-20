---
# required metadata

title: Depreciation calculation (Russia)
description: This topic provides information about calculating depreciation for Russian fixed assets.
author: anasyash
manager: AnnBe
ms.date: 10/28/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Russia
ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---


[!include [banner](../includes/banner.md)]

## Calculate fixed asset depreciation

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  On the **List** tab, press the **New** button to create a new journal.
3.  In the **Name** field, select a journal name and in the **Description** field, view or modify the description of the journal.
5.  Click **Lines** to open the **Journal voucher** form.
6.  On the **List** tab, press the **New** button to open the **Add to journal** form to create a single depreciation transaction for one fixed asset.
    
    > [!NOTE]
    > Click <STRONG>Group operations</STRONG> &gt; <STRONG>Depreciation</STRONG> to create depreciation transactions for several fixed assets. Use **Record to include/ Filter** to open the **Inquiry** form to set criteria for fixed assets selections.

7.  In the **Transaction date** field, select the date of the next calculation period. If no depreciation was calculated for the previous periods, depreciation transactions are created in the journal for all months prior to the transaction date, excluding the month of the transaction.
8.  In the **Transaction type** field, select **Depreciation**.
9.  In the **FA number** field, select a fixed asset number.
10. In the **Value model** field, select a fixed asset value model. If you do not select a model, transactions for all value models are created in the journal.
11. In the **Reason code** field, select a reason code and in the **Reason comment** field, view or modify the reason for the depreciation transaction (if needed).
13. Click **OK**. Depreciation transactions are created in the journal for all value models that you set up in the **Value models** form.
14. Click **Validate** \> **Validate** to validate the transaction details.
15. Click **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

## Calculate or reverse depreciation using the tax group non-linear depreciation method 

You can calculate depreciation in tax accounting by using the linear method or the non-linear method. You can also calculate tax depreciation by using the tax non-linear group depreciation method. This method allows you to specify a depreciation rate for each group, or a depreciation factor for each subgroup, to calculate the depreciation amount that is accrued for each depreciation group or subgroup.

You can group the depreciation register lines by depreciation group or subgroup by using the **FA depreciation (nonlinear method)**, **IA depreciation (nonlinear method)**, **FA - information about object**, and **IA - object information** tax registers.

Use the following procedures to set up a method of depreciation, and to calculate or reverse depreciation by using the tax group non-linear depreciation method.

## Calculate fixed asset depreciation for fixed assets by using the tax non-linear group method

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select a journal name.
4.  In the **Description** field, modify the description of the journal.
5.  Click **Lines** to open the **Journal voucher** form.
6.  Click **Group operations** \> **Depreciation by group** to open the **Depreciation by group** form.
    
    > [!NOTE]
    > If you select the **Tax nonlinear group method**as the depreciation method, you cannot calculate the depreciation for a tax value model by using the single or group depreciation function.

7.  In the **Transaction date** field, select the date of the transaction.
8.  Click **Select** to open the **Inquiry** form, and then enter the selection criteria for the fixed assets.
9.  Click **OK**. Depreciation transactions are created in the journal.
10. Click **Validate** \> **Validate** to validate the journal.
11. Click **Post** \> **Post** to post the journal. Corresponding fixed asset and ledger transactions are created.

## Calculating depreciation bonus

The depreciation bonus is an additional depreciation amount that is assessed during the first year for some operational asset types. You must set up a posting profile and create an acquisition journal before you calculate the fixed asset depreciation bonus.

Use the **Depreciation bonus** form to calculate the depreciation bonus for fixed assets by using the **Tax nonlinear group method** as the depreciation method. When you create the depreciation transactions, a depreciated bonus is calculated for every asset. The bonus amount is calculated first, and then the depreciation from the cost is calculated, excluding the bonus. The bonus amount is not included in the total balance of the depreciation group.

## Reverse fixed asset depreciation

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  On the **List** tab, press the **New** button to create a new journal.
3.  In the **Name** field, select a journal name and in the **Description** field, view or modify the description of the journal.
4.  Click **Lines** to open the **Journal voucher** form.
5.  Click **Group operations** \> **Storno of depreciation** to open the **Storno of depreciation** form.
6.  In the **Date of storno** field, select a date for the depreciation reversal.
7.  In the **Accounting** field, select a fixed asset value model.
8.  Click **Record to include/ Filter** to open the **Inquiry** form, and then enter the selection criteria for fixed assets.
9.  Click **OK**. Depreciation reversal transactions are created in the journal.
10. Click **Validate** \> **Validate** to validate the transaction details.
11. Click **Post** \> **Post** to post the journal. The fixed asset depreciation transaction is reversed and the ledger transaction is updated accordingly.

## Additional resources

- [Depreciation setup (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-methods.md)
