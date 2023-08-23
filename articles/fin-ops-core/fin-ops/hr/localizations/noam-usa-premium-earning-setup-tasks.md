---
# required metadata

title: Set up premium earnings
description: This article provides information about premium earnings and how to set them up.
author: twheeloc
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: PayrollEarningCode, PayrollEarningCodeGroup, PayrollPremiumEarningCode, PayrollPremiumEarningGenerationPolicy, SysPolicySourceDocumentRuleType
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 221084
ms.assetid: 50a441e2-b5b4-4ff0-9fc3-472c3b85c46f
ms.search.region: USA
# ms.search.industry: 
ms.author: panolte
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Set up premium earnings

[!include [banner](../../includes/banner.md)]

This article provides information about premium earnings and how to set them up. Premium earnings are extra earnings, such as bonuses or overtime premiums, that are paid to workers when specific conditions are met. Other types of premium earnings include a differential for hours that are worked on a second or third shift, and additional pay for workers who hold a certificate for advanced training or qualifications.

To set up and pay simple premiums, such as annual bonuses, you just have to create an earning code for the premium. Then, when it's time to pay the premium, you add the earning code to earnings statements. For more information, see [Set up earning codes and earning code groups](noam-usa-earning-code-group-tasks.md). Other premiums are based on other earnings, or on characteristics of the worker or position. This article explains how to set up the more complex types of premiums that are supported.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

| Category                        | Prerequisite |
|---------------------------------|--------------|
| Organization hierarchy purposes | On the **Organization hierarchy purposes** page, **Legal entity** must be selected as the only organization type that is allowed for premium earnings. |
| Policy parameters               | On the **Policy parameters** page, **Companies** must be included in the **Order or precedence** list. |
| Related configuration tasks     | Complete the basic setup of Payroll before you set up premiums. Note that work cycles and work periods are required for regular-rate-of-pay premiums. For more information, see [Set up work cycles and work periods](noam-usa-work-cycle-work-period-tasks.md). |

## Types of premiums

### Premiums that are based on earning codes

These premiums are used for shift differentials and similar premiums that should be paid any time that specified earning codes are included on an earnings statement. The following information must be set up before you can pay premiums that are based on earning codes:

- A premium earning policy. Most often, an organization has a single premium earning policy that is shared by all legal entities.
- Policy rule types that define the document and query parameters that you use when you develop specific policy rules.
- An earning code group that contains all earning codes that qualify for the premium.
- An earning code that uses a rate basis of **Percent of earnings** or **Hours of earnings** to calculate and pay the premium amount.
- Policy rules that specify the earning codes that must be present on the earnings statement for the premium earning to be generated.
- Premium codes that link the policy rule type that specifies the rules for the premium with the earning code that specifies how the premium should be calculated.

### Premiums that are based on characteristics of the worker or position

These premiums are used to provide additional pay, based on characteristics of the worker or position. For example, premiums can be paid to workers who hold certificates for advanced training, or they can be paid for positions that are based in a specific location. The following information must be set up before you can pay premiums that are based on the characteristics of a worker of position:

- A premium earning policy. Most often, an organization has a single premium earning policy that is shared by all legal entities.
- Policy rule types that define the document and query parameters that you use when you develop specific policy rules.
- An earning code that uses a rate basis of **Flat amount** to pay the premium amount.
- Policy rules that specify the conditions that must be met for the premium earning to be generated.
- Premium codes that link the policy rule type that specifies the rules for the premium with the earning code that specifies how the premium should be calculated.

> [!TIP]
> A premium can be based on a combination of earning codes and the worker or position. In that case, follow the instructions for setting up a premium that is based on earning codes. In the policy rules, include all earning codes that must be present and all conditions that must be met for the premium earning to be generated.

### Regular-rate-of-pay premiums

These premiums are most often used for overtime earnings that are paid in addition to the base earnings. These earnings include any adjustments that are required by the Fair Labor Standards Act (FLSA). The following information must be set up before you can pay regular-rate-of-pay premiums:

