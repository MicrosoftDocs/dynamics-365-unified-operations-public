---
# required metadata

title: Maintain fixed assets 
description: This topic explains how to inactivate, reactivate, and update a fixed asset in Microsoft Dynamics 365 Finance in Russia.
author: ShylaThompson
ms.date: 07/28/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

#ms.search.form:  
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

# Maintain fixed assets
[!include [banner](../includes/banner.md)]

If a fixed asset is closed down or inactive for more than three months, or if refurbishment of the asset is conducted for more than 12 months, calculation of depreciation is suspended. It resumes when the fixed asset is put back into operation.
For example, a fixed asset may be inactivated in the case of capital improvements.
"Capital improvements" is a special asset category that includes capital renovations, improvements, technical updates, additional construction, and the acquisition of additional equipment for a fixed asset. When you update capital improvements, calculated depreciation isn't revalued. However, the depreciated cost and service life of the fixed asset are changed.


## Temporarily inactivate a fixed asset

1. Select **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select the fixed asset to temporarily inactivate. The status of the asset is currently **In operation**.
3. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Temporary closing-down** to open the **Temporary closing-down** page.
4. In the **Start date** field, select the inactivation date, and then close the page. The status of the asset is updated to **Temporary closing-down**.

    > [!NOTE]
    > Depreciation isn't accrued while the status of a fixed asset is **Temporary closing-down**.

## Reactivate a fixed asset

1. Select **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select the fixed asset that has a status of **Temporary closing-down**.
3. On the Action Pane, on the **Fixed asset** tab, in the **History** group, select **Temporary closing-down** to open the **Temporary closing-down** page.
4. In the **Finish date** field, select the reactivation date, and then close the page.

    > [!NOTE]
    > Depreciation is calculated from the date that is specified in the **Depreciation start date** field on the **Depreciation groups** page.

## Post an update for a major repair of a fixed asset

You must complete the following tasks before you can post an update for a major repair of a fixed asset:

1. Create dimensions for depreciation. For more information, see [Define financial dimensions](../general-ledger/tasks/define-financial-dimensions.md).
2. Set up expense codes. 
3. Set up bonus depreciation.
4. Set up depreciation groups.

### Create a journal for a major repair of a fixed asset

1. Select **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2. Create a fixed asset (FA) journal.
3. In the **Name** field, select a journal name.
4. In the **Description** field, view or modify the description of the journal.
5. Select **Lines**.
6. Create a journal line.
7. In the **Transaction date** field, select the date to update the transaction on.
8. In the **Transaction type** field, select **Major repairs**.
9. In the **FA inventory number** field, select the fixed asset number.
10. In the **Value model** field, select the value model of the fixed asset.
11. In the **Reason code** field, select a reason code.
12. In the **Reason comment** field, update the reason for the major repair of the fixed asset.
13. Select **OK**. The improvement lines for the asset are shown in the journal.
14. In the **Description** field, select transaction text.
15. In the **Debit** or **Credit** field, enter the transaction amount.
16. In the **Offset account type** field, select the type of offset account.
17. In the **Offset account** field, select the offset account number.

    > [!TIP]
    > You can also select **Group operations** \> **Major repairs** on the Action Pane to create transactions for several fixed assets.

18. On the Action Pane, select **Post** \> **Post** to post the journal.

### Update a value model for a fixed asset

1. Select **Fixed assets (Russia)** \> **Common** \> **Fixed assets**.
2. Select a fixed asset, and then, on the Action Pane, select **Value models**.
3. On the Action Pane, select **FA lifetime history**.
4. Select **New**, and then in the **Date** field, select the date of the lifetime change.
5. In the **New lifetime** and **New factor** fields, enter a lifetime and factor for the fixed asset.
6. In the **Depreciation method** and **Depreciation subgroup** fields, select a depreciation method and subgroup.
7. In the **Reason code** field, select a reason code.
8. In the **Reason comment** field, update the reason for the transaction.

> [!NOTE]
> When major repair work is done on a fixed asset, bonus depreciation can be applied to the asset on or after the transaction date of the major repair. You can create a transaction for a major repair of a fixed asset, and you can specify the bonus depreciation and bonus start date. The start date of the bonus depreciation can be the same as the transaction date of the major repair, or it can be the next depreciation date.

## Reverse major repair transactions
By default, when you reverse transactions, the reversal date is equal to the original transaction date. However, you can specify a different reversal date.

1. Go to **Fixed assets (Russia)** > **Fixed assets**, and on the Action Pane, select **Value models**.
2. On the **FA value models** page, on the Action Pane, select **Transactions**.
3. On the **FA transactions** page, select and transaction and on the Action Pane, select **Reverse transaction**.
4. In the **Reverse transactions** dialog box, change the transaction reversal date as needed and then select **OK**. A transaction to reverse the original transaction is created and added to the **FA transactions** page.
5. Select **Voucher**, and on the **Voucher transactions** page, view the transactions in the ledger.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
