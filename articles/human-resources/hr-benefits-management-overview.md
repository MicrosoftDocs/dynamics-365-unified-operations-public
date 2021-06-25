---
# required metadata

title: Benefits management overview
description: Overview of Benefits management feature in Dynamics 365 Human Resources. Offer your employees extended benefits options with an easy-to-use online experience.
author: andreabichsel
ms.date: 06/25/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace, HcmBenefitSummaryPart
# ROBOTS: 
audience: Application User
# ms.devlang: 
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

# Benefits management overview

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

To remain competitive, you must offer a rich set of benefits to attract and retain your best employees. In addition to standard benefits like medical and dental coverage, you might also want to offer expanded services like adoption assistance, recreation programs, and clothing allowances. Benefits management in Microsoft Dynamics 365 Human Resources provides you with a flexible solution that supports a wide variety of benefit options. Human Resources also includes an easy-to-use employee experience that showcases your offerings.

- Enhanced benefits plans let you create and manage unique benefit plans and support complex benefit rate tables and nested tiers. You can easily create benefit programs, bundles, and auto-enrollment rules for an easier employee experience.

- Flex credit programs let you prorate to support retirement and other life events.

- Extensive eligibility rules ensure you make the right benefits available to the right employees.

- Online benefits enrollment provides an easy experience for your employees.

- Qualified life event processing supports future life events.

If you would like to access the demo data, you'll need to redeploy your sandbox environment.

>[!NOTE]
>You can now customize Benefits management forms. You can now add custom fields related to coverage rates to the **Coverage option** form for benefit plans. For more information about working with custom fields, see [Custom fields](hr-developer-custom-fields.md).
>![Benefits management custom fields](media/hr-benefits-management-custom-fields.png)

## Enable Benefits management

This topic describes how to turn on features in Human Resources. It also tells which existing features in Human Resources that Benefits management replaces or are disabled once you turn on Benefits management.

> [!IMPORTANT]
> After you enable Benefits management in a **Production** environment, you can't disable it. We recommend enabling and testing Benefits management in a **Sandbox** environment before enabling it in a **Production** environment. There are significant differences between the legacy Benefit functionality and new Benefits management functionality that require additional setup and should be tested prior to being placed into production.

- [Manage features](hr-admin-manage-features.md)

## Process overview
The process of configuring benefits involves the following tasks:

-	Set up required benefit information
-	Set up optional benefit information
-	Set up benefit plans
-	Set up flex credit plans (optional)
-	Configure required employee information
-	Configure optional employee information
-	Process eligibility
-	Employees select plans via ESS
-	Employee’s plan selections are confirmed
-	Life event processing (optional)
-	Rate updates (optional)

## Set up required information
Before employees can be enrolled in the plans, there are multiple components that must be set up:

-	**Benefit management parameters** - These settings are shared across companies.  You can set default reason codes, enable the **Benefits annual salary** option, set a default pay frequency for new hires, and enable life events.  For more information, see [Set benefits management parameters](hr-benefits-setup-parameters.md).
-	**Personal contact eligibility options** – These are the individuals who will either be a dependent or beneficiary of the plans that are set up. Typically these are children, spouses, or trust organizations.  For more information, see [Configure personal contact eligibility options](hr-benefits-setup-contact-eligibility-options.md).
-	**Coverage options** – These are the type of coverages that will be available for a plan, specifically, who should be covered or how much coverage is available. For more information, see [Create coverage options](hr-benefits-setup-coverage-options.md).
-	**Plan types** – These are the types of plans that will be available when creating a benefit plan. Examples of plan types are *Dental*, *Vision*, and *Savings*. There are important settings on the plan type that dictates what settings are available on the benefit plan. For more information, see [Create plan types](hr-benefits-setup-plan-types.md).
-	**Eligibility rules** - These are the rules that will be used to determine if an employee is eligible for a plan. A benefit plan must have at least one eligibility rule associated to it. For more information, see [Configure eligibility rules and options](hr-benefits-setup-eligibility-rules.md).
-	**Payment frequencies** - These must be set up, as they are needed when configuring benefit rates. The payment frequency is used on the rate for understanding the amount owed by employee and/or employer either on a weekly, monthly or annual basis. For more information, see [Set up payment frequencies](hr-benefits-setup-payment-frequencies.md).
-	**Rates** - Rates are how much a benefit is going to cost either the employee or the employer. If money should be allocated back to an employee, such as a credit towards a gym membership, then a negative rate would be entered. For more information, see [Configure rates](hr-benefits-setup-rates.md).
-	**Tier rates** - Tier rates are used when you need to have a rate that changes based on some criteria. The most common tier rate is a single tier based on age. Double tier rates can also be set, where the rate may change based on gender or age or other criteria.
-	**Deductions** - The deductions are basically the header information/codes that are going to be passed onto the payroll system to understand the deduction for the benefit. You must set these up because they will be required on the benefit plan. For more information, see [Configure deductions](hr-benefits-setup-deductions.md).
-	**Benefit periods** – This is the time period employees will have benefit coverage. This is also known as a plan year. This is also where the open enrollment time periods are set.

