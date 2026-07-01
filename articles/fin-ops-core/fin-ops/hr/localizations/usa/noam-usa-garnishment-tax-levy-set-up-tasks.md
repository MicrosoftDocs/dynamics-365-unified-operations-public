---
title: Set up garnishments and tax levies
description: Learn about how to set up garnishments and tax levies, including an overview on setting up disposable income definitions.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 06/25/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: USA
ms.search.validFrom: 2016-11-30
ms.search.form: HcmBenefit, HcmBenefitElementSetup, PayrollDisposableIncome
ms.dyn365.ops.version: Version 1611
ms.assetid: 6b3c8e46-96b2-4503-9f85-8408f9f97620
---

# Set up garnishments and tax levies

[!include [banner](../../../../../finance/includes/banner.md)]

This article explains how to set up garnishments and tax levies. Use the benefit framework to create and manage garnishments and tax levies. This framework helps ensure that the effect that garnishments and tax levies have on payroll is handled correctly.

If you have questions about garnishments that aren't answered in this article, or in [Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md) or [Garnishments, tax levies, and administrative fees FAQ](noam-usa-garnishment-tax-levy-administrative-fees.md), contact your legal advisor. Here's a summary of each step in the process:

1. **Set up disposable income definitions.** When the court imposes an order to garnish a worker's wages, the actual amount of the garnishment is limited to a percentage of the worker's disposable income. The federal definition of disposable income is built into the payroll calculation. However, some states require additional reductions to disposable income. Use disposable income definitions to identify those reductions and help ensure that the correct earnings and deductions are included when the worker's disposable income is calculated.
1. **Set up benefit elements for garnishments, tax levies, and administrative fees.** Because garnishments and tax levies are processed as benefits, each garnishment or tax levy consists of a benefit type, plan, and option. Together, these elements create a single instance of a garnishment or tax levy. Administrative fees aren't permitted in every state. Even in states where administrative fees are permitted, they're never mandatory. Your organization must decide whether to charge them.
1. **Create benefits for garnishments, tax levies, and administrative fees.** You must have at least one benefit for garnishments and at least one benefit for tax levies. If a worker has more than one garnishment of the same type, you must have more than one garnishment benefit of that type. If your organization charges an administrative fee for handling garnishments and tax levies, you must have at least one benefit for the fee. You can also optionally have additional benefits for other administrative fees.

> [!NOTE]
> In this article, the term *garnishment* implies both garnishments and tax levies, unless the text specifies otherwise. For more information about the concepts that are discussed in this article, see [Garnishments, tax levies, and administrative fees FAQ](noam-usa-garnishment-tax-levy-administrative-fees.md).

## Setting up disposable income definitions

When a court orders wage garnishment, the garnishment amount is limited to a percentage of the worker's disposable income. Under the federal definition, disposable income is the worker's gross earnings or income minus all legally required deductions. Gross earnings include wages, commissions, bonuses, paid time off (PTO) pay, and periodic pension statements. Here are some of the deductions that are required by law:

- Federal, state, and local income tax
- Social Security and Medicare tax
- State unemployment or disability tax
- State-mandated payments for state employee retirement systems

Under the federal formula, voluntary deductions (for example, deductions for life insurance, union dues, and retirement plan contributions) aren't subtracted from earnings. The federal formula is built into the Payroll system.

Many states use the federal definition of disposable income. However, some states have their own definition that exempts some additional earnings from total wages and subtracts other deductions, to further reduce what is considered disposable income. You don't have to create a definition by using the federal formula. (The federal formula is built into the Payroll calculations.) However, you must create additional disposable income definitions to comply with each state's formula.

> [!IMPORTANT]
> State definitions can change every year. Because it can be difficult to match your organization's earning codes and benefits to the definitions that a specific state uses, have your legal advisors determine the earning codes and benefits that each disposable income definition must include. Have your legal advisors review the definitions every year.

