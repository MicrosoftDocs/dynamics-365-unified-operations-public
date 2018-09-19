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
    
      - **[Linear](rus-depreciation-methods.md#linear-and-non-linear-depreciation-methods)** − This method is a uniform accrual method. A capital allowance is calculated proportionately for each period or interval that you set up, such as monthly, quarterly, semi-annually, or annually, or for the whole service life of the asset.
    
      - **Reducing remainder** − This method decreases the depreciation value over the service life of the asset. The depreciation amount is based on the residual value of the fixed asset at the start of the reporting year. The depreciation rate is calculated based on the remaining useful life and the acceleration factor.
    
      - **[Manual](rus-depreciation-methods.md#manual-depreciation-method)** − The depreciation schedule is defined as a percentage value for each period. In this method, you can manually define the depreciation rate for each depreciation period.
    
      - **[Factor](rus-depreciation-methods.md#factor-depreciation-method)** − The depreciation amount is calculated as a remaining amount that is multiplied by a fixed ratio.
    
      - **By number of years** − The asset value is based on the number of years of useful life that remain.
    
      - **[Product output/mileage](rus-depreciation-methods.md#product-output-mileage-depreciation-method)** − The asset value is proportionate to the volume of units that are produced.
    
      - **Tax nonlinear** − The accrued monthly depreciation for the asset is defined as the product of its remaining value and the depreciation rate. The depreciation rate is defined as K= (2/n) \* 100%, where n is the useful life of the asset in months.
    
      - **[Tax nonlinear group method](rus-depreciation-methods.md#non-linear-tax-accounting-group-depreciation-method)** − The accrued monthly depreciation for the asset group is defined as the product of its remaining value and the depreciation rate. The depreciation rate is defined as K = (2/n) \* 100%, where n is the useful life of the asset group in months.

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

Use the **Product output/mileage** form to create product output or mileage for a fixed asset.

1.  Click **Fixed assets (Russia)** \> **Periodic** \> **Product output/mileage**.

2.  Press CTRL+N to create new product output or mileage for a fixed asset.

3.  In the **FA inventory number** field, select a fixed asset number.

4.  In the **Period** field, select a start date of the period for calculating the product output or mileage for the fixed asset.
    
    > [!NOTE]
    > <P>The date that you specify in this field is used to calculate the depreciation for the specified fixed asset.</P>

5.  In the **Output/mileage** field, enter the number of units that are produced or the distance that is traveled for the specified period.
    
    > [!NOTE]
    > The number of units (mileage) indicated cannot be less than the sum of the units (mileage) that is indicated in the <STRONG>Output/run nontaxable</STRONG> and <STRONG>Output/run export</STRONG> fields.


6.  In the **Output/run export** field, enter the product output or mileage to export for the fixed asset.

7.  In the **Output/run nontaxable** field, enter the product output or mileage for tax-exempt operations for the fixed asset.

8.  Click **Functions** \> **Copy output/run** to open the **Create or copy output/run lines** form and copy lines from previous reporting periods.
    
    –or–
    
    Click **Functions** \> **Copy output/run** to open the **Create or copy output/run lines** form and create lines in the defined reporting period with specified export and tax-exempt details for the fixed asset.

## Non-linear tax accounting group depreciation method

Linear and non-linear depreciation methods are used to calculate depreciation for tax accounting. The linear method that is used in tax accounting corresponds to the linear method that is used in standard accounting.

When the non-linear method is used, the accrued monthly depreciation for the asset is calculated as the product of the remaining value of the asset and the depreciation rate. The depreciation rate is defined by the formula K = (2/n) \* 100%, where n = the useful life of the asset in months.

### Calculate or reverse depreciation using the tax group non-linear depreciation method 

You can calculate depreciation in tax accounting by using the linear method or the non-linear method. You can also calculate tax depreciation by using the tax non-linear group depreciation method. This method allows you to specify a depreciation rate for each group, or a depreciation factor for each subgroup, to calculate the depreciation amount that is accrued for each depreciation group or subgroup.

You can group the depreciation register lines by depreciation group or subgroup by using the **FA depreciation (nonlinear method)**, **IA depreciation (nonlinear method)**, **FA - information about object**, and **IA - object information** tax registers.

Use the following procedures to set up a method of depreciation, and to calculate or reverse depreciation by using the tax group non-linear depreciation method.

#### Set up the method of depreciation

You can create a tax non-linear group depreciation method in the **Depreciation methods** form. For more information, see [(RUS) Set up depreciation methods](rus-set-up-depreciation-methods.md) and [Depreciation methods and conventions](depreciation-methods-and-conventions.md).

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2.  In the **Value model** field, select the value model that the depreciation group is defined for.

    > [!NOTE]
    > You must specify the posting layer as <STRONG>Tax</STRONG> for the selected value model in the <STRONG>Value models</STRONG> form.

3.  Create a new depreciation group. For more information, see [(RUS) Set up depreciation groups](rus-set-up-depreciation-groups.md).
4.  In the **Depreciation group** and **Name** fields, enter the depreciation group and name.
5.  In the **Depreciation method** field, select the **Tax nonlinear** method of depreciation.
6.  In the **Lifetime** field, enter the maximum asset service life, during which depreciation accrues for the fixed assets in the depreciation group. The value is expressed in months.

7.  In the **Year rate** field, enter the depreciation rate for the year.
   
    > [!NOTE]
    > This field is available only if you select <STRONG>Tax nonlinear group method</STRONG> as the method of depreciation.

8.  On the **Subgroups** FastTab, in the **Depreciation subgroup** field, enter the identification code of the depreciation subgroup.
    
    > [!NOTE]
    > <P>This FastTab is available only if you select <STRONG>Tax nonlinear group method</STRONG> as the method of depreciation.</P>

9.  In the **Name** field, enter the name of the depreciation subgroup.
10. In the **Factor** field, enter the depreciation calculation ratio.

#### Calculate fixed asset depreciation for fixed assets by using the tax non-linear group method

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select a journal name.
4.  In the **Description** field, modify the description of the journal.
5.  Click **Lines** to open the **Journal voucher** form.
6.  Click **Group operations** \> **Depreciation by group** to open the **Depreciation by group** form.
    
    > [!NOTE]
    > <P>If you select the <STRONG>Tax nonlinear group method</STRONG> as the depreciation method, you cannot calculate the depreciation for a tax value model by using the single or group depreciation function.</P>

7.  In the **Transaction date** field, select the date of the transaction.
8.  Click **Select** to open the **Inquiry** form, and then enter the selection criteria for the fixed assets.
9.  Click **OK**. Depreciation transactions are created in the journal.
10. Click **Validate** \> **Validate** to validate the journal.
11. Click **Post** \> **Post** to post the journal. Corresponding fixed asset and ledger transactions are created.

#### Reverse fixed asset depreciation

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  Create a new journal.
3.  In the **Name** field, select a journal name.
4.  In the **Description** field, modify the description of the journal.
5.  Click **Lines** to open the **Journal voucher** form.
6.  Click **Group operations** \> **Storno of depreciation** to open the **Storno of depreciation** form.
7.  In the **Date of storno** field, select a date for the depreciation reversal.
8.  In the **Accounting** field, select a fixed asset value model.
9.  Click **OK**. Depreciation reversal transactions are created in the journal.
10. Click **Validate** \> **Validate** to validate the journal.
11. Click **Post** \> **Post** to post the journal. The fixed asset depreciation transaction is reversed, and the ledger transaction is updated.

#### Calculating depreciation bonus

The depreciation bonus is an additional depreciation amount that is assessed during the first year for some operational asset types. You must set up a posting profile and create an acquisition journal before you calculate the fixed asset depreciation bonus.

Use the **Depreciation bonus** form to calculate the depreciation bonus for fixed assets by using the **Tax nonlinear group method** as the depreciation method. When you create the depreciation transactions, a depreciated bonus is calculated for every asset. The bonus amount is calculated first, and then the depreciation from the cost is calculated, excluding the bonus. The bonus amount is not included in the total balance of the depreciation group.

### Change the depreciation method in tax accounting 

1.  Click **Fixed assets (Russia)** \> **Periodic** \> **Changing depreciation method**.
2.  On the **General** tab, in the **Year** field, select the year when the new depreciation method will go into effect.
3.  In the **Old depreciation profile** field, select the depreciation method that was previously used for tax accounting.
4.  In the **New depreciation profile** field, select the new depreciation method to be used.
    
    > [!NOTE]
    > <P>You cannot specify the same depreciation method in both the <STRONG>Old depreciation profile</STRONG> and <STRONG>New depreciation profile</STRONG> fields.</P>

5.  Click **Select** to open the **Inquiry** form, and then enter the selection criteria for fixed assets.
6.  Click **OK**. The new depreciation method will be updated in the **Depreciation method** field on the **General** tab in the **FA value models** form.
    
    > [!NOTE]
    > Click **Fixed assets (Russia)> Common > Fixed assets**.Click **Fixed assets > Value models > FA lifetime history** to open the **FA history** page to view these changes.
    
## Set up analysis codes for fixed asset depreciation 


Analysis codes are used to calculate the depreciation accrual for a fixed asset. You can set up an annual depreciation rate that is applied to the fixed assets or to a depreciation group. 

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Analysis codes**.

2.  On the left pane, press CTRL+N to create a new line.

3.  In the **Analysis code** field, enter the analysis code.

4.  In the **Name** field, enter a description of the analysis code.

5.  In the **Depreciation group** field, select a depreciation group.

6.  In the **Depreciation type** field, select the depreciation type from the following options:
    
      - **On cost** − The analysis code is applied to all fixed assets excluding vehicular fixed assets.
    
      - **On 1000 km mileage** − The analysis code is applied to vehicular fixed assets.

7.  On the right pane, press CTRL+N to create a new line.

8.  In the **Start date** field, specify the date when the depreciation rate becomes active.

9.  In the **Depreciation rate** field, enter the annual depreciation rate as a percentage.

10. In the **Factor** field, enter the factor by which the specified depreciation rate is increased or decreased from the fixed value that is defined by the Russian Federation legislation for a fixed asset group.

## Set up depreciation groups 

Depreciation groups are defined for fixed asset value models to specify asset details such as the depreciation profile, service life, and deferral parameters that are generated when depreciating a fixed asset. 

If a fixed asset is registered after it is put into operation, depreciation is calculated from the first day of the month of registration. If a fixed asset is registered before it is put into operation, depreciation is calculated from the first day of the month after the fixed asset is put into operation. 

1.  Click **Fixed assets (Russia)** \> **Setup** \> **Depreciation groups**.
2.  In the **Value model** field, select the value model that the depreciation group is defined for.
3.  Create a line.
4.  In the **Depreciation group** and **Name** fields, enter the depreciation group code and name for the depreciation group.
5.  In the **Depreciation method** field, select a depreciation method for the depreciation group.
6.  On the **General** FastTab, in the **Lifetime** field, enter the maximum service life, in years, during which depreciation is accrued for the fixed assets in the depreciation group.
7.  In the **Minimal depreciation** field, enter the minimum depreciation amount when you use the **Reducing remainder** depreciation method.

8.  In the **Depreciation start date** field, select the type of starting date for depreciation from the following options:
    
      - **From month when put into operation** – Depreciation is calculated from the first day of the month when the fixed asset is put to use after acquisition.
    
      - **Next month start** – Depreciation is calculated from the month after the fixed asset is put to use after acquisition.
      - **Next quarter start** – Depreciation is calculated from the quarter after the fixed asset is put to use after acquisition.
      - **Next half year start** – Depreciation is calculated from the half-year after the fixed asset is put to use after acquisition.
      - **Next year start** – Depreciation is calculated from the year after the fixed asset is put to use after acquisition.

9.  Click the **Deferrals** FastTab.
10. In the left pane, click **Disposal** to set up parameters to create deferrals on the disposal of fixed assets that accrue a loss. Click **Partial dismantlement** to create deferrals on the partial write-off of fixed assets that accrue a loss.
    
    > [!NOTE]
    > When you create a transaction for the partial write-off or disposal of a fixed asset, if the transaction causes a loss, the transaction details are posted to a deferral account. This account contains the values of the calculated loss and the write-off time. The write-off time is calculated by using the fixed asset depreciation factor and the difference between the useful life of the depreciated asset and the actual period that the asset is used before disposal.

11. In the right pane, press CTRL+N to create a line.
12. In the **Model number** field, select the model number of the deferral.
13. In the **Deferrals group** field, select the deferrals group for deferred expenses.
14. In the **Expense code** field, select the expense code for deferrals.
  
## Calculate fixed asset depreciation

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  On the **Overview** tab, press CTRL+N to create a new journal.
3.  In the **Name** field, select a journal name.
4.  In the **Description** field, view or modify the description of the journal.
5.  Click **Lines** to open the **Journal voucher** form.
6.  On the **Overview** tab, press CTRL+N to open the **Add to journal** form to create a single depreciation transaction for one fixed asset.
    
    > [!NOTE]
    > Click <STRONG>Group operations</STRONG> &gt; <STRONG>Depreciation</STRONG> to create depreciation transactions for several fixed assets.

7.  In the **Transaction date** field, select the date of the next calculation period. If no depreciation was calculated for the previous periods, depreciation transactions are created in the journal for all months prior to the transaction date, excluding the month of the transaction.
8.  In the **Transaction type** field, select **Depreciation**.
9.  In the **FA number** field, select a fixed asset number.
10. In the **Value model** field, select a fixed asset value model. If you do not select a model, transactions for all value models are created in the journal.

11. In the **Reason code** field, select a reason code.
12. In the **Reason comment** field, view or modify the reason for the depreciation transaction.
13. Click **OK**. Depreciation transactions are created in the journal for all value models that you set up in the **Value models** form.
14. Click **Validate** \> **Validate** to validate the transaction details.
15. Click **Post** \> **Post** to post the journal. Fixed asset and ledger transactions are created.

## Reverse fixed asset depreciation

1.  Click **Fixed assets (Russia)** \> **Journals** \> **FA journal**.
2.  On the **Overview** tab, press CTRL+N to create a new journal.
3.  In the **Name** field, select a journal name.
4.  In the **Description** field, view or modify the description of the journal.
5.  Click **Lines** to open the **Journal voucher** form.
6.  Click **Group operations** \> **Storno of depreciation** to open the **Storno of depreciation** form.
7.  In the **Date of storno** field, select a date for the depreciation reversal.
8.  In the **Accounting** field, select a fixed asset value model.
9.  Click **OK**. Depreciation reversal transactions are created in the journal.
10. Click **Validate** \> **Validate** to validate the transaction details.
11. Click **Post** \> **Post** to post the journal. The fixed asset depreciation transaction is reversed and the ledger transaction is updated accordingly.
