---
# required metadata

title: Depreciation methods (Russia)
description: This topic describes the various fixed asset depreciation methods for Russia.
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
ms.custom: 27231
ms.search.region: Russia
ms.search.industry: 
ms.author: anasyash
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1

---

# Depreciation methods (Russia)

[!include [banner](../includes/banner.md)]

This topic describes the various methods that can be used for fixed asset depreciation for Russia.
The process of calculating monthly depreciation can be done in several ways. In tax accounting and accounting, a linear and non-linear calculation algorithm is distinguished.
The difference of non-linear methods in the uneven distribution of depreciation value during the useful life. In some situations it is beneficial to organizations.

## Linear and non-linear depreciation methods

The linear depreciation method is the simplest and most widely used method for calculating depreciation for fixed assets. The capital allowance is recorded in equal parts for every period or interval during the whole service life of the fixed asset.

For example, the cost of a computer is 10,000 Russian rubles (RUB). When functional and physical deterioration are considered, the established service life of the computer is five years. Therefore, an amount that equals 10,000 ÷ 5 is written off every year. In other words, the depreciation is RUB 2,000. Therefore, you can calculate depreciation for a computer by using the linear method.

In accounting, there are 3 non-linear depreciation methods:
- Reducing remainder - depreciation is calculated from the net book value, taking into account the acceleration factor, the method is accelerated depreciation, as it allows to transfer a large part of the value of the fixed assets object to expenses in the first years of useful fixed asset life.
Further, over time, the amount of depreciation decreases.
If the company additionally introduces an accelerating factor, the process of write-off using the dreducing remainer method is accelerated
- Product output/mileage;
- By numbers of years.
Depreciation in tax accounting is calculated one of two ways: 
- linear and, 
- non-linear (Article 259 of the Tax Code of the Russian Federation).
In the non-linear depreciation method, the accrued monthly depreciation for the asset is calculated by multiplying the asset's remaining value by the depreciation rate. The depreciation rate is defined by the formula K = (2 ÷ n) × 100 percent, where *n* is the asset's useful life in months. (The same formula is used in the reducing balance method.)

In addition, when an asset's residual value reaches 20 percent of its original value, the residual value is used as the base value for additional depreciation calculations for the asset. The monthly depreciation amount is calculated by dividing the asset's base cost by the number of months that remain until the end of its service life.

## Manual depreciation method

The manual depreciation method is based on a manual definition of the depreciation percentage. For the depreciation profile, you must define a depreciation schedule that indicates the depreciation percentage that is required for each period. The number of periods in the depreciation schedule corresponds to the number of periods in the fixed asset record.

## Factor depreciation method

In the factor depreciation method, the depreciation amount for a fixed asset is calculated by multiplying the remaining amount by a fixed ratio.

You select the period for depreciation accrual in the **Interval** field on the **Depreciation method** page.

If you use the reducing balance method or the non-linear depreciation method, you must specify the increasing factor. If you use the factor depreciation method, you must specify the amount of the fixed ratio.

For the non-linear method, you enter the cut-off percentage value in the **Factor** field (for example, enter **20**). When the accrued depreciation amount is calculated, the depreciation amount for the year is recalculated based on the asset's service life and depreciation profile. The depreciation is distributed equally across all the intervals in the year.

## Product output-mileage depreciation method 

The product output-mileage depreciation method is used to write off the value of an asset in proportion to the volume of units that is produced or the distance that is traveled.

### Create the product output or mileage of a fixed asset 
Use this procedure to create the product output or mileage of a fixed asset. 

1. Select **Fixed assets (Russia)** \> **Periodic** \> **Product output/mileage**.
2. Select **New** to create the product output or mileage for a fixed asset.
3. In the **FA inventory number** field, select a fixed asset number.
4. In the **Period** field, select the start date of the period that the product output or mileage for the fixed asset is calculated for.

    > [!NOTE]
    > The date that you specify is used to calculate the depreciation for the specified fixed asset.

5. In the **Output/mileage** field, enter the number of units that are produced or the distance that is traveled during the specified period.

    > [!NOTE]
    > The number of units or mileage that you specify can't be less than the sum of the units or mileage that is indicated in the **Output/run export** and **Output/run nontaxable** fields.

6. In the **Output/run export** field, enter the product output or mileage to export for the fixed asset.
7. In the **Output/run nontaxable** field, enter the product output or mileage for tax-exempt operations for the fixed asset.
8. Follow one of these steps:

    - To copy lines from previous reporting periods, select **Copy output/run**, and then, in the **Create or copy output/run lines** dialog box, specify the periods.
    - To create lines that have specific export and tax-exempt details for the fixed asset, select **Create output/run**, and then, in the **Create or copy output/run lines** dialog box, specify the details.

    > [!NOTE]
    > You can enter the output or mileage on the **Fixed assets** page (select **Fixed assets (Russia)** \> **Common** \> **Fixed assets**, and then, on the Action Pane, on the **Fixed asset** tab, select **FA usage**). 

## Non-linear tax accounting group depreciation method

The linear and non-linear depreciation methods are used to calculate depreciation for tax accounting. The linear method that is used in tax accounting corresponds to the linear method that is used in standard accounting.

When the non-linear method is used, the accrued monthly depreciation for the asset is calculated by multiplying the asset's remaining value by the depreciation rate. The depreciation rate is defined by the formula K = (2 ÷ n) × 100 percent, where *n* is the asset's useful life in months.

### Set up the depreciation method

You can create a tax non-linear group depreciation method on the **Depreciation methods** page. For more information, see [Depreciation setup (Russia)](rus-depreciation-setup.md).

1. Select **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2. In the **Value model** field, select the value model that the depreciation group is defined for.

    > [!NOTE]
    > You must specify **Tax** as the posting layer for the selected value model on the **Value models** page.

3. Create a depreciation group. For more information, see [Set up a depreciation group](rus-depreciation-setup.md##set-up-depreciation-groups).
4. In the **Depreciation group** and **Name** fields, enter the depreciation group and name.
5. In the **Depreciation method** field, select **Tax nonlinear**.
6. In the **Lifetime** field, enter the maximum service life during which depreciation is accrued for the fixed assets in the depreciation group. The value is expressed in months.
7. In the **Year rate** field, enter the depreciation rate for the year.

    > [!NOTE]
    > This field is available only if you select **Tax nonlinear group method** as the method of depreciation.

8. On the **Subgroups** FastTab, in the **Depreciation subgroup** field, enter the identification code of the depreciation subgroup.

    > [!NOTE]
    > The **Subgroup** FastTab is available only if you select **Tax nonlinear group method** as the method of depreciation.

9. In the **Name** field, enter the name of the depreciation subgroup.
10. In the **Factor** field, enter the ratio for calculating depreciation.


## Additional resources

- [Depreciation setup (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-calculation.md)
