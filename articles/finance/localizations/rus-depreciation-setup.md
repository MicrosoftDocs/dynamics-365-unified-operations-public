---
# required metadata

title: Set up depreciation (Russia)
description: This topic explains how to set up depreciation for Russian fixed assets.
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

# Set up depreciation (Russia)

[!include [banner](../includes/banner.md)]

This topic explains how to set up depreciation for Russian fixed assets.

## Set up depreciation methods

Depreciation methods define the rules for calculating depreciation.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Depreciation methods**.
2. Select **New** to create a depreciation method.
3. In the **Depreciation method** field, enter the identification code of the depreciation method for the fixed asset. In the **Name** field, enter the name of the depreciation method.
4. In the **Method** field, select the depreciation method:

    - **[Linear](rus-depreciation-methods.md#linear-and-non-linear-depreciation-methods)** − This method is a uniform accrual method. A capital allowance is calculated proportionately for each period or interval that you set up, such as monthly, quarterly, semi-annually, or annually, or for the whole service life of the asset.
    - **Reducing remainder** − This method decreases the depreciation value over the service life of the asset. The depreciation amount is based on the residual value of the fixed asset at the start of the reporting year. The depreciation rate is calculated based on the remaining useful life and the acceleration factor.
    - **[Manual](rus-depreciation-methods.md#manual-depreciation-method)** − The depreciation schedule is defined as a percentage value for each period. In this method, you can manually define the depreciation rate for each depreciation period.
    - **[Factor](rus-depreciation-methods.md#factor-depreciation-method)** − The depreciation amount is calculated as a remaining amount that is multiplied by a fixed ratio.
    - **By number of years** − The asset value is based on the number of years of useful life that remain.
    - **[Product output/mileage](rus-depreciation-methods.md#product-output-mileage-depreciation-method)** − The asset value is proportionate to the volume of units that are produced or the distance that is traveled.
    - **Tax nonlinear** − The accrued monthly depreciation for the asset is calculated by multiplying its remaining value by the depreciation rate. The depreciation rate is defined as K = (2 ÷ n) × 100 percent, where *n* is the asset's useful life in months.
    - **[Tax nonlinear group method](rus-depreciation-methods.md#non-linear-tax-accounting-group-depreciation-method)** − The accrued monthly depreciation for the asset group is calculated by multiplying its remaining value by the depreciation rate. The depreciation rate is defined as K = (2 ÷ n) × 100 percent, where *n* is the asset group's useful life in months.

5. In the **Interval** field, select the period that the depreciation must be accrued for. If you select **Quarterly**, you must enter three monthly transactions instead of a single transaction for the whole quarter.
6. If you selected **Reducing remainder** or **Factor** as the depreciation method, in the **Factor** field, enter the factor or percentage that must be reduced per interval.

    > [!NOTE]
    > The **Factor** field is available only if you select **Reducing remainder** or **Factor** as the depreciation method.

7. If you selected **Tax nonlinear** as the depreciation method, in the **Cost limit** field, enter the cut-off percentage value. When the accrued depreciation amount is calculated, the depreciation amount for the year is recalculated based on the asset's service life and depreciation profile. The amount is allocated across the specified periods in the year.
8. If you selected **Manual** as the depreciation method, on the Action Pane, select **Schedule of depreciation** to manually create depreciation schedules for fixed assets.

    > [!NOTE]
    > The **Schedule of depreciation** button is available only if you select **Manual** as the depreciation method.

### Change the depreciation method for tax accounting

1. Go to **Fixed assets (Russia)** \> **Periodic** \> **Changing depreciation method**.
2. In the **Changing depreciation method** dialog box, in the **Year** field, specify the year when the new depreciation method goes into effect.
3. In the **Old depreciation profile** field, select the depreciation method that was previously used for tax accounting.
4. In the **New depreciation profile** field, select the new depreciation method.
5. On the **Records to include** FastTab, select **Filter** to open the **Inquiry** dialog box, and then enter the criteria that are used to select fixed assets.
6. Select **OK**. The **Depreciation method** field on the **General** FastTab of the **FA value models** page is updated with the new depreciation method.

    > [!TIP]
    > To open the **FA history** page to view these changes, go to **Fixed assets (Russia)** \> **Common** \> **Fixed assets**, select the fixed asset, and then select **Value models**. Then, on the **FA value models** page, select **FA lifetime history**.

## Set up analysis codes for fixed asset depreciation

Analysis codes are used to calculate the depreciation accrual for a fixed asset. You can set up an annual depreciation rate that is applied to fixed assets or to a depreciation group.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Analysis codes**.
2. Select **New** to create an analysis code.
3. In the **Analysis code** field, enter the analysis code. In the **Name** field, enter a description of the analysis code.
4. In the **Depreciation group** field, select a depreciation group.
5. In the **Depreciation type** field, select the depreciation type:

    - **From cost** − The analysis code is applied to all fixed assets except vehicular fixed assets.
    - **On 1000 km mileage** − The analysis code is applied to vehicular fixed assets.

6. On the **Lines** FastTab, select **Add** to create a line.
7. In the **Start date** field, specify the date when the depreciation rate becomes active.
8. In the **Depreciation rate** field, enter the annual depreciation rate as a percentage.
9. In the **Factor** field, enter the factor that the specified depreciation rate is increased or decreased by, relative to the fixed value that is defined by the Russian Federation legislation for a fixed asset group.

## Set up depreciation groups

By defining depreciation groups for fixed asset value models, you can specify asset details that are generated when a fixed asset is depreciated. These details include the depreciation profile, service life, and deferral parameters.

If a fixed asset is registered after it's put into operation, depreciation is calculated from the first day of the month of registration. If a fixed asset is registered before it's put into operation, depreciation is calculated from the first day of the month after the fixed asset is put into operation.

1. Go to **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2. In the **Value model** field, select the value model that you're creating a depreciation group for.
3. Select **New** to create a depreciation group.
4. In the **Depreciation group** field, enter the depreciation group code. In the **Name** field, enter the name of the depreciation group.
5. In the **Depreciation method** field, select a depreciation method for the depreciation group.
6. On the **General** FastTab, in the **Lifetime** field, enter the maximum service life, in years, that depreciation is accrued for the fixed assets in the depreciation group.
7. If you selected **Reducing remainder** as the depreciation method, in the **Minimal depreciation** field, enter the minimum depreciation amount.
8. In the **Depreciation start date** field, select the type of start date for depreciation:

    - **From month when put into operation** – Depreciation is calculated from the first day of the month when the fixed asset is put into operation after acquisition.
    - **Next month start** – Depreciation is calculated from the month after the fixed asset is put into operation after acquisition.
    - **Next quarter start** – Depreciation is calculated from the quarter after the fixed asset is put into operation after acquisition.
    - **Next half year start** – Depreciation is calculated from the half-year after the fixed asset is put into operation after acquisition.
    - **Next year start** – Depreciation is calculated from the year after the fixed asset is put into operation after acquisition.
    - **Date of the registration** – Depreciation is calculated from the date of registration.

9. In the **Depreciation bonus** field, enter the maximum depreciation bonus percentage. The **Depreciation bonus** percentage that is selected in the **Putting into operation** transaction can't exceed this value.
10. On the **Deferrals** FastTab, in the field above the grid, select **Disposal** to set up the parameters that are used to create deferrals on the disposal of fixed assets that accrue a loss. Select **Partial dismantlement** to set up the parameters that are used create deferrals on the partial write-off of fixed assets that accrue a loss.

    > [!NOTE]
    > When you create a transaction for the disposal or partial write-off of a fixed asset, if the transaction causes a loss, the transaction details are posted to a deferral account. This account contains the values of the calculated loss and the write-off time. The write-off time is calculated by using the fixed asset depreciation factor and the difference between the useful life of the depreciated asset and the actual amount of time that the asset was used before disposal.

11. Select **Add** to create a line.
12. In the **Model number** field, select the model number of the deferral.
13. In the **Deferrals group** field, select the deferrals group for deferred expenses.
14. In the **Expense code** field, select the expense code for deferrals.

## Additional resources

- [Depreciation methods (Russia)](rus-depreciation-methods.md)
- [Calculate depreciation for Russia](rus-depreciation-calculation.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]