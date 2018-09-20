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

You can calculate bonus depreciation by reducing the value of an asset by means other than the usual rate of depreciation. You can apply bonus depreciation amounts during the accounting period, after the asset is put into service, and then depreciated. Bonus depreciation is available only for depreciation books, and is not available for value models. Bonus depreciation is always calculated and applied before other types of depreciation.

> [!NOTE]
> You can restore the bonus depreciation for a fixed asset only if you sell the fixed asset to an affiliated customer within five years of placing the fixed asset into operation. For more information, see [Set up an affiliated customer](#set-up-an-affiliated-customer).

You can select the following options to calculate bonus depreciation:

  - **Putting into operation** – The bonus depreciation is calculated from the first day of the month in which the fixed asset is put to use after it is acquired.

  - **Major repair** – The bonus depreciation amount is determined for a fixed asset when you calculate the depreciation amount for the following month. You can also calculate bonus depreciation by using the major repair amount that is posted to the accounting books on the same day.


## Set up bonus depreciation 

When major repair work is performed on a fixed asset, a bonus depreciation allowance is applied to the asset on or after the date of the major repair transaction. You can create a major repair transaction for a fixed asset, and specify the bonus depreciation and the start date for the bonus depreciation. The start date for the bonus depreciation can be the same as the date of the major repair transaction or the next depreciation date. Bonus depreciation records are used to calculate bonus depreciation amounts through the bonus depreciation proposal process.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation bonus**.

2.  Click **New** to create a new bonus depreciation allowance.

3.  In the **Depreciation bonus** field, enter a unique identification code to determine the bonus depreciation allowance.

4.  In the **Description** field, enter a description.

5.  In the **Depreciation bonus percent** field, enter the percentage of the depreciation bonus.


## Calculate a bonus depreciation 

The depreciation bonus is an additional depreciation amount that is assessed during the first year for some asset types that are operational. The depreciation bonus is calculated only for the tax value model for fixed assets. You must set up a posting profile before you can calculate the depreciation bonus for fixed assets.

1.  Click **Fixed assets (Russia)** \> **Periodic** \> **Depreciation bonus initialization**.

2.  In the **Value model** field, select a model for the depreciation bonus.

3.  In the **Depreciation bonus** field, select the bonus ID that you create in the **Depreciation bonus** form.

4.  Click **Select** to open the **Inquiry** form. Then enter the selection criteria for the fixed asset or fixed asset group to create the transaction for.

5.  Click **OK**. The depreciation bonus percentage is updated in the **Depreciation bonus** field in the **FA transactions** form.
    

    > [!NOTE]
    > <P>When you post a depreciation transaction, two transactions are created in the fixed asset (FA) journal to register the depreciation and the depreciation bonus.</P>

## Set up an affiliated customer 

Use the **Customers** page to affiliate a customer with an intercompany. If you sell a fixed asset to an affiliated customer within five years of placing the fixed asset into operation, then you can restore the bonus depreciation for the fixed asset.

1.  Click **Accounts receivable** \> **Common** \> **Customers** \> **All customers**.
    
    –or–
    
    Click **Sales and marketing** \> **Common** \> **Customers** \> **All customers**.

2.  On the **All customers** list page, on the **Action Pane**, click **Customer** to create a customer, or open an existing customer record.

3.  In the **Customers** form, on the **Invoice and delivery** FastTab, select the **Affiliated** check box to affiliate the customer with an intercompany.

## Additional resources

- [Depreciation setup (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-methods.md)
- [Depreciation calculation (Russia)](rus-depreciation-calculation.md)