- Work cycles and work periods
- An earning code group that contains all earning codes for all nondiscretionary earnings
- Earning codes that use a rate basis of **Regular rate of pay** to calculate and pay the premium amount

A single earning code group can be shared by all earning codes that are used to calculate FLSA overtime premiums.

## Defining premium earning policies

Every legal entity that pays premium earnings that are based on earning codes, or on characteristics of the worker or position, must be assigned to a premium earning policy. You can create one policy that is shared by all legal entities, or you can create separate policies for each legal entity. You can also use a combined approach.

> [!TIP]
> After a premium policy is created, it usually doesn't require additional maintenance. You manage the premiums that your organization pays by maintaining the policy rules and earning codes.

Later in this process, you will define policy rule types and create policy rules for this policy. The policy rules specify the conditions that must be met for the premium to be paid. The policy rule types are used on the premium codes to associate the policy rules with the earning codes that are used to calculate the premium amount.

> [!NOTE]
> Although you can't delete policies or policy rules, you can retire them so that they are no longer used. When you retire a policy, you also retire all the corresponding policy rules for that policy. You can't reactivate a policy that has been retired. However, you can reactivate a retired policy rule by changing the effective dates on the rule.

## Setting up premiums that are based on earning codes

These premiums are used for shift differentials and similar premiums that should be paid any time that specified earning codes are included on an earnings statement.

Before you create the premium earning codes, review the earning codes that were created during the basic Payroll setup process, to make sure that all earning codes that qualify for premiums have been created. For example, your company pays a premium for hours that are worked on the second shift. Earnings for the first shift and the second shift are identical, but only the hours that are worked on the second shift qualify for the premium. In this case, to correctly apply the premium, you must have separate earning codes for first-shift earnings and second-shift earnings. If you require additional earning codes, you can create them before you continue to create premium policies and codes. Be sure to add those earning codes to the earning code group that was created for regular-rate-of-pay premiums.

If your company pays a differential for work on the second and third shifts, the premium might differ for union workers and non-union workers. In this case, you must have four earning codes. Therefore, you must identify all the various premiums that your organization pays. You must then identify which of those premiums are based on other earnings.

### Creating premium policy rule types

Policy rule types define the document and query parameters that are used when you develop specific policy rules. You must create a premium policy rule type for each premium that you identify. You create policy rule types on the **Premium earning policy rule types** page. The following table shows the information that you must enter.

| Field            | Description |
|------------------|-------------|
| Name Description | Enter a name and a brief description for the policy rule type. For example, for a second-shift differential, you might enter **2nd Shift** as the name and **Second shift differential** as the description. |
| Query name       | Select **Premium earnings**. This query is the default Application Object Tree (AOT) query that should be used as the starting point to develop policy rules for this policy rule type. |

### Setting up earning code groups to identify earnings that qualify for a premium

Earning code groups are used to identify earnings that qualify for the premium. You set up earning code groups on the **Earning code groups** page. You must create additional earning code groups to correctly identify the earnings for all your premiums that are based on earnings. An earning code group can be used by more than one premium. For example, if you have different shift differentials for union workers and non-union workers, those premiums will probably use the same earning code group.

Earning codes are also used to calculate and pay the premium amounts for each premium that is based on other earnings. These earning codes use a rate basis of **Percent of earnings** when the premium is defined as a percentage of the eligible earning amount. They use a rate basis of **Hours of earnings** when a premium is defined as an amount per hour.

### Setting up policy rules for premium earnings

Policy rules must be set up for premium earnings. A policy rule is a database query that is run against source documents. It specifies the conditions that must be met for the premium to be paid. The policy rule types are used on premium codes to connect the policy rules with the earning codes that are used to calculate the premium amount. Typically, you create one policy rule for each policy rule type that you create.

A policy rule that is used to generate premium earnings for workers is sometimes known as a premium earning rule. You set up policy rules for premium earnings on the **Premium earnings policies** page. To create policy rules, double-click the policy to create policy rules for.