When you create a disposable income definition, you specify the earnings and the benefits to reduce the worker's disposable income by. You don't have to specify the taxes. The system automatically subtracts all mandatory taxes from the total wages.

Tax levies and other garnishments aren't automatically excluded from the worker's disposable income. To exclude them, you must specify them in the benefit section of the disposable income definition.

> [!IMPORTANT]
> Disposable income definitions don't have date-effective versions. When you change a definition, the change takes effect immediately. Therefore, don't change any existing disposable income definitions that you're using.

Create a new disposable income definition on the **Disposable income definition** page. Enter a name and description for the new disposable income definition. Because you typically define disposable income definitions for each state, consider using the two-letter state abbreviation as the first two letters of the name of every disposable income definition. For example, when you create a disposable income definition for garnishments from Texas, enter a name that starts with **TX**. Then, when you receive a new garnishment order, you can quickly see whether you already have the required disposable income definition, or whether you must create it.

When the system calculates total wages, it excludes earning lines that the earning code designates. Select **Add** in the **Reduce total wages by the following earnings** grid, and select an earning code that represents the earnings that the state identified as exempt from disposable income.

> [!IMPORTANT]
> It can be difficult to match your organization's earning codes to the definitions that a specific state uses. Therefore, we recommend that your legal advisors determine the earning codes that should be included in each disposable income definition.

When total wages are calculated, deductions for selected benefits are excluded. Select the **Add** button above the **Reduce disposable income by deductions for the following benefits** grid, and select benefits that the state has identified as exempt from disposable income. Remember that the system handles garnishments and tax levies as benefits. Therefore, to exclude the amount of garnishments or tax levies from a disposable income definition, you must add the garnishment or tax levy benefits here.

> [!IMPORTANT]
> We recommend that you work with your legal advisors to determine the benefits that should be included in each disposable income definition.

If you delete an earning code or benefit, it's automatically removed from all disposable income definitions. New earning codes and benefits that you create aren't automatically added. When you maintain earning codes and benefits, consider the effect that any changes have on the disposable income definitions.

## Set up benefit elements

Garnishments and tax levies are handled as benefits. A benefit is a unique combination of a benefit type, plan, and option. Use this set of tasks to create the following benefit elements that are required to create garnishment and tax levy benefits:

- **Benefit types** – You must create two benefit types: one for garnishments and one for tax levies. If your organization charges administrative fees for garnishments and tax levies, you must also create a benefit type for the administrative fees.
- **Benefit plans** – Most organizations create a benefit plan for each type of garnishment and tax levy. You can create extra benefit plans. For example, you might create a separate benefit plan for tax levies from each state.
- **Benefit options** – When you create benefit options, create a set of numbered options for garnishments and tax levies. For example, you might create options 01, 02, and 03. By numbering the options in this manner, you can quickly see the order that the garnishments were entered in.

When you set up the benefit elements for garnishments and tax levies, remember that multiple garnishments can be in effect for a worker at the same time, but the worker can have only one enrollment in each benefit at any time. Therefore, you must create multiple garnishment benefits. To create multiple garnishment benefits, set up multiple benefit plans or multiple benefit options. The easier method is to set up multiple benefit options, as described in the following set of tasks.

### Set up benefit types for garnishments, tax levies, and administrative fees

Set up benefit types for garnishments, tax levies, and administrative fees on the **Benefit elements** page. In the **Type** section of the **Benefit elements** page, enter the following information.

| Field | Description |
|-------|-------------|
| Name Description | Enter a name and a description for the type of garnishment benefit. For example, you might enter **Garnishment** as the name and **Court-ordered garnishment** as the description. |
| Concurrent enrollment | Select **Multiple enrollments per type**. This value is required, so that you can enroll a worker in more than one garnishment benefit or more than one tax levy at the same time. |
| Payroll category | Select one of the following payroll categories for the benefit type:<ul><li>For garnishments, select **Garnishment**.</li><li>For tax levies, select **Tax levy**.</li><li>Optional: For administrative fees, select **Standard**.</li></ul>The payroll category helps guarantee that the benefit follows the processing requirements that the government defines for garnishments or tax levies. The payroll category also determines which settings are available in the **Plans** area of this page. Settings that don't apply to the selected payroll category aren't available. |

