---
# required metadata

title: Fixed assets depreciation for Russia
description: 
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

# Fixed assets depreciation for Russia

[!include [banner](../includes/banner.md)]


## Set up depreciation methods

Depreciation methods are used to define the rules for calculating depreciation. Use this procedure to set up depreciation methods.

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation methods**.

2.  Press CTRL+N to create a new depreciation method.

3.  In the **Depreciation method** field, enter the identification code of the depreciation method for the fixed asset.

4.  In the **Name** field, enter the name of the depreciation method.

5.  In the **Method** field, select the depreciation method from the following options:
    
      - **Linear** − This method is a uniform accrual method. A capital allowance is calculated proportionately for each period or interval that you set up, such as monthly, quarterly, semi-annually, or annually, or for the whole service life of the asset.
    
      - **Reducing remainder** − This method decreases the depreciation value over the service life of the asset. The depreciation amount is based on the residual value of the fixed asset at the start of the reporting year. The depreciation rate is calculated based on the remaining useful life and the acceleration factor.
    
      - **Manual** − The depreciation schedule is defined as a percentage value for each period. In this method, you can manually define the depreciation rate for each depreciation period.
    
      - **Factor** − The depreciation amount is calculated as a remaining amount that is multiplied by a fixed ratio.
    
      - **By number of years** − The asset value is based on the number of years of useful life that remain.
    
      - **Product output/mileage** − The asset value is proportionate to the volume of units that are produced.
    
      - **Tax nonlinear** − The accrued monthly depreciation for the asset is defined as the product of its remaining value and the depreciation rate. The depreciation rate is defined as K= (2/n) \* 100%, where n is the useful life of the asset in months.
    
      - **Tax nonlinear group method** − The accrued monthly depreciation for the asset group is defined as the product of its remaining value and the depreciation rate. The depreciation rate is defined as K = (2/n) \* 100%, where n is the useful life of the asset group in months.

6.  In the **Interval** field, select the period for which the depreciation must be accrued. If you select **Quarterly** in the **Interval** field, you must enter three monthly transactions instead of a single transaction for the whole quarter.

7.  In the **Factor** field, enter the factor or percentage that must be reduced by interval.
    

    > [!NOTE]
    > <P>This field is available only if you select <STRONG>Reducing remainder</STRONG> or <STRONG>Factor</STRONG> as the depreciating method.</P>



8.  In the **Cost limit** field for the **Tax nonlinear** method, enter the cutoff percentage value. When the accrued depreciation amount is calculated, the depreciation amount for the year is recalculated based on the service life and the depreciation profile for the asset. The amount is allocated across the specified periods in the year.

9.  Click **Schedule of depreciation** to manually create depreciation schedules for fixed assets.
    

    > [!NOTE]
    > <P>The <STRONG>Schedule of depreciation</STRONG> button is available only if you select <STRONG>Manual</STRONG> as the depreciation method.</P>

## Linear and non-linear depreciation methods

The linear depreciation method is the simplest and the most widely used method to calculate the depreciation for fixed assets. The capital allowance is recorded by equal portions for every time period or interval for the entire service life of the fixed asset.

For example, the cost of a computer is RUB 10,000, and its established service life, when functional and physical deterioration are considered, is five years. Each year, 10,000/5 is written off, which equals RUB 2,000 of depreciation. Therefore, you can calculate depreciation for a computer by using the linear method.

In the non-linear method, the accrued amount per month for the depreciation asset is defined as the product of the remaining value of the object and the depreciation rate. The depreciation rate is defined by the formula K = (2/n) \* 100%, where n = the useful life of the object in months, as in the reducing balance method.

In addition, when the residual value of the object reaches 20 percent of its original value, the residual value is used as the base value for additional depreciation calculations for the object. The monthly depreciation amount is defined by dividing the base cost of the object by the number of months that remain until the end of its service life.


