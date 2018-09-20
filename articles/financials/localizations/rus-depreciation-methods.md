---
# required metadata

title: Depreciation methods (Russia)
description: This topic describes the fixed assets depreciation methods for Russia.
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

## Linear and non-linear depreciation methods

The linear depreciation method is the simplest and the most widely used method to calculate the depreciation for fixed assets. The capital allowance is recorded by equal portions for every time period or interval for the entire service life of the fixed asset.

For example, the cost of a computer is RUB 10,000, and its established service life, when functional and physical deterioration are considered, is five years. Each year, 10,000/5 is written off, which equals RUB 2,000 of depreciation. Therefore, you can calculate depreciation for a computer by using the linear method.

In the non-linear method, the accrued amount per month for the depreciation asset is defined as the product of the remaining value of the object and the depreciation rate. The depreciation rate is defined by the formula K = (2/n) \* 100%, where n = the useful life of the object in months, as in the reducing balance method.

In addition, when the residual value of the object reaches 20 percent of its original value, the residual value is used as the base value for additional depreciation calculations for the object. The monthly depreciation amount is defined by dividing the base cost of the object by the number of months that remain until the end of its service life.

## Manual depreciation method

This method is based on a manual definition of the depreciation percentage level. For this depreciation profile, you must define a depreciation schedule that states the required depreciation percentage level for each period. The number of periods specified in the depreciation schedule corresponds to that in the fixed asset record.

## Factor depreciation method

When you use the factor depreciation method, the fixed asset depreciation amount is calculated as a remaining amount, multiplied by a fixed ratio.
Select the period for depreciation accrual in the Interval field, in the Depreciation method form.
If you select the reducing balance or non-linear depreciation methods, specify the increasing factor. If you select the factor depreciation method, specify the amount of the multiplier.
For the non-linear method, enter the cutoff percentage value in the Factor field (for example, 20). When the accrued depreciation amount is calculated, the depreciation amount for the year will be recalculated based on the service life and depreciation profile for the asset. The depreciation is distributed equally across the intervals in the year.

## Product output-mileage depreciation method 

The product output-mileage depreciation method is used to write off the value of an asset in proportion to the volume of units produced.

### Create the product output or mileage of a fixed asset 
Use this procedure to create the product output or mileage of a fixed asset. 

1.  Click **Fixed assets (Russia)** \> **Periodic** \> **Product output/mileage**.
2.  Press the **New** button to create new product output or mileage for a fixed asset.
3.  In the **FA inventory number** field, select a fixed asset number.
4.  In the **Period** field, select a start date of the period for calculating the product output or mileage for the fixed asset.
    
    > [!NOTE]
    > The date that you specify in this field is used to calculate the depreciation for the specified fixed asset.

5.  In the **Output/mileage** field, enter the number of units that are produced or the distance that is traveled for the specified period.
    
    > [!NOTE]
    > The number of units (mileage) indicated cannot be less than the sum of the units (mileage) that is indicated in the **Output/run nontaxable** and **Output/run export** fields.

6.  In the **Output/run export** field, enter the product output or mileage to export for the fixed asset.
7.  In the **Output/run nontaxable** field, enter the product output or mileage for tax-exempt operations for the fixed asset.
8.  Click **Functions** \> **Copy output/run** to open the **Create or copy output/run lines** form and copy lines from previous reporting periods.
    
    –or–
    
    Click **Functions** \> **Copy output/run** to open the **Create or copy output/run lines** form and create lines in the defined reporting period with specified export and tax-exempt details for the fixed asset.
   
    > [!NOTE]
    > You may enter the output or mileage on the **Fixed assets** page (**Fixed assets (Russia)** \> **Common** \> **Fixed assets**, **FIXED ASSETS** button \> **FA usage** ). 

## Non-linear tax accounting group depreciation method

Linear and non-linear depreciation methods are used to calculate depreciation for tax accounting. The linear method that is used in tax accounting corresponds to the linear method that is used in standard accounting.

When the non-linear method is used, the accrued monthly depreciation for the asset is calculated as the product of the remaining value of the asset and the depreciation rate. The depreciation rate is defined by the formula K = (2/n) \* 100%, where n = the useful life of the asset in months.

### Set up the method of depreciation

You can create a tax non-linear group depreciation method on the **Depreciation methods** page. For more information, see [Depreciation setup (Russia)](rus-depreciation-setup.md).

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2.  In the **Value model** field, select the value model that the depreciation group is defined for.

    > [!NOTE]
    > You must specify the posting layer as **Tax** for the selected value model op the **Value models** page.

3.  Create a new depreciation group. For more information, see [Set up a depreciation group](rus-depreciation-setup.md##set-up-depreciation-groups).
4.  In the **Depreciation group** and **Name** fields, enter the depreciation group and name.
5.  In the **Depreciation method** field, select the **Tax nonlinear** method of depreciation.
6.  In the **Lifetime** field, enter the maximum asset service life, during which depreciation accrues for the fixed assets in the depreciation group. The value is expressed in months.

7.  In the **Year rate** field, enter the depreciation rate for the year.
   
    > [!NOTE]
    > This field is available only if you select <STRONG>Tax nonlinear group method</STRONG> as the method of depreciation.

8.  On the **Subgroups** FastTab, in the **Depreciation subgroup** field, enter the identification code of the depreciation subgroup.
    
    > [!NOTE]
    > This FastTab is available only if you select **Tax nonlinear group method** as the method of depreciation.</P>

9.  In the **Name** field, enter the name of the depreciation subgroup.
10. In the **Factor** field, enter the depreciation calculation ratio.


## Additional resources

- [Depreciation setup (Russia)](rus-depreciation-setup.md)
- [Depreciation methods (Russia)](rus-depreciation-calculation.md)
