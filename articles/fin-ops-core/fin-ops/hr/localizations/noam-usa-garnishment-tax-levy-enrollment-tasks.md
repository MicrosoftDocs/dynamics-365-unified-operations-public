---
# required metadata

title: Enroll workers in garnishments or tax levies
description: This article describes the process for enrolling workers in garnishments, tax levies, and any associated administrative fees.
author: twheeloc
ms.date: 04/01/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmBenefit, HcmBenefitElementSetup, HcmWorkerEnrollment, PayrollDisposableIncome, PayrollWorkerGarnishmentRule
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 221194
ms.assetid: f734d55a-304c-4e49-b437-6fa34c30b5ca
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Enroll workers in garnishments or tax levies

[!include [banner](../../includes/banner.md)]

This article describes the process for enrolling workers in garnishments, tax levies, and any associated administrative fees. Garnishments and tax levies are managed by using the benefit framework. This framework helps ensure that the payroll impact of garnishments and tax levies is handled correctly.

If you have questions about garnishments and tax levies that aren't answered in this article, or in the [Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md) or [Garnishments, tax levies, and administrative fees FAQ](noam-usa-garnishment-tax-levy-administrative-fees.md) topics, contact your legal advisors. To learn more about the concepts that are discussed in this article, see [Garnishments, tax levies, and administrative fees FAQ](noam-usa-garnishment-tax-levy-administrative-fees.md).

## Enroll a worker in a garnishment or tax levy

When the Payroll department is notified about a court-ordered garnishment or tax levy, the federal government requires that deductions begin within a specific number of days. As for other garnishment rules, some states might use federal rules, or they might set their own requirements. For example, a state might require that deductions begin in the first payroll payment, no later than three days after the court order is received. Because this payment might occur in the current pay period, it's in your interest to enroll workers as quickly as possible.

When you enroll a worker, you set up payroll information, together with details of the garnishment or tax levy.

During the enrollment process, you will be prompted for various information.

Start on the **Payroll details** FastTab. The following table shows the information that you must enter.

| Field                | Description |
|----------------------|-------------|
| Benefit              | Enter **Eligibility passed**. |
| Paid by              | Specify the legal entity that the worker is employed by, and that pays for the worker position. By default, the current legal entity is shown. |
| Position             | If you select a position, the deduction for the garnishment is based only on the earnings from that position. It's unlikely that a garnishment will be based on earnings from a specific position. If you don't select a position, the deductions for the garnishment are based on all the worker's earnings. |
| Vendor               | Specify the vendor that the garnishment is paid to. Typically, this vendor is a state agency and is listed on the garnishment order. If you don't already have a vendor record for the agency, you must create it. For more information, see [Create a vendor account](../../../../supply-chain/procurement/tasks/create-vendor-account.md). |
| Calculation priority | The number that you enter determines the order that deductions for the garnishment are calculated in, relative to other benefits. The deductions and contributions for the benefit that has the lowest calculation priority number are calculated first. The lowest calculation priority number is 0 (zero). The calculation priority is important when the result of the calculation for one benefit is used in the calculation for another benefit. For example, in some states, the deductions for union dues and health plans reduce disposable income. To make sure that the garnishment is calculated correctly, you must make sure that union dues and health plans have a lower calculation priority number than the garnishment has. For tax levies, voluntary benefit enrollments that were in place before the tax levy typically have higher priority than the tax levy. Therefore, those benefits must have a lower calculation priority number than the tax levy.<strong>NOTE: </strong>Your legal advisors should help you determine the correct calculation priority for all benefits. |
| Deduction priority   | The number that you enter determines the order that deductions for the garnishment are made in, relative to other deductions. The deduction for the benefit that has the lowest deduction priority number is made first. The lowest deduction priority number is 0 (zero). Often, garnishments must be deducted from pay before other voluntary benefits. However, some states require that specific deductions take precedence, such as union dues or term life deductions. The default value for this field is set on the **Benefit elements** page.<strong>NOTE: </strong>Your legal advisors should help you determine the correct deduction priority for all benefits. |
| Rate source          | This field is automatically set to **Custom**. Because you must manually maintain the amount of a garnishment, you can't change this value. For more information, see "Setting up payroll information for benefits" in [Set up payroll for workers](noam-usa-worker-position-payroll-tasks.md). This field isn't available for tax levies. |
| Basis Deduction      | The court order indicates whether the deduction should be a fixed amount (for example, 350.00 per pay period) or a percentage of earnings (for example, 15 percent of earnings). Select the basis, and then enter the deduction amount that is specified on the court order. These fields aren't available for tax levies. The tax levy deduction is calculated based on the information on the **Tax levy details** FastTab. |
| Notes                | Enter detailed information about the garnishment order, such as the date when it was received, data that was entered, and communication with the worker. |