After you create the benefit type for garnishments, repeat this setup to create a benefit type for tax levies and a benefit type for administrative fees, if your organization uses administrative fees.

### Set up benefit plans

Set up benefit plans on the **Benefit elements** page. At the side of the page, select **Plans** to show the **Define benefit plans** area. You must create at least one benefit plan for garnishments and one benefit plan for tax levies. However, create one benefit plan for each garnishment type and one benefit plan for each tax levy type. If you use this approach, create the following benefit plans:

- Support order
- Bankruptcy
- Federal administrative
- Student loan
- Creditor
- Federal tax levy
- State tax levy
- Local tax levy
- Optional: Administrative fees

Enter the following information.

| Field            | Description |
|------------------|-------------|
| Name Description | Enter a name and a description for the benefit plan. For example, for the bankruptcy plan, enter **Bankruptcy** as the name and **Bankruptcy order** as the description. For an administrative fee plan, enter **Admin fee** as the name and **Garnishments** as the description. |
| Benefit type     | Select the appropriate benefit type. This benefit type is one of the benefit types that you created in the previous section, "Setting up benefit types for garnishments, tax levies, and administrative fees." |
| Payroll impact   | Select **Deduction only**. |

On the **Tax rule** FastTab, enter the following information.

| Field        | Description      |
|--------------|------------------|
| Pretax basis | Select **None**. |

On the **Payroll details** FastTab, enter the following information.

| Field | Description |
|-------|-------------|
| Lock pay statement | Select this option to prevent changes to pay statement lines that include the garnishment or tax levy. When you select this option, you can add lines that include the garnishment or tax levy to the pay statement, or delete them from the pay statement. However, you can't change the garnishment or tax levy lines that are on the pay statement. If you don't select this option, you can change garnishment and tax levy lines directly on the pay statement. |
| Deduction method | By default, this field is set to **Partial**. When the **Partial** deduction method is used, part of the garnishment amount is automatically deducted from a worker's pay if the whole amount can't be deducted legally. |
| Payroll types | Make sure that at least one of the following payment types is selected:<ul><li>Primary</li><li>Additional</li><li>Gross up</li></ul><p>Deductions for the garnishment or tax levy are included in payroll runs of the selected type.</p>**IMPORTANT:** Many states have laws that specify how garnishments for child support are handled when a worker receives a lump-sum payment, such as a bonus, severance pay, or a vacation payout. The laws vary, but they typically include a provision that the state must be notified before a lump-sum payment is made. The state then gives the employer specific instructions about whether to calculate the garnishment and how to calculate it. In some cases, the whole lump-sum payment is subject to garnishment. |
| Deduction priority | This field determines the order that the garnishment or tax levy is deducted from pay in, relative to other deductions. The default value is **100**. Don't change the default value on this page. Instead, to adjust the value, use the **Maintain benefits** page for each worker when the worker is enrolled in the garnishment or tax levy. |
| Limit period Limit amount | The limit period and limit amount differ for each worker, and for each garnishment or tax levy. Set these values for each worker when the worker is enrolled. Therefore, on this page, leave the **Limit period** field blank, and set the **Limit amount** field to **0.00**. |

On the **Accounting** FastTab, set up accounting information for each legal entity that has workers who are enrolled in the garnishment or tax levy.

| Field        | Description                                                                                 |
|--------------|---------------------------------------------------------------------------------------------|
| Category     | Leave this field blank.                                                                     |
| Vendor       | Leave this field blank.                                                                     |
| Main account | Select the general ledger account to apply the payroll deductions to for this benefit plan. |

On the **Accounting** FastTab, you can also optionally enter the default financial dimension values for the benefit plan. If there's more than one legal entity in your organization, repeat the setup on the **Accounting** FastTab for each legal entity.

### Setting up benefit options