## Optional setup
These components are not required to be set up to create a benefit plan.

-	**Programs** - A series of benefits that are governed by the same eligibility rules. For example, anyone in the sales department gets a cell phone.
-	**Bundles** - A group of benefits that a grouped together where one plan is required to be selected to get the option to select additional plans. An example would be bundling a high deductible medical plan with an HSA savings plan.
-	**Life event types** – These are the events that would allow for a change in coverage for an employee. These are tied to a plan type. For example, a medical plan type may allow for changes to plans due to a birth/adoption or change in marital status. An insurance plan type might not allow for any changes due to a life event. For more information, see [Configure life event types](hr-benefits-setup-life-event-types.md).
-	**Waiting days and Waiting periods** – On a benefit plan, a coverage waiting period can be set. For example, a newly hired employee can only enroll in a 401k after 3 months of employment. The waiting period would be 3 months. Waiting days are used within the waiting period if there is a specific date of the month that new enrollments can be processed to the provider. Tying into the 401k example above, if the 401k enrollments can only be processed on the 15th of the month, then a waiting period would be setup with 3 months and a waiting day of the 15th. For more information, see [Configure waiting days](hr-benefits-setup-waiting-days.md) and [Configure waiting periods](hr-benefits-setup-waiting-periods.md).
- **Reason codes** - Reason codes are used to explain why a benefit might be changing for an employee. For more information, see [Set up reason codes](hr-benefits-setup-reason-codes.md).

## Set up benefit plans
When setting up a benefit plan, the following items are required to be set to enroll employees: 

- Assign a benefit period
- Attach coverage options
- Set a valid from and valid to date on the **General** tab 
- Assign at least one eligibility rule
- Set **Allow/continue enrollment** on the **Setup** tab.  

To learn more about setting up benefit plans, see [Set up benefit plans](hr-benefits-plans-setup.md).

## Set up flex credit programs (optional)
You can use flex credit programs to enroll employees in benefits according to a predetermined number of flex credits. Employees can choose how to allocate their flex credits. For example, if an employee is already covered under their spouse’s health insurance plan, they may want to use the credits they would have otherwise used on health coverage toward other benefits.  To learn more about flex credit programs, see [Set up flex credit programs](hr-benefits-plans-flex-credit-programs.md).

## Configure required employee information
Before you can enroll employees in benefits, you must provide required information for the employee. The employee must have a position. You must enroll an employee in a fixed compensation plan on their start date or have an annual benefits salary amount, and you must select a **Benefit pay frequency** in the **Employment details** section on the **Worker** page.

If you have an employee who receives supplemental compensation like commissions, you can add a **Benefits annual salary** amount from the employee record. Human Resources will use the **Benefits annual salary** amount when determining coverage amounts, instead of the fixed compensation annual amount. The **Benefits annual salary** must be valid as of the employee’s start date or the beginning of the benefit period, whichever is latest. If both a fixed compensation and benefits annual salary amount is recorded for an employee, the benefits annual salary will be used in determining coverage amounts.

## Configure optional employee information
When you create a benefit plan that uses rates that are based on gender or age, you must enter a birth date and gender for the employee to calculate the benefit cost.

## Process employees to determine eligibility
Before an employee can be enrolled in plans, eligibility processing is run to see which plans an employee is eligible for. Results of the eligibility process can be viewed in the process results viewer.  For more information, see [Process enrollment eligibility](hr-benefits-process-enrollment-eligibility.md).

## Employees select plans via employee self-service (optional)
When open enrollment occurs, a new employee is hired, or a life event happens, an employee can select/update their benefits from employee self-service. For more information, see [Configure employee self-service](hr-benefits-setup-employee-self-service.md)

## Confirm employee plan selections 
After an employee selects their benefits, the benefits must be confirmed before the employee will be considered enrolled in the benefit. Benefits can also be selected on the employee's behalf.  Benefits can be selected and/or confirmed by navigating to the **Employee page**, selecting the **Benefits** tab, and selecting **Worker benefits plans**.  To select or confirm benefits for multiple employees, navgivate to the **Worker benefit plans bulk update** page.

## Life event processing (optional)
During the employee lifecycle, each employee may encounter various life event changes. For example, marriage, change in employment, or a dependent/beneficiary change. To use life events, you must enable life events in the **Human resources shared parameters** page. Set up **Life event types** and set up **Life event options** for plan types.

Before you can process life events, you must have already run open enrollment at least once during a hiring time frame. In the United States, open enrollment is typically once per year. Outside the United States, open enrollment may be run at the time of hire. A worker does not need to select a benefit plan in order for life events to be processed, but they need to have been included in open enrollment processing. For more information, see:

- [Process life events](hr-benefits-process-life-events.md)
- [Process life event changes](hr-benefits-process-life-event-changes.md)
- [Process life event eligibility](hr-benefits-process-life-event-eligibility.md)

## Rate updates (optional)
Sometimes the rate of a benefit may change during the plan period. To update the rates for employees that are already enrolled in the plan, you must process the rate changes. For more information, see [Process rate changes](hr-benefits-process-rate-changes.md).

[!INCLUDE[footer-include](../includes/footer-banner.md)]