Enter the following information on the **Payroll limits** FastTab. In most cases, garnishment orders don't have limit amounts or periods. Instead, the garnishment continues until the court notifies you to stop it.

| Field        | Description |
|--------------|-------------|
| Limit amount | If a limit is indicated on the support order, set the limit period, and enter the value in the **Limit amount** field.|
| Remaining    | Enter the initial amount of the order. |

If the garnishment enhancement hotfix is installed, skip to the table for the **Garnishment and tax levy details** FastTab. If the garnishment enhancement hotfix isn't installed, enter the following information on the **Garnishment details** and **Tax levy details** pages. If you require more information about these fields, contact your legal advisors.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Garnishment type Tax levy type</td>
<td>Specify the garnishment type or the tax levy type.</td>
</tr>
<tr>
<td>Case number</td>
<td>Enter the case number or reference number that is assigned by the court.</td>
</tr>
<tr>
<td>Limit method</td>
<td>In most cases, select <strong>Calculate disposable income</strong>. Select <strong>Use alternative limit</strong> only if your legal advisors direct you to select that option. In this case, your legal advisors should provide the amount to enter in the <strong>Alternative limit</strong> field.</td>
</tr>
<tr>
<td>Disposable income definition Maximum withholding percent</td>
<td>If the state that issued the garnishment order requires any changes to the federal rules that define the worker's disposable income, select the disposable income definition for this garnishment. Then enter the maximum withholding percentage that is provided in the court order. Otherwise, leave these fields blank. These fields are available only for garnishments, and only when the limit method is <strong>Calculate disposable income</strong>.</td>
</tr>
<tr>
<td>Income exempt from levy</td>
<td>Enter the amount of wages that are exempt from the tax levy.
<ul>
<li>For a federal tax levy, use publication 1494, which is updated and issued every year.</li>
<li>For state and local tax levies, see the state's tax levy withholding rules, and apply the formulas to determine the amount of the exemption.</li>
</ul>
This field is available only for tax levies, and only when the limit method is <strong>Calculate disposable income</strong>.</td>
</tr>
<tr>
<td>Alternative limit</td>
<td>Enter the maximum amount that can be deducted from a single pay statement for the garnishment. This amount should be provided by your legal advisors. This field is available only when the limit method is <strong>Use alternative limit</strong>.</td>
</tr>
<tr>
<td>Administrative fee</td>
<td>Enter the amount to reduce the deduction for the garnishment by if the deduction for the garnishment plus the deduction for the administrative fee exceeds the worker's disposable income limit. This field doesn't cause the administrative fee to be deducted. Instead, it sets the amount that the garnishment deduction should be reduced by. To deduct the administrative fee, you must create a benefit for the administrative fee and then assign that benefit to the worker.
<strong>IMPORTANT: </strong>The amount in this field must be the same as the amount in the <strong>Amount or rate</strong> field for the administrative fee benefit that you assign to the worker.</blcockquote>
</td>
</tr>
<tr>
<td>Multiple garnishment method</td>
<td>Select the method to use if the amount of the deduction must be split among multiple garnishments of the same type:
<ul>
<li><strong>None</strong> – The garnishment should not be included in a group of garnishments.</li>
<li><strong>Pro rata</strong> – The deduction is divided so that each garnishment receives a proportionate amount.</li>
<li><strong>Equal</strong> – The deduction is divided so that each garnishment receives an equal amount.</li>
<li><strong>First in</strong> – The garnishments are satisfied in the order in which the worker enrolled in them. This option is typically used for tax levies.</li>
</ul>
<strong>IMPORTANT: </strong>If the court order doesn't specify which method to use, check with your legal advisors for clarification. Typically, if the orders have the same type but are from different states, the laws in the state where the worker works apply. For example, a worker who is located in Washington has three orders: two from California and one from Idaho. The rules for Washington apply to all three orders. However, if this worker has two support orders from California and a creditor garnishment from Idaho, the support orders use the California rules, and the creditor garnishment uses the Idaho rules. If it isn't clear which method you should use, check with your legal advisors.</td>
</tr>
</tbody>
</table>