Set up benefit options on the **Benefit elements** page. Select **Options** to show the **Define benefit options** area. To create a new benefit option, select **New**, and enter the following information.

| Field                                                   | Description |
|---------------------------------------------------------|-------------|
| Option Description                                      | Enter a name and a description for the option. For example, you might enter **01** as the name and **Garnishment/tax levy** as the description. When you create benefit options for garnishments, create a set of numbered options for garnishments and tax levies. For example, you might create options 01, 02, and 03. By numbering the options in this manner, you can quickly see the order that the garnishments were entered in. You can optionally create a separate numbered sequence for each type of garnishment or tax levy. |
| Allow dependent coverage Allow beneficiary designations | Dependent coverage and beneficiary designations don't apply to garnishments or tax levies. Therefore, don't select the **Allow dependent coverage** and **allow beneficiary designations** check boxes. |

## Creating benefits for garnishments and tax levies

After you set up the benefit types, plans, and options, you must create the benefits for garnishments and tax levies. If your organization charges administrative fees for garnishments and tax levies, you must also create a benefit for the administrative fees. When you create a benefit, you link a benefit plan and an option, designate a benefit period, and assign eligibility rules to the benefit. You create benefits for garnishments and tax levies on the **Benefits** page. To create a new benefit, select **New**, and enter the following information.

| Field                | Description                                         |
|----------------------|-----------------------------------------------------|
| Create a new benefit | Select a plan and an option.                        |
| Effective Expiration | Specify dates that are appropriate for the benefit. |

After you enter this information, select **Create benefit**.

Next, on the **Eligibility rules** FastTab, change the eligibility from **All workers are eligible** to **Bypass eligibility process**. The benefit eligibility process is used to determine which workers can enroll in a benefit, and when they can enroll. Because anyone can be enrolled in a garnishment at any time, there's no reason to use the benefit eligibility process.

> [!NOTE]
> When eligibility is set to **Bypass eligibility process**, eligibility overrides have no effect. Therefore, you can skip the fields on the **Eligibility overrides** FastTab.

Next, on the **Payroll details** FastTab, enter the following payroll information. The values that you enter here are used as default values when you enroll a worker in the garnishment or tax levy.

| Field                                     | Description |
|-------------------------------------------|-------------|
| Frequency                                 | Select how often payroll calculations should occur. The frequency determines the pay periods that the selected benefit is calculated in. Most often, garnishments and tax levies use **All**. |
| Basis                                     | Leave this field set to the default value, **Fixed amount**. When the **Fixed amount** basis is used, the payroll process starts with a fixed deduction amount, regardless of the amount of earnings. You can change the value to **Percent of earnings**, as required, when you enroll a worker in the garnishment or tax levy. |
| Amount or rate (Garnishment and tax levy) | For garnishment and tax levy benefits, leave this field set to **0.0000**. The correct amount or rate is set on the **Maintain benefits** page for a specific worker when the worker is enrolled in the garnishment or tax levy. |
| Amount or rate (Administrative fees)      | For administrative fee benefits, enter the amount of the fee that your organization charges. If you charge different administrative fees under different circumstances, create separate administrative fee benefits for each fee amount. |

Finally, on the **Earning basis** FastTab, enter the earning codes that can be included when the basis is **Percent of earnings**. To enter an earning code, select **Add**, and then select the earning code in the list. Typically, your legal department determines the appropriate earning codes. Don't enter earning codes if the basis is **Fixed amount**, or if the benefit is for administrative fees.

> [!IMPORTANT]
> You can't change the list of earning codes on the **Maintain benefits** page for a specific worker. However, you can change the basis. If you change the basis to **Percent of earnings**, but don't enter any earning codes, the calculated amount of the deduction for the garnishment or tax levy is 0 (zero).

## Next step

The next step is to enroll workers in garnishments and tax levies. For more information, see [Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md).

## Additional resources

[Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md)

[Set up benefits](noam-usa-benefit-set-up-tasks.md)

[Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md)

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
