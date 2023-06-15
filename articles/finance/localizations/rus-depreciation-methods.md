---
title: Depreciation methods (Russia)
description: This article describes the various fixed asset depreciation methods for Russia.
author: AdamTrukawka
ms.date: 09/20/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Russia
ms.author: atrukawk
ms.search.validFrom: 2018-10-28
ms.dyn365.ops.version: 8.1
ms.search.industry: 
---

# Depreciation methods (Russia)

[!include [banner](../includes/banner.md)]

This article describes the various methods that can be used for fixed asset depreciation for Russia and their implementation in the application.
The process of calculating monthly depreciation can be done in several ways. In tax accounting and accounting, there are a linear and non-linear depreciation calculation methods.

## Linear and non-linear depreciation methods


The linear depreciation method is the simplest and most widely used method for calculating depreciation for fixed assets. The capital allowance is recorded in equal parts for every period or interval during the whole service life of the fixed asset.

For example, the cost of a computer is 10,000 Russian rubles (RUB). When functional and physical deterioration are considered, the established service life of the computer is five years. Therefore, an amount that equals 10,000 ÷ 5 is written off every year. In other words, the depreciation is RUB 2,000. Therefore, you can calculate depreciation for a computer by using the linear method.

The difference of non-linear methods in the uneven distribution of depreciation value during the useful life. In some situations it is beneficial to organizations.

In accounting, there are 3 non-linear depreciation methods:
- **Decreasing balance** (**Reducing remainder**) - depreciation is calculated from the net book value, taking into account the acceleration factor, the method is accelerated depreciation, as it allows to transfer a large part of the value of the fixed assets object to expenses in the first years of useful fixed asset life.
Further, over time, the amount of depreciation decreases.
If the company additionally introduces an accelerating factor, the process of write-off using the dreducing remainer method is accelerated
- **In proportion to the volume of products, works** (**[Product output/mileage](rus-depreciation-methods.md#product-output-mileage-depreciation-method)**) - it is convenient to apply for equipment used in production, as well as fixed assets for which the standard volume of products, goods and services is pre-established by the manufacturer. With this method, depreciation is calculated on a monthly basis, based on the actual work performed. This method can also be used for Vehicles 
- **By the sum of the numbers of years of useful life** (**By numbers of years**). The method is rarely used due to its unusual nature. Depreciation is calculated based on the number of years of the remaining useful life and the initial cost of the fixed asset.

Depreciation in tax accounting is calculated one of two ways: 
- **linear** and, 
- **non-linear** (Article 259 of the Tax Code of the Russian Federation).
In the non-linear depreciation method, the accrued monthly depreciation for the asset is calculated by multiplying the asset's remaining value by the depreciation rate. The depreciation rate is defined by the formula K = (2 ÷ n) × 100 percent, where *n* is the asset's useful life in months (the same formula is used in the reducing remainder method).
In addition, when an asset's net book value (remaider) reaches 20 percent of its original value, the residual value (net book value) is used as the base value for additional depreciation calculations for the fixed asset. The monthly depreciation amount is calculated by dividing the fixed asset's net book value by the number of months that remain until the end of its service life.

> [!NOTE] 
> **Non-lilear method** may be used for a individual fixed asset or for a fixed asset group (**[Non-linear tax accounting depreciation methods](rus-depreciation-methods.md#non-linear-tax-accounting-group-depreciation-method)**) in the tax accounting.

For additional information about the depreciation methods implemented in application, see the following section.  

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

## Factor depreciation method

In the factor depreciation method, the depreciation amount for a fixed asset is calculated by multiplying the remaining amount by a fixed ratio.

You select the period for depreciation accrual in the **Interval** field on the **Depreciation method** page.

If you use the reducing balance method or the non-linear depreciation method, you must specify the increasing factor. If you use the factor depreciation method, you must specify the amount of the fixed ratio.

For the non-linear method, you enter the cut-off percentage value in the **Factor** field (for example, enter **20**). When the accrued depreciation amount is calculated, the depreciation amount for the year is recalculated based on the asset's service life and depreciation profile. The depreciation is distributed equally across all the intervals in the year.

## Manual depreciation method

The manual depreciation method is based on a manual definition of the depreciation percentage. For the depreciation profile, you must define a depreciation schedule that indicates the depreciation percentage that is required for each period. The number of periods in the depreciation schedule corresponds to the number of periods in the fixed asset record.


## Non-linear tax accounting group depreciation method

Depreciation is charged not for each object of fixed assets, but for the depreciation group (subgroup) as a whole. Subgroup - objects included in the group to which the increasing or decreasing depreciation factor is applied. The cost of all objects included in a group (subgroup) forms its total net book value, which is monthly reduced by the amount of calculated depreciation. Depreciation is calculated at the rate established by law for each group. In the case when the total net book value of a group (subgroup) becomes less than 20,000 rubles, in the month following the month when the specified value was reached, the organization has the right to liquidate this group (subgroup).


### Set up the depreciation method

You can create a tax non-linear group depreciation method on the **Depreciation methods** page. For more information, see [Set up depreciation (Russia)](rus-depreciation-setup.md).

1. Select **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2. In the **Value model** field, select the value model that the depreciation group is defined for.

    > [!NOTE]
    > You must specify **Tax** as the posting layer for the selected value model on the **Value models** page.

3. Create a depreciation group. For more information, see [Set up depreciation groups](rus-depreciation-setup.md#set-up-depreciation-groups).
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

- [Set up depreciation (Russia)](rus-depreciation-setup.md)
- [Calculate depreciation for Russia](rus-depreciation-calculation.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