Then create the policy rule on the **Policy rules** FastTab. Each policy rule specifies an earning code that must be present on an earnings statement for the associated premium earning to be generated. Be sure to enter a date range for your policy rule. Otherwise, the policy rule is effective when it's created, and it never expires.

> [!TIP]
> If you know that the requirements for the premium earning will change later, you can create future-dated versions of the rule in addition to the current version.

Use the expression builder to add a line for each earning code that qualifies for the premium earning. In addition to the earning code, other conditions might have to be met for the premium to be paid. In this case, be sure to add a line for each condition.

### Setting up premium codes

Premium codes must also be set up. Premium codes contain the information that is required in order to generate premium earnings. They link the policy rule type that specifies the rules for the premium with the earning code that specifies how the premium should be calculated.

You set up premium codes on the **Premium codes** page. When you create a premium code, it's a good idea to use the same name and description that you used for the policy rule type. Specify the field values on the **General** FastTab. These field values define the rule that triggers this premium, the earning code that is used, whether earnings are created based on earning lines or the earnings statement, and the calculation frequency.

The payroll calculation frequency should include the pay periods that this premium code should be used in. Premium earnings are generated only in the pay periods that are included in the payroll calculation frequency that you select. For example, some premium earnings might be generated only in the first pay period of each month.

The policy rule type determines whether earnings statement lines are created for this premium code.

In the **Payout basis** field, select **Earnings statement**.

> [!IMPORTANT]
> The earning code that is used to pay the premium aggregates hours and earnings to determine the line total. If you select **Earning line** as the payout basis, the aggregate line is created one time for each earning code that is in the Basis earning code group. This setup causes earnings to be significantly overstated. Select the earning code that is used to pay the premium. This earning code appears on the premium lines that are added to earnings statements. You must also specify an active interval, or the first and last dates that the premium code can be used.
>
> Active intervals can't overlap. Therefore, if an existing interval for the selected premium code is active on the date when a new interval takes effect, the existing interval is automatically expired on that date. Likewise, if you change the date when an existing interval starts or ends, any existing intervals that are active during the new interval are expired to prevent the intervals from overlapping.

## Setting up premiums that are based on characteristics of the worker or position

These premiums are used when workers are entitled to extra pay because of characteristics that are related to the worker or position. To set up premiums that are based on characteristics of the worker or position, identify the premiums that your organization pays. Then identify which of those premiums are based on characteristics of the worker or position. For example, many organizations pay a premium to workers who hold advanced certifications. Policy rule types define the document and query parameters that are used when you develop specific policy rules. You must create a premium policy rule type for each premium that you've identified.

### Creating premium policy rule types

To create a premium policy rule type, on the **Premium earning policy rule types** page, enter a name and a brief description for the policy rule type. For example, if you're paying a premium to workers who hold advanced certifications, you might enter **Certification premium** as the name and **Licenses and certificates** as the description. The default AOT query that you should use as the starting point to develop policy rules for this policy rule type is **Premium earnings**. It's a good idea to use this value as your query name. Use this page to create any additional policy rule types that your organization requires.

For each premium that is based on characteristics of the worker or position, create an earning code to pay the premium amounts. These earning codes use **Flat amount** as the rate basis.

### Setting up policy rules for premium earnings

A policy rule consists of a database query that is run against source documents. It specifies the conditions that must be met for a premium to be paid. The policy rule types are used on premium codes to connect the policy rules with the earning codes that are used to calculate the premium amount. Typically, you create one policy rule for each policy rule type that you create.

A policy rule that is used to generate premium earnings for workers is sometimes known as a premium earning rule.

To set up policy rules for your premium earnings, on the **Premium earning policies** page, click the policy, and then create a policy rule on the **Policy rules** FastTab. Each policy rule specifies a characteristic of the worker or position that must be present for the associated premium earning to be generated. Specify effective and expiration dates for the policy rule. If you don't specify these values, the policy rule is effective when it's created, and it never expires.

