---
# required metadata

title: Depreciation bonuses (Russia)
description: This topic provides information about depreciation bonuses for Russian fixed assets.
author: anasyash
ms.date: 04/20/2020
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
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Depreciation bonuses (Russia)

[!include [banner](../includes/banner.md)]

The depreciation bonus is an additional depreciation amount that is assessed during the first year for some asset types that are operational.

You can calculate a depreciation bonus by reducing the value of an asset through means other than the usual rate of depreciation. You can apply depreciation bonus amounts during the accounting period, after the asset is put into operation, or after major repairs. Depreciation bonuses are always calculated and applied before other types of depreciation.

> [!NOTE]
> You can restore the depreciation bonus for a fixed asset only if you sell the fixed asset to an affiliated customer within five years after you put the fixed asset into operation. For more information, see the [Set up an affiliated customer](#set-up-an-affiliated-customer) section.

## Set up a depreciation bonus

1. Select **Fixed assets (Russia)** \> **Setup** \> **Depreciation bonus**.
2. Select **New** to create a depreciation bonus allowance.
3. In the **Depreciation bonus** field, enter a unique identifier for the depreciation bonus allowance. In the **Description** field, enter a description.
4. In the **Depreciation bonus percent** field, enter the percentage of the depreciation bonus.

> [!NOTE]
> Depreciation bonuses can be used when you create a Fixed asset journal line for the **Putting into operation** transaction type. For more information, see [Acquiring fixed assets and putting them into operation](rus-fixed-asset-acquisition.md). When you post the Fixed asset journal, the system fills in the **Depreciation bonus** field in the fixed asset transaction of the **Putting into operation** transaction type. This information is then used when depreciation is calculated. 

## Calculate a depreciation bonus

The depreciation bonus is calculated only for the tax value model. You must set up a posting profile before you can calculate the depreciation bonus for fixed assets. Use the following procedure to fill in the depreciation bonus fields for all fixed asset transactions of the **Putting into operation** transaction type at the same time by using a filter that you set. 

1. Select **Fixed assets (Russia)** \> **Periodic** \> **Depreciation bonus initialization**.
2. In the **Value model** field, select a model for the depreciation bonus.
3. In the **Depreciation bonus** field, select the depreciation bonus ID that you created in the previous section.
4. On the **Records to include** FastTab, select **Filter** to open the **Inquiry** dialog box. Then enter criteria that are used to select the fixed asset or fixed asset group that the transaction should be created for.
5. Select **OK**. The depreciation bonus percentage is updated in the **Depreciation bonus** field on the **FA transactions** page.

    > [!NOTE]
    > When you post a depreciation transaction, two transactions are created in the Fixed asset journal (**Fixed assets (Russia)** \> **Journals** \> **FA journal**). One transaction registers the depreciation, and the other transaction registers the depreciation bonus.

## Set up an affiliated customer

Use the **All customers** page to affiliate a customer with an intercompany. If you sell a fixed asset to an affiliated customer within five years after you put the fixed asset into operation, you can restore the depreciation bonus for the fixed asset.

1. Select **Accounts receivable** \> **Customers** \> **All customers**.

    –or–

    Select **Sales and marketing** \> **Customers** \> **All customers**.

2. On the **All customers** list page, on the Action Pane, select **New** to create a customer, or open an existing customer record.
3. In the customer record, on the **Invoice and delivery** FastTab, set the **Affiliated** option to **Yes** to affiliate the customer with an intercompany.

## Additional resources

- [Set up depreciation (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-methods.md)
- [Calculate depreciation for Russia](rus-depreciation-calculation.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]