If the worker is enrolled in more than one garnishment or tax levy, you must complete the steps in the "Additional setup requirements when a worker is enrolled in multiple garnishments or tax levies, and the garnishment enhancement hotfix isn't installed" section, later in this article. If the garnishment enhancement hotfix is installed, enter the following information on the **Garnishment and tax levy details** FastTab. If you require more information about these fields, contact your legal advisors.

| Field              | Description |
|--------------------|-------------|
| Type               | Select the garnishment or tax levy type. Don't select the **Combined garnishments** type. If a worker is enrolled in garnishments and tax levies of more than one type, set up rules for the **Combined garnishments** type on the **Garnishments and tax levy rules** page. |
| Case number        | Enter the case number or reference number that is assigned by the court. |
| State              | Specify the state that the tax levy is from. This field is available only for state and local tax levies. It isn't available for other garnishment types. |
| Administrative fee | When the garnishment type is **Support order**, if the deduction for the garnishment plus the deduction for the administrative fee exceeds the worker's disposable income limit, the deduction for the garnishment is reduced by the amount that you enter. This field helps ensure that the total deduction doesn't exceed the worker's disposable income limit for support orders. For all other garnishment and tax levy types, this field is for information only and doesn't cause the administrative fee to be deducted. To deduct the administrative fee, you must create a benefit for the administrative fee and assign that benefit to the worker.<strong>IMPORTANT: </strong>The sum of all administrative fees that are charged to the worker should equal the sum of the deductions for all administrative fee benefits that the worker is enrolled in. If the amounts differ, the amount that is deducted from the worker's pay for administrative fees might be incorrect. |

