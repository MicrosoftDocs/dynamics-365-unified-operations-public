---
# required metadata

title: Benefits management overview
description: Overview of Benefits management feature in Dynamics 365 Human Resources. Offer your employees extended benefits options with an easy-to-use online experience.
author: andreabichsel
manager: AnnBe
ms.date: 04/06/2020
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

To remain competitive, you must offer a rich set of benefits to attract and retain your best employees. In addition to standard benefits like medical and dental coverage, you might also want to offer expanded services like adoption assistance, recreation programs, and clothing allowances. Benefits management in Microsoft Dynamics 365 Human Resources provides you with a flexible solution that supports a wide variety of benefit options. Human Resources also includes an easy-to-use employee experience that showcases your offerings.

- Enhanced benefits plans let you create and manage unique benefit plans and support complex benefit rate tables and nested tiers. You can easily create benefit programs, bundles, and auto-enrollment rules for an easier employee experience.

- Flex credit programs let you prorate to support retirement and other life events.

- Extensive eligibility rules ensure you make the right benefits available to the right employees.

- Online benefits enrollment provides an easy experience for your employees.

- Qualified life event processing supports future life events.

If you would like to access the demo data, you'll need to redeploy your sandbox environment.

## Benefits management known issues

### Flex credit programs

The total credit value defined for a flex credit program doesn't display in the **Worker benefit plans** form. Also, if you set a flex credit program to have a proration rule of **None**, you get an error in the **Worker benefit plan** form when selecting and confirming plans.

## Enable Benefits management

This article describes how to turn on features in Human Resources. It also tells which existing features in Human Resources that Benefits management replaces or are disabled once you turn on Benefits management.

> [!IMPORTANT]
> After you enable Benefits management in a **Production** environment, you can't disable it. We recommend enabling and testing Benefits management in a **Sandbox** environment before enabling it in a **Production** environment. There are significant differences between the legacy Benefit functionality and new Benefits management functionality that require additional setup and should be tested prior to being placed into production.

- [Manage features](hr-admin-manage-features.md)

## Configure employee information

Before you can enroll employees in benefits, you must provide required information. You must enroll an employee in a **Fixed compensation plan** on their start date, and you must select a **Benefit pay frequency** in **Employment details** on the **Worker** form.

When you create a benefit plan that uses rates that are based on gender or age, you must enter a birth date and gender for the employee to calculate the benefit cost.

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
- [Set up flex credit programs](hr-benefits-plans-flex-credit-programs.md)

## Process benefit plans

You need to process some of your changes to make them active.

- [Process enrollment eligibility](hr-benefits-process-enrollment-eligibility.md)
- [Process life events](hr-benefits-process-life-events.md)
- [Process life event changes](hr-benefits-process-life-event-changes.md)
- [Process life event eligibility](hr-benefits-process-life-event-eligibility.md)
- [Process rate changes](hr-benefits-process-rate-changes.md)

