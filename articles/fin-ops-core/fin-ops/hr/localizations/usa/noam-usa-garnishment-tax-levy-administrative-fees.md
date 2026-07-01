---
title: Garnishments, tax levies, and administrative fees FAQ
description: Access frequently asked questions and answers about garnishments and tax levies, including questions about deducted amounts and sums.
author: twheeloc
ms.author: twheeloc
ms.topic: faq
ms.date: 06/25/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: USA
ms.search.validFrom: 2016-11-30
ms.search.form: HcmBenefit, HcmBenefitElementSetup, HcmWorkerEnrollment, PayrollDisposableIncome, PayrollWorkerGarnishmentRule
ms.dyn365.ops.version: Version 1611
ms.assetid: e87ff0bd-0594-45a6-bd54-5f8d085e1894
---

# Garnishments, tax levies, and administrative fees FAQ

[!include [banner](../../../../../finance/includes/banner.md)]

This article lists frequently asked questions and answers about garnishments and tax levies. It provides information to help you quickly and accurately set up garnishments and tax levies to keep your organization in compliance with applicable laws, regulations, and court orders. If you have a question that isn't answered here or in the related articles, confer with your legal advisors.

In this article, *garnishment* implies both garnishments and tax levies, unless otherwise specified.

## How do tax levies differ from other garnishments?

Two main differences exist between tax levies and other garnishments:

- The deductions for tax levies aren't included in the legal limit for all combined garnishments. Therefore, the amount of the deduction for a tax levy is never reduced because of the legal limit.
- For state and local tax levies, you must specify the state. You can set up one state tax levy type and one local tax levy type for each state. Each combination of type and state is treated as a separate garnishment type when tax levies are processed.

## Why is the amount that is deducted for a garnishment less than the amount that I entered?

Legal limits exist for the total amount that you can deduct from a worker's pay for garnishments and tax levies. In some cases, you can't deduct the full amount for a garnishment. If you're not sure that the amount that was deducted is correct, check with your legal advisors.

## For a worker who has multiple garnishments, why is the sum of all of the garnishment deductions more than the legal limit?

Several situations can create garnishment deductions that seem to exceed the legal limit. In most cases, the amount is correct. You can check this information to verify that the amount is correct:

- If one of the garnishments is a support order, the legal limit for support orders is higher than the legal limit for other kinds of garnishments.
- If one of the garnishments is a tax levy, the deduction for a tax levy doesn't count as part of the legal limit.
- If the disposable income that is calculated for combined garnishments is too high, the combined deductions for all garnishments are too high. Verify that the disposable income definition that you specify for combined garnishments on the **Garnishment and tax levy rules** page is set up correctly.

## When a worker has multiple garnishments and the total deductions exceed the legal limit, how do you decide which garnishments are deducted, and the amount of the deduction for each one?

How deductions are determined in this situation depends partly on legal limits and partly on the settings that you specified. This series of steps is used to determine the amounts for garnishment deductions:

1. The amount for every garnishment and tax deduction is calculated as if that garnishment or deduction is the only one.
2. Deduction limits are determined. The deduction limits can be affected by many things. These include the disposable income limit, an alternative limit, federal or state minimum wages, and earnings exemptions.
3. If the worker has multiple garnishments of the same type, the deduction amounts are adjusted so that they don't exceed the legal limit. The multiple garnishment method that is selected on the **Garnishment and tax levy rules** page determines how the adjustments are made. The amounts for tax levies aren't adjusted.
4. If the worker has multiple garnishments of different types, the deduction amounts are adjusted based on the information that is specified for combined garnishments on the **Garnishment and tax levy rules** page. The amounts for tax levies aren't adjusted.
5. If it's required, the amount of support orders is adjusted to account for the administrative fee.

After these steps are completed, the calculated amounts are submitted to the payroll process. They're deducted from the worker's pay in the deduction priority order that was specified on the **Maintain benefits** page. If the worker's pay reaches 0 (zero) before all deductions have been made, the deductions for any garnishments or tax levies that haven't yet been made are set to 0 (zero).

## Why are some garnishments not listed on workers' pay statements?

If you can't make a deduction for a garnishment, the garnishment isn't displayed on the worker's pay statement. You can't make a deduction for a garnishment in these situations:

- The deduction would cause the combined total of the garnishment deductions to exceed the legal limit. Deductions for a worker's garnishments are made one at a time, according to the deduction priority that is set on the **Payroll details** FastTab on the **Maintain benefits** page. When the legal limit for the combined total is reached, no additional garnishment deductions can be made. Because tax levies don't count toward the legal limit, this situation doesn't prevent a deduction for a tax levy.
- The deduction would cause the worker's pay to fall below zero. This can happen when the worker has other payroll deductions with a higher deduction priority than the garnishment. For example, after you deduct health insurance premiums, taxes, and union dues for a low-wage worker, it's possible that the worker's net pay is already 0 (zero). If that occurs, no amount is deducted for a garnishment of any type, including tax levies.
- The worker is enrolled in a garnishment, but the rules for the garnishment type haven't been added. When you enroll a worker in a garnishment, you must make sure that the garnishment type has been added to the **Garnishment and tax levy rules** page. State and local tax levies require a separate rule for each combination of garnishment type and state. For example, suppose a worker has three garnishments for student loans and two for state tax levies – one from Arkansas and one from Missouri. The **Garnishment and tax levy rules** page for that worker must have one rule for student loans, one rule for state tax levies from Arkansas, and one rule for state tax levies from Missouri.
- Settings on the garnishment enrollment or garnishment rule create a deduction of 0 (zero). Many settings on the **Maintain benefits** page and the **Garnishment and tax levy rules** page can create a calculated deduction amount of 0 (zero) if they're entered incorrectly. For example, if a position for which the worker has no earnings is selected on the **Payroll details** FastTab, or if the alternative limit on the **Garnishment and tax levy rules** page is left blank, no amount is deducted for the affected garnishment.

> [!NOTE]
> If your organization charges an administrative fee for garnishments or tax levies, you might have to adjust the amount of the administrative fee for any garnishments that aren't taken in a pay period.

## Why isn't the administrative fee for workers' garnishments being deducted from their pay?

To deduct administrative fees from a worker's pay, you have to create an administrative fee benefit and enroll the worker in that benefit. For more information, see [Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md).

For support orders, the **Administrative fee** field on the **Maintain benefits** page is used to ensure that the amount of the deduction plus the amount of the fee doesn't exceed the legal maximum for support orders. For all other garnishment types, this field has no effect and is for information only.

## Can a partial deduction be made for a garnishment?

Yes. For example, if 1,000.00 remains before a worker's pay reaches 0 (zero), and the requested amount for the next garnishment is 1,250.00, only 1,000.00 is deducted for that garnishment.

## Additional resources

[Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md)

[Enroll workers in garnishments or tax levies](noam-usa-garnishment-tax-levy-enrollment-tasks.md)

[!INCLUDE[footer-include](../../../../../includes/footer-banner.md)]