Set up each garnishment type only one time for each worker. When a worker has more than one garnishment of the same type, all the garnishments that have the same type use the rules that are set up for that type. State and local tax levies are an exception. In this case, you set up one state tax levy type and one local tax levy type for each state. On the **Garnishment and tax levy rules** page, enter the following information for each garnishment type that a worker is enrolled in.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Type</td>
<td>Specify the garnishment type.
<strong>IMPORTANT: </strong>When a worker is enrolled in more than one type of garnishment, you must add the <strong>Combined garnishments</strong> type in addition to the types that the worker is enrolled in. The <strong>Combined garnishments</strong> type helps ensure that the garnishment amounts are adjusted correctly, based on the selected disposable income definition and any rules that apply across garnishment types. The disposable income definition and maximum withholding percentage are the only fields that are used by the <strong>Combined garnishments</strong> type. All other fields are for your information only.
</td>
</tr>
<tr>
<td>State</td>
<td>Specify the state that a tax levy is from. This field is available only for state and local tax levies. It isn't available for other garnishment types.</td>
</tr>
<tr>
<td>Limit method</td>
<td>Select <strong>Calculate disposable income</strong> to calculate the worker's disposable income for garnishments of this type. Select <strong>Use alternative limit</strong> only if your legal advisors direct you to select that option. In this case, your legal advisors should provide the amount to enter in the <strong>Alternative limit</strong> field.</td>
</tr>
<tr>
<td>Disposable income definition</td>
<td>Select the disposable income definition to use for garnishments of this type. If you leave this field blank, the federal rules that define the worker's disposable income are used. This field is available only when the limit method is <strong>Calculate disposable income</strong>. For more information, see <a href="noam-usa-garnishment-tax-levy-set-up-tasks.md">Garnishment and tax levy setup tasks</a>.</td>
</tr>
<tr>
<td>Maximum withholding percent</td>
<td>Enter the maximum percentage of disposable income that can be withheld for garnishments of this type. For the <strong>Combined garnishments</strong> type, enter the maximum percentage of disposable income that can be deducted for the combined total of all garnishments except support orders and tax levies. If you leave this field set to <strong>0.0000</strong>, no deduction is made. This field is available only when the limit method is <strong>Calculate disposable income</strong>.</td>
</tr>
<tr>
<td>Alternative limit</td>
<td>Enter the maximum amount that can be deducted from a single pay statement for garnishments of this type. The amount should be provided by your legal advisors. This field is available only when the limit method is <strong>Use alternative limit</strong>.</td>
</tr>
<tr>
<td>Multiple garnishment method</td>
<td>Select the method to use if the amount of the deduction must be split among multiple garnishments of the same type:
<ul>
<li><strong>None</strong> – The deduction isn't split among garnishments of this type.</li>
<li><strong>Pro rata</strong> – The deduction is divided so that each garnishment receives a proportionate amount.</li>
<li><strong>Equal</strong> – The deduction is divided so that each garnishment receives an equal amount.</li>
<li><strong>First in</strong> – The garnishments are satisfied in the order in which the worker enrolled in them. This option is typically used for tax levies.</li>
</ul>
<strong>IMPORTANT: </strong>If the court order doesn't specify which method to use, check with your legal advisors for clarification. Typically, if the orders have the same type but are from different states, the laws in the state where the worker works apply. For example, a worker who is located in Washington has three support orders: two from California and one from Idaho. The rules for Washington apply to all three orders. However, if this worker has two support orders from California and a creditor garnishment from Idaho, the support orders use the California rules and the creditor garnishment uses the Idaho rules. If it isn't clear which method you should use, check with your legal advisors.
</td>
</tr>
<tr>
<td>Exempt disposable income</td>
<td>Enter the amount that should be used to further reduce the allowable deduction after the worker's disposable income is calculated. The amount should be provided by your legal advisors. It's based on IRS publication 1494 and applicable state requirements.</td>
</tr>
<tr>
<td>Exempt earnings</td>
<td>Enter the amount that the worker's earnings should be reduced by before the disposable income is calculated. The amount should be provided by your legal advisors.</td>
</tr>
<tr>
<td>Minimum wage Minimum wage multiplier</td>
<td>Specify the weekly minimum wage multiplier to use to calculate the garnishment amount. The minimum wage can be the federal minimum wage or a state minimum wage. For more information, see the state rules for the garnishment type, or contact your legal advisors.</td>
</tr>
<tr>
<td>Allow reduction</td>
<td>Select this option if deduction amounts for this garnishment type can be reduced so that they stay within the mandated limit for all garnishment types. This option is usually selected for student loan garnishments and cleared for support orders. If you aren't sure whether you should select this option, check with your legal advisors.</td>
</tr>
</tbody>
</table>

If the garnishment enhancement hotfix is installed, you can use the **Comments** FastTab to information about the garnishment or tax levy types that you entered or changed.

## Optional: Enrolling workers in administrative fees

Administrative fees, such as garnishments and tax levies, are processed as benefits. Administrative fees aren't permitted in every state. Even in states where they are permitted, they are never mandatory. Your organization must decide whether to charge them. The steps for enrolling a worker in an administrative fee vary, depending on whether the garnishment enhancement hotfix is installed.

