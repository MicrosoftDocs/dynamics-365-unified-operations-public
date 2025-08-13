---
title: Calculate depreciation for Russia
description: Learn how to calculate depreciation for Russian fixed assets in Microsoft Dynamics 365 Finance.
author: evgenypopov
ms.author: evgenypopov
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 08/15/2025
ms.reviewer: johnmichalak
ms.search.region: Russia
ms.search.validFrom: 2018-10-28
---

# Calculate depreciation for Russia

[!include [banner](../../includes/banner.md)]

This article explains how to calculate depreciation for Russian fixed assets in Microsoft Dynamics 365 Finance.

## Calculate fixed asset depreciation

To calculate fixed asset depreciation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
1. Select the **List** tab, and then select **New** to create a journal.
1. In the **Name** field, select a journal name.
1. In the **Description** field, you can change the description of the journal.
1. Select **Lines** to open the **Journal voucher** page.
1. Select the **Overview** tab, select **New** to open the **Add to journal** dialog, and create one depreciation transaction for one fixed asset.

    > [!NOTE]
    > To create depreciation transactions for several fixed assets, on the **Journal voucher** page, select **Group operations** \> **Depreciation** to open the **Depreciation** dialog. On the **Records to include** FastTab, select **Filter** to open the **Assets** dialog, where you can set the criteria that are used to select fixed assets.

1. In the **Transaction date** field, select the date of the next calculation period. If no depreciation was calculated for the previous periods, depreciation transactions are created in the journal for all months before the transaction date, except the month of the transaction.
1. In the **Transaction type** field, select **Depreciation**.
1. In the **FA inventory number** field, select a fixed asset number.
1. In the **Value model** field, select a fixed asset value model. If you don't select a model, transactions for all value models are created in the journal.
1. In the **Reason code** field, select a reason code. In the **Reason comment** field, you can change the reason for the depreciation transaction.
1. Select **OK**. Depreciation transactions are created in the journal for all value models that you set up on the **Value models** page.
1. Select **Validate** \> **Validate** to validate the transaction details.
1. Select **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

## Calculate or reverse depreciation by using the tax non-linear group depreciation method 

You can calculate depreciation for tax accounting by using the linear depreciation method or the non-linear depreciation method. You can also calculate tax depreciation by using the tax non-linear group depreciation method. This method lets you calculate the depreciation amount that is accrued for each depreciation group or subgroup. To use this method, you specify a depreciation rate for each group, or a depreciation factor for each subgroup.

You can group the depreciation register lines by depreciation group or subgroup by using the **FA depreciation (nonlinear method)**, **IA depreciation (nonlinear method)**, **FA - information about object**, and **IA - object information** tax registers.

Use the following procedures to set up a depreciation method, and to calculate or reverse depreciation by using the tax non-linear group method.

### Calculate fixed asset depreciation by using the tax non-linear group method

To calculate fixed asset depreciation by using the tax non-linear group method, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
1. Select **New** to create a journal.
1. In the **Name** field, select a journal name.
1. In the **Description** field, change the description of the journal.
1. Select **Lines** to open the **Journal voucher** page.
1. Select **Group operations** \> **Depreciation by group** to open the **Depreciation by group** dialog.

    > [!NOTE]
    > If you select **Tax nonlinear group method** as the depreciation method, you can't calculate the depreciation for a tax value model by using the single or group depreciation operation.

1. In the **Transaction date** field, select the date of the transaction.
1. On the **Records to include** FastTab, select **Filter** to open the **Assets** dialog, and then set the criteria that are used to select fixed assets.
1. Select **OK**. Depreciation transactions are created in the journal.
1. Select **Validate** \> **Validate** to validate the journal.
1. Select **Post** \> **Post** to post the journal. Corresponding fixed asset and ledger transactions are created.

### Calculating a depreciation bonus

The depreciation bonus is an additional depreciation amount that is assessed during the first year for some operational asset types. Before you can calculate the fixed asset depreciation bonus, you must set up a posting profile and create an acquisition journal.

Use the **Depreciation bonus** page to calculate the depreciation bonus for fixed assets by using the tax non-linear group depreciation method. When you create the depreciation transactions, a depreciation bonus is calculated for every asset. The bonus amount is calculated first, and then the depreciation from the cost is calculated. This depreciation excludes the bonus. The bonus amount isn't included in the total balance of the depreciation group. For more information, see [Depreciation bonuses (Russia)](rus-bonus-depreciation.md).

### Reverse fixed asset depreciation

To reverse fixed asset depreciation, follow these steps.

1. In Dynamics 365 Finance, go to **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
1. Select the **List** tab, and then select **New** to create a journal.
1. In the **Name** field, select a journal name.
1. In the **Description** field, you can change the description of the journal.
1. Select **Lines** to open the **Journal voucher** page.
1. Select **Group operations** \> **Storno of depreciation** to open the **Storno of depreciation** dialog.
1. In the **Date of storno** field, select a date for the depreciation reversal.
1. In the **Accounting** field, select a fixed asset value model.
1. On the **Records to include** FastTab, select **Filter** to open the **Assets** dialog, and then set the criteria that are used to select fixed assets.
1. Select **OK**. Depreciation reversal transactions are created in the journal.
1. Select **Validate** \> **Validate** to validate the transaction details.
1. Select **Post** \> **Post** to post the journal. The fixed asset depreciation transaction is reversed, and the ledger transaction is updated accordingly.

## Additional resources

- [Set up depreciation (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-methods.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
