---
# required metadata

title: Configure rates
description: Rates in Microsoft Dynamics 365 Human Resources define how much employers and employees contribute for a benefit.
author: andreabichsel
manager: AnnBe
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anbichse
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Configure rates

Rates in Microsoft Dynamics 365 Human Resources define how much employers and employees contribute for a benefit. The value can be an amount or flex credits, depending on your configuration.

Use rates to determine how much employees and employers pay for each benefit, based on several factors. Coverage rates are date-effective, so you can keep a historical record of rates. 

## Set up rates

1. In the **Benefits management** workspace, under **Setup**, select **Rates**.

2. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- |
   | **Rate** | A unique name that identifies the benefit rate. |
   | **Description** | A description of the benefit rate. |
   | **Effective** | The date the rate is effective. The current system date is the default value. 
   | **Expiration** | The end date of the rate. 12/31/2154 (which represents never) is the default value. |
   | **Use tiers** | The tier to use for the benefit rate calculation. Single tier for a one tier benefit rate or Double tier for a two tier benefit rate. An example of a double tier is a tier based on gender and age. |
   | **Payment frequency** | The payment frequency that determines how often the benefit premium rate is paid to the benefit provider. For example, if the payment frequency is monthly, then benefit rate represents the monthly payment amount. |
   | **Pay frequency rate rounding** | The method for rounding the rate: Standard or Truncated. |
   | **Non-smoker employee amount** | The amount the benefit provider charges for a nonsmoking employee. This is the amount the employer pays to the benefit provider and should be based on the payment frequency for the rate setup. |
   | **Non-smoker employer amount** | The amount the benefit provider charges for a nonsmoking employee. This is the amount the employer pays to the benefit provider and it should be based on the payment frequency for the rate setup. |
   | **Smoker employee amount** | The amount the benefit provider charges for an employee who smokes. This is the amount the employer pays to the benefit provider and should be based on the payment frequency for the rate setup. |
   | **Smoker employer amount** | The amount the benefit provider charges for an employee who smokes. This is the amount the employer pays to the benefit provider and should be based on the payment frequency for the rate setup. |
   | **Administrative amount** | The administrative amount charged by a third-party administrator. This is the amount that the employer pays to the third-party administrator and it should be based the payment frequency for the rate setup. |
   | **Flex credit rate** | The number of flex credits the benefit costs. This is only applicable to rates that are for benefit plans that are associated with flex credit programs. If you use tier rates, the flex credit rate is defined in Actions > Tier rates. |
   | **Change effective date** | The date when the benefit rate change takes effect. The system will automatically change the benefit rate and update all benefit plans associated with this rate, as long as you run Rate change update processing. Don't set this date unless you want the system to automatically update the employee benefit plans based on this rate. This is normally reserved to automatic future rate change processing. The change effective date must be within the benefit rate effective and expiration dates. |
   | **Rate change completed** | The **Rate change completed** check box will be automatically selected after the benefit rate changes have been completed by the Rate change update processing. |

4. To track and maintain changes to the benefit rate setup, select **Actions**, and then select **Maintain versions**.

5. Select **Save**. 

## Set up tier rates

You can use tier rates in your rate setup if the rate varies depending on various factors. For example, you could configure tier rates to say that if your age is up to 34.99, then the non-smoker amount is 2. If your age is up to 39.99, then the non-smoker amount is 3.

You can also use double tiers. If you select **Double tier** for the **Use tiers** value on the **Rate setup** form, you can define rates based on two dimensions. For example, you could configure a double tire system to say that if you are male and your age is up to 34.99, then the non-smoker amount is 2. If you are male and your age is up to 39.99, then the non-smoker amount is 3. If you are female and your age is up to 34.99, then the non-smoker amount is 1.8. If you are female and your age is up to 39.99, then the non-smoker amount is 2.8.

1. In the **Benefits management** workspace, under **Setup**, select **Rates**.

2. Select one or more rates from the list, select **Actions**, and then select **Tier rates**.

3. Select **New**.