- If the garnishment enhancement hotfix isn't installed, enroll the worker in one administrative fee benefit for each administrative fee that the worker is charged. For each administrative fee benefit, the amount in the **Amount or rate** field on the **Payroll details** FastTab of the **Benefit** page must match the amount in the **Administrative fee** field on the **Garnishment details** or **Tax levy details** FastTab of the **Maintain benefits** page.
- If the garnishment enhancement hotfix is installed, enroll the worker in one administrative fee benefit. The amount in the **Amount or rate** field on the **Payroll details** FastTab of the **Benefit** page for the benefit should equal the sum of all the administrative fees that the worker is charged.

On the **Benefits** page, enter the following information.

| Field   | Description                      |
|---------|----------------------------------|
| Benefit | Select **Eligibility bypassed**. |

On the **Payroll details** FastTab, enter the following information.

| Field                | Description |
|----------------------|-------------|
| Paid by              | Select the legal entity that the worker is employed by, and that pays for the worker position. By default, the current legal entity is selected. |
| Position             | Leave this field blank. |
| Vendor               | Leave this field blank. |
| Calculation priority | Your legal advisors should determine the correct calculation priority for the administrative fee benefit. |
| Deduction priority   | Your legal advisors should determine the correct deduction priority for the administrative fee benefit. |
| Rate source          | Select **Custom**. You must manually update the deduction amount for each worker when you change the amount that you charge for an administrative fee. You must also update the deduction amount when you enroll the worker in an additional garnishment that you charge an administrative fee for. |
| Basis                | Select **Fixed amount**.<strong>NOTE: </strong>You might have to adjust this amount in pay periods when some of the worker's garnishments or tax levies can't be taken. |
| Notes                | Enter information about the administrative fee. |

## Additional setup requirements when a worker is enrolled in multiple garnishments or tax levies, and the garnishment enhancement hotfix isn't installed

This section applies only if the garnishment enhancement hotfix isn't installed. When a worker has more than one garnishment order or tax levy, you might not be able to deduct the full amount of every garnishment and tax levy. Federal and state laws dictate the maximum combined amount that can be deducted for all garnishments, tax levies, and administrative fees.

State laws dictate how the total amount should be allocated among the various garnishments and tax levies. This allocation is partly based on the garnishment type and the calculation priority. When a worker's garnishments have the same type and calculation priority, the amounts are calculated automatically. If a worker has more than one type of garnishment, you might have to do some of the calculations manually. Procedures for both situations are described later in this article.

### Setting up multiple garnishments of the same type

When a worker has more than one garnishment of the same type and the same calculation priority, you must specify the multiple garnishment method that is used to allocate the amount of the deduction among the garnishments, as described in "Enrolling a worker in a garnishment or tax levy," earlier in this article. When multiple garnishments must be processed together, make sure that the garnishments have the same values in the following fields on the **Maintain benefits** page:

- Calculation priority
- Garnishment type
- Multiple garnishment method

Any garnishment that has a different value in one of these fields isn't included with the garnishments that are processed together. To make sure that garnishments of the same type are calculated correctly, you might have to adjust the calculation priority on one or more of the garnishments, so that the priorities match. You should seek guidance from your legal advisors any time that a worker has more than one garnishment or tax levy of the same type.

### Example of multiple garnishments of the same type

A worker has the following three child support orders. Because the calculation priority, garnishment type, and multiple garnishment method of all three child support orders match, the three garnishments are processed together.

|  &nbsp;                         | ChldSup01     | ChldSup02     | ChldSup03     |
|---------------------------------|---------------|---------------|---------------|
| **Calculation priority**        | 20            | 20            | 20            |
| **Basis**                       | Fixed amount  | Fixed amount  | Fixed amount  |
| **Deduction**                   | 450.0000      | 225.0000      | 200.0000      |
| **Garnishment type**            | Support order | Support order | Support order |
| **Maximum withholding percent** | 55.0000       | 55.0000       | 55.0000       |
| **Multiple garnishment method** | Pro rata      | Pro rata      | Pro rata      |

#### Wages and other factors that influence the garnishment amount