> [!TIP]
> If you know that the requirements for the premium earning will change later, you can create future-dated versions of the rule in addition to the current version.

In the expression builder, add a line for each condition that must be met for the premium to be paid. On this page, you can create as many additional policy rules as you require.

### Setting up premium codes

Premium codes contain the information that is required in order to generate premium earnings. They link the policy rule type that specifies the rules for the premium with the earning code that specifies how the premium should be calculated. To set up a premium code, on the **Premium codes** page, enter a name and a description for it. It's a good idea to use the same name and description that you used for the policy rule type. For example, for premiums for workers who hold advanced certifications, you might enter **Certification premium** as the name and **Licenses and certificates** as the description.

Field values on the **General** FastTab of the **Premium codes** page define the rule that triggers this premium, the earning code that is used, whether earnings are created based on earning lines or the earnings statement, and the calculation frequency. The following table shows the information that you must enter.

<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Payroll calculation frequency</td>
<td>Select the payroll calculation frequency that includes the pay periods that this premium code should be used in. Premium earnings are generated only in the pay periods that are included in the payroll calculation frequency that you select. For example, some premium earnings might be generated only in the first pay period of each month.</td>
</tr>
<tr>
<td>Policy rule type</td>
<td>Select the policy rule type that determines whether earnings statement lines are created for this premium code. For example, select <strong>Certification premium</strong>.</td>
</tr>
<tr>
<td>Payout basis</td>
<td>Select how the premium is paid:
<ul>
<li>To add one premium line for each statement line that qualifies for the premium, select <strong>Earning line</strong>.</li>
<li>To add one premium line for each earnings statement that qualifies for the premium, select <strong>Earnings statement</strong>.</li>
</ul>
</td>
</tr>
<tr>
<td>Earning code</td>
<td>Select the earning code that is used to pay the premium. This earning code appears on the premium lines that are added to earnings statements.</td>
</tr>
<tr>
<td>Active interval &gt; New</td>
<td>Enter the first and last dates that a premium code can be used.
[!IMPORTANT] Active intervals can&#39;t overlap. Therefore, if an existing interval for the selected premium code is active on the date that a new interval takes effect, the existing interval is automatically expired on that date. Likewise, if you change the date when an existing interval starts or ends, any existing intervals that are active during the new interval are expired to prevent the intervals from overlapping.
</td>
</tr>
</tbody>
</table>

## Setting up regularrateofpay premiums

Regular-rate-of-pay premiums are most often used for overtime earnings that are paid in addition to the base earning rate. These earnings include any adjustments that are required by the FLSA.

Before you set up a regular-rate-of-pay premium, review the earning codes that were created during the basic Payroll setup process, to make sure that all earning codes that are required for nondiscretionary earnings have been created. Make sure that work cycles and work periods have been set up. For more information, see [Set up work cycles and work periods](noam-usa-work-cycle-work-period-tasks.md). Additionally, identify all the various overtime earnings that your organization pays. For example, your organization pays both time-and-a-half and double-time for overtime hours that are worked on first, second, and third shifts. This combination requires that you have six earning codes to correctly calculate and pay all overtime premiums. Union contracts, location differentials, and other factors might require additional earning codes.

You set up an earning code group for nondiscretionary earnings on the **Earning code groups** page. Create a new earning group, and enter a name and a brief description for it. For example, you might enter **FLSA earnings** as the name and **All nondiscretionary earnings** as the description. Add the relevant earning codes.

> [!IMPORTANT]
> If any earning codes for nondiscretionary earnings are omitted from this earning code group, the overtime premium won't be calculated correctly.

You must create an earning code to calculate and pay the premium amounts for each type of overtime earnings that you identified. These earning codes all use **Regular rate of pay** as the rate basis.

## Additional resources

[Set up earning codes and earning code groups](noam-usa-earning-code-group-tasks.md)


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