3. Specify values for the following fields:

   | Field | Description |
   | --- | --- | 
   | **Description** | The Description field value will be applied from the description in the rate setup record. This helps you identify which rate setup the tier rates are linked to. |
   | **Tier code** | Select a tier code. Tier codes are defined in the Tier codes form. The system will automatically display the description of the tier code in the grid to the left. |
   | **Tier type** | Specifies what field should be used as a selection criterion for the tier rate calculation process. For example:</br></br><ul><li>If Age is used, the system will use the employee’s birthdate in the benefit rate calculation process.</li><li>If Salary is used, the system will use the employee’s annual benefit salary in the benefit rate calculation process.</li><li>If Job type is used, the system will use the employee’s current active position record to determine the job type by the job record linked to the position.</li></ul></br></br>The tier types are Age, Salary, Physical, Gender, Full time equivalent, Job type, Compensation region, and Level. | 
   | **Level** | The value to use with the tier type during benefit rate calculation process. For example:</br></br><ul><li>If the tier type is Age, this would be the age value.</li><li>If the tier type is Salary, this would be the salary amount.</li><li> If the tier type is Job type, this would be the job type.</li></ul></br></br>With a tier type of Age or Salary, the system uses an ascending approach during tier rate selection, meaning the value in the Level field represents the lower bound of the tier. With a tier type of Job type, the system uses an exact match approach during tier rate selection. |
   | **Calculation type** | Specifies how to use the amount in the calculation amount field and what math calculation to perform if necessary. If the calculation type is a flat amount, the system uses the amount fields as is. If the calculation type is per $ amount of salary or coverage, the system uses the calculation amount and calculation direction in its math calculation.</br></br>If the calculation type is per $ amount of salary, the system will use the following math equation:</br></br>Annual benefit salary divided by Calculation amount (rounded up or down) times the amounts for smoker or non-smoker for employee or employer.</br></br>If the calculation type is per $ amount of coverage, the system will use the following math equation:</br></br>Coverage amount divided by Calculation amount (rounded up or down) times the amounts for smoker or non-smoker for employee or employer.)</br></br>In both calculations, the Calculation direction is used to determine whether to round the Annual benefit salary or Coverage amount divided by Calculation amount up or down. |
   | **Calculation amount** | The amount to use during the benefit rate calculation process. This amount will be the divisor during the math calculation of the tier rate. |
   | **Calculation direction** | The direction (Increase or Decrease) that the calculated result amount should be rounded. The system supports three calculation directions: Blank (exact method), Increase, and Decrease.</br></br><ul><li>If blank, the system will use the exact calculation of the salary/coverage amount divided by the calculation amount. If this value has a fraction, then the system will use this in its calculation.</li><li>If Increase, the system will increase the math calculation of the salary/coverage amount divided by the calculation amount to the next integer, which means 12.25 would increase to 13.</li><li>If Decrease, the system will decrease the math calculation of the salary/coverage amount divided by the calculation amount to the current integer, which means 12.25 would decrease to 12.</li></ul> |
   | **Non-smoker employee amount** | The amount a benefit provider charges for a nonsmoking employee. This is the amount the employer pays to the benefit provider and it should be based on the payment frequency for the rate setup. |
   | **Non-smoker employer amount** | The amount a benefit provider charges for a nonsmoking employee. This is the amount the employer pays to the benefit provider and it should be based on the payment frequency for the rate setup. |
   | **Smoker employee amount** | The amount a benefit provider charges for a nonsmoking employee. This is the amount the employer pays to the benefit provider and it should be based on the payment frequency for the rate setup. |
   | **Smoker employer amount** | The amount a benefit provider charges for a nonsmoking employee. This is the amount the employer pays to the benefit provider and it should be based on the payment frequency for the rate setup. |
   | **Administrative amount** | The administrative amount charged by a third-party administrator. This is the amount that the employer pays to the third-party administrator and it should be based the payment frequency for the rate setup. |
   | **Flex credit non-smoker rate** | The number of flex credits the benefit costs, based on the calculation defined for the tier level for non-smokers. For example, if the calculation type is **Per $ amount of coverage**, the calculation amount is 10,000, and the flex credit non-smoker rate is 6, that means that if a nonsmoking employee chooses $10,000 of coverage, it will cost 6 flex credits. If they choose $20,000 of coverage, it will cost 12 flex credits, and so on. |
   | **Flex credit smoker rate** | The number of flex credits the benefit costs, based on the calculation defined for the tier level for smokers. |

5. Select **Save**. 