The worker's gross wages for the pay period are 2,000.00, and the total amount of taxes and benefits that are excluded from the worker's disposable income is 600.00. Therefore, the worker's calculated disposable income is 2,000.00 – 600.00, or 1,400.00.

The maximum amount that can be withheld from the worker's pay for these garnishments is 55 percent of 1,400.00, or 770.00.

The total amount that is required by the three garnishments is 450.00 + 225.00 + 200.00, or 875.00.

Because 875.00 is more than 770.00, which is the maximum withholding amount that is allowed, the multiple garnishment method must be applied.

> [!NOTE]
> For this example, if the total garnishments that are requested are less than the maximum withholding amount that is allowed, the full amount of each garnishment will be taken, and no multiple garnishment method will be applied.

#### How the pro-rata amount for each garnishment is calculated

In this example, here are the garnishment amounts for the **Pro rata** method:

- Total amount from all three support orders: 875.00
- Maximum withholding amount that is allowed: 770.00
- Percentage that can be applied to the first order: 51 percent (450.00 ÷ 875.00)
- Percentage that can be applied to the second order: 26 percent (250.00 ÷ 875.00)
- Percentage that can be applied to the third order: 23 percent (200.00 ÷ 875.00)
- First garnishment amount: 392.00 (770.00 × 0.51)
- Second garnishment amount: 200.20 (770.00 × 0.26)
- Third garnishment amount: 177.10 (770.00 × 0.23)

#### How the amount is calculated when the Equal method is used

Based on the wages and other factors that are described in the previous section, here are the garnishment amounts for the **Equal** method:

- Maximum withholding amount that is allowed: 770.00
- Maximum withholding amount divided by 3, because there are three orders: 256.67
- Third garnishment amount: 200.00 (the smaller of 256.67 and the requested amount)
- Second garnishment amount: 225.00 (the smaller of 256.67 and the requested amount)
- First garnishment amount: 345.00 (the maximum amount of 770.00 after it has been reduced by 200.00 from Gam03 and by 225.00 from Gam02)

#### How the amount is determined when the First-in method is used

Based on the wages and other factors that were described earlier, here are the garnishment amounts for the **First-in** method:

- Maximum withholding amount that is allowed: 770.00.
- First garnishment amount: 450.00. This garnishment is satisfied in full and is then subtracted from the maximum amount. Therefore, 320.00 remains for the other two garnishments.
- Second garnishment amount: 225.00. This garnishment is satisfied in full and is then subtracted from the remaining 320.00. Therefore, 95.00 remains for the third garnishment.
- Third garnishment amount: 95.00

After the amount remains reaches 0 (zero), no additional amounts can be deducted for any garnishment.

## Setting up multiple garnishments of different types

When a worker has multiple garnishments of different types, the individual limit that applies to each garnishment can be determined automatically. However, the final deductions against a single limit for the combined total of all the garnishments can't be determined. Therefore, when there are multiple garnishments of different types, you must manually calculate the total disposable income limit, and you must determine whether the combined amount of all the garnishments and tax levies exceeds the maximum deduction limit.

If the combined amount exceeds the maximum deduction limit, set the following values on the **Maintain benefits** page for each garnishment and tax levy that the worker is enrolled in.

| Field                       | Description |
|-----------------------------|-------------|
| Basis                       | Select **Fixed amount**. |
| Limit method                | Enter the amount of the garnishment that is specified on the court order. |
| Limit method                | Select **Use alternative limit**. |
| Alternative limit           | Enter the amount to deduct for this garnishment on each paycheck, based on the calculated disposable income, type of garnishment, and deduction priority. Your legal advisors should provide this amount.<strong>NOTE: </strong>When there are multiple garnishments and tax levies, the deduction amount for one or more of the garnishments or tax levies can be 0 (zero). |
| Multiple garnishment method | Select **None**. |

## Additional resources

[Set up garnishments and tax levies](noam-usa-garnishment-tax-levy-set-up-tasks.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
