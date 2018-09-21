---
# required metadata

title: Depreciation bonus (Russia)
description: This topic provides information about depreciation bonuses for Russian fixed assets.
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

# Depreciation bonus (Russia)

[!include [banner](../includes/banner.md)]

You can calculate bonus depreciation by reducing the value of an asset by means other than the usual rate of depreciation. You can apply bonus depreciation amounts during the accounting period, after the asset is put into operation or after major repairBonus depreciation is always calculated and applied before other types of depreciation.

> [!NOTE]
> You can restore the bonus depreciation for a fixed asset only if you sell the fixed asset to an affiliated customer within five years of placing the fixed asset into operation. For more information, see [Set up an affiliated customer](#set-up-an-affiliated-customer).

## Set up bonus depreciation 

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation bonus**.
2.  Click **New** to create a new bonus depreciation allowance.
3.  In the **Depreciation bonus** field, enter a unique identification code to determine the bonus depreciation allowance and in the **Description** field, enter a description.
4.  In the **Depreciation bonus percent** field, enter the percentage of the depreciation bonus.

## Calculate a bonus depreciation 

The depreciation bonus is an additional depreciation amount that is assessed during the first year for some asset types that are operational. The depreciation bonus is calculated only for the tax value model. You must set up a posting profile before you can calculate the depreciation bonus for fixed assets.

1.  Click **Fixed assets (Russia)** \> **Periodic** \> **Depreciation bonus initialization**.
2.  In the **Value model** field, select a model for the depreciation bonus.
3.  In the **Depreciation bonus** field, select the bonus ID that you create in the **Depreciation bonus** form.
4.  Click **Records to include/ Filter** to open the **Inquiry** form. Then enter the selection criteria for the fixed asset or fixed asset group to create the transaction for.
5.  Click **OK**. The depreciation bonus percentage is updated in the **Depreciation bonus** field in the **FA transactions** form.
    
    > [!NOTE]
    > When you post a depreciation transaction, two transactions are created in the FA journal (**Fixed assets (Russia)** \> **Journals**) to register the depreciation and the depreciation bonus.

## Set up an affiliated customer 

Use the **Customers** page to affiliate a customer with an intercompany. If you sell a fixed asset to an affiliated customer within five years of placing the fixed asset into operation, then you can restore the bonus depreciation for the fixed asset.

1.  Click **Accounts receivable** \> **Common** \> **Customers** \> **All customers**.
    –or–
    Click **Sales and marketing** \> **Common** \> **Customers** \> **All customers**.
2.  On the **All customers** list page, on the **Action Pane**, click **Customer** to create a customer, or open an existing customer record.
3.  In the **Customers** page, on the **Invoice and delivery** FastTab, select the **Affiliated** check box to affiliate the customer with an intercompany.

## Additional resources

- [Depreciation setup (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-methods.md)
- [Depreciation calculation (Russia)](rus-depreciation-calculation.md)
