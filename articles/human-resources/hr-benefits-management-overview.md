---
# required metadata

title: Benefits management overview
description: Overview of the Benefits management preview feature in Dynamics 365 Human Resources. Offer your employees extended benefits options with an easy-to-use online experience.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: BenefitWorkspace
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

# Benefits management overview

To remain competitive, you must offer a rich set of benefits to attract and retain your best employees. In addition to standard benefits like medical and dental coverage, you might also want to offer expanded services like adoption assistance, recreation programs, and clothing allowances. The Benefits management preview feature in Microsoft Dynamics 365 Human Resources provides you with a flexible solution that supports a wide variety of benefit options. Human Resources also includes an easy-to-use employee experience that showcases your offerings.

- Enhanced benefits plans let you create and manage unique benefit plans and support complex benefit rate tables and nested tiers. You can easily create benefit programs, bundles, and auto-enrollment rules for an easier employee experience.

- Flex credit programs let you prorate to support retirement and other life events.

- Extensive eligibility rules ensure you make the right benefits available to the right employees.

- Online benefits enrollment provides an easy experience for your employees.

- Qualified life event processing integrates with Employee self service, and also supports future life events.

If you would like to access the demo data, you'll need to redeploy your sandbox environment.

You can provide direct feedback or report issues to:  D365BenefitsPreview@microsoft.com.

## Benefits management known issues

### Eligibility processing

When running eligibility for benefits that use a 1-5X Salary, % of Salary, and Flat Amount coverage amount, you must set the **Benefit details** date to the **Employee start date** in **Employment history**. You must also include **Hours worked**, **Payment frequency**, and **Annual benefits salary amount**. If the worker has fixed compensation, enter **Hours worked** and **Payment frequency**. The annual salary amount will calculate. If the employee is salaried, you don't need to enter **Hours worked**. We recommend that when creating new workers, enter fixed compensation first. To update the benefit details record, navigate to **Worker > Worker history > Employment details**. Adjust the date to the worker's start date.

### Employee self-service

Employee amount doesn't calculate when updating the coverage amount for life insurance. For example, when an employee is offered a life insurance plan, they can select up to $50,000 in coverage at a cost of $.36 per $1,000 of coverage.  When the employee updates the coverage amount, the employee’s associated cost remains at zero.

For a benefit plan that only allows a single selection of that plan type, the user receives an error if they attempt to waive a plan after selecting a plan. For example, a user selects a medical plan and places it in their cart. The user then selects **Waive** for another medical plan. The user will receive an error.

## Enable Benefits management

Benefits management is a preview feature, and is only available in **Sandbox** environments. These articles describe how to turn on preview features in Human Resources. They also tell which existing features in Human Resources that Benefits management replaces or are disabled once you turn on Benefits management.

- [Manage features](hr-admin-manage-features.md)
- [Preview feature: Benefits management](hr-admin-manage-features.md?preview-feature-benefits-management)

## Configure Benefits management

Before you can create benefit plans for your employees, you need to configure options for the plans.

- [Set Benefits management parameters](hr-benefits-setup-parameters.md)
- [Configure eligibility rules and options](hr-benefits-setup-eligibility-rules.md)
- [Configure personal contact eligibility options](hr-benefits-setup-contact-eligibility-options.md)
- [Create coverage options](hr-benefits-setup-coverage-options.md)
- [Set up payment frequencies](hr-benefits-setup-payment-frequencies.md)
- [Configure life event types](hr-benefits-setup-life-event-types.md)
- [Create plan types](hr-benefits-setup-plan-types.md)
- [Set up reason codes](hr-benefits-setup-reason-codes.md)
- [Set up tier codes](hr-benefits-setup-tier-codes.md)
- [Configure rates](hr-benefits-setup-rates.md)
- [Configure deductions](hr-benefits-setup-deductions.md)
- [Configure waiting days](hr-benefits-setup-waiting-days.md)
- [Configure waiting periods](hr-benefits-setup-waiting-periods.md)
- [Set up rounding rules](hr-benefits-setup-rounding-rules.md)
- [Create employment categories](hr-benefits-setup-employment-categories.md)
- [Set up employment types](hr-benefits-setup-employment-types.md)
- [Configure employee self service](hr-benefits-setup-employee-self-service.md)

## Create benefit plans

These articles show how to create benefit plans, including bundles and flex credit programs.

- [Set up benefit plans](hr-benefits-plans-setup.md)
- [Create worker benefit plans](hr-benefits-plans-worker.md)
- [Set up flex credit programs](hr-benefits-plans-flex-credit-programs.md)
- [Configure future life events](hr-benefits-plans-future-life-events.md)

## Process benefit plans

You need to process some of your changes to make them active.

- [Process enrollment eligibility](hr-benefits-process-enrollment-eligibility.md)
- [Process life events](hr-benefits-process-life-events.md)
- [Process life event changes](hr-benefits-process-life-event-changes.md)
- [Process life event eligibility](hr-benefits-process-life-event-eligibility.md)
- [Process rate changes](hr-benefits-process-rate-changes.md)

