---
# required metadata

title: Manage features
description: Learn how to turn new features on or off in Dynamics 365 Human Resources.
author: andreabichsel
manager: AnnBe
ms.date: 02/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-human-resources
ms.technology: 

# optional metadata

ms.search.form: FeatureManagementWorkspace
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

# Manage features

As part of our continuous rollout of new capabilities for Microsoft Dynamics 365 Human Resources, we want to let customers experience new features as soon as possible. We provide preview features, which are almost ready for general availability and have gone through extensive testing. We're just looking for a final round of customer feedback and validation before we release them for general availability.

For more information about new features in Human Resources, see [What's new in Human Resources](hr-admin-whats-new.md) and [Dynamics 365 and Power Platform Release Plan](https://docs.microsoft.com/dynamics365/release-plans/#pivot=products&panel=products1).

The **Feature management** workspace provides a list of features delivered in each release. By default, new features are turned off. You can use the workspace to turn them on and view the documentation for them. For more information about Feature management, see [Feature management overview](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview).

All new features remain in preview for at least 30 days, and typically 30-60 days. Major features are generally available in October and April of each year following the preview period. As soon as you see new capabilities in the **Feature management** workspace, you can turn them on. Some features may be on by default.

Once a feature is generally available, it may be turned on or off in production environments. The **Feature management** workspace indicates when a preview feature will become mandatory. This date is usually on October 1 or April 1 to align with the semiannual release plans. You can't turn off mandatory features. Until it becomes mandatory, you can turn a feature on and off in all environments.

## Enable or disable preview features

To access preview features, you must first enable them in your environment. Enabling or disabling preview features is environment-specific.

> [!IMPORTANT]
> Preview features are only available in **Sandbox** environments. When you turn on a preview feature, you enable it for all users in your organization who are in that environment. When you turn off the preview feature, you disable it and make it inaccessible to your users. Preview features have limited support in Human Resources. They might use fewer privacy and security measures, and they aren't included in the Human Resources service level agreement (SLA). You should not use preview features to process personal data (that is, any information that could identify you), or to process other data that is subject to legal or regulatory compliance requirements.

1. In Human Resources, select **System administration**.

2. Select the **Feature management** tile.

3. To enable a preview feature, select it from the list, and then select **Enable**. To disable a preview feature, select it from the list, and then select **Disable**.

## Preview feature: Benefits management

Benefits management provides you with a flexible solution that supports a wide variety of benefit options, along with an easy-to-use employee experience that showcases your offerings. For more information about Benefits management configuration and use, see [Benefits management overview](hr-benefits-management-overview.md).

Benefits management replaces functionality in the **Benefits** workspace. When you enable the Benefits management preview feature, you can no longer access the following forms in the **Benefits** workspace:

- **Benefits**
- **Benefit elements**
- **Contribution calculation rates**
- **Benefit enrollment results**
- **Benefit expiration and extension results**
- **Benefit eligibility policy rule types**
- **Benefit eligibility policies**
- **Eligibility events**

You can view the information in these forms in read-only mode. If you want to edit the information, you must first disable the Benefits management preview feature.

### Benefits management known issues

#### Life events

When processing life events, the user will receive an error:

Coverage start date must be between *beginning of plan period* and *end of plan period*. 

The life event will continue to process as expected.

#### Eligibility processing

When running eligibility for benefits that use a 1-5X Salary, % of Salary, and Flat Amount coverage amount, the benefit details date must be set to the employee start date in **Employment history**, with hours worked, payment frequency and annual benefits salary amount. If fixed compensation exists for the worker, enter in the hours worked along with the payment frequency, and the annual salary amount will calculate. If the employee is salaried, the hours worked isn't needed. We recommend that when creating new workers, enter fixed compensation first. To update the benefit details record:  Navigate to **Worker > Worker history > Employment details**. Adjust the date to workers start date.

#### Employee-self service

Employees can select a plan that they aren't qualified for and check out.  For example: A worker doesn't have any dependents, but is allowed to select a medical plan with a family coverage option.

Employee amount isn’t being calculated when updating the coverage amount for life insurance. For example, when an employee is offered a life insurance plan, they can select up to $50,000 in coverage at a cost of $.36 per $1,000 of coverage.  When the employee updates the coverage amount, the employee’s associated cost remains at zero.

For a benefit plan that only allows a single selection of that plan type, the user will receive an error if they attempt to waive a plan after selecting a plan. For example, a user selects a medical plan and places it in their cart. The user then selects **Waive** for another medical plan. The user will receive an error.

## Preview features in Leave and absence

Leave and absence preview features include:

- **Leave and absence calendar** - Leave and absence parameters will move from **Human resources parameters** to a new screen called **Leave and absence parameters**. The new screen includes a new **Calendar** tab. This preview only enables a subset of the parameters. You can access the new screen from the **Links** tab of the **Leave and absence** workspace. The calendars include:
  - **Company calendar** - shows all employee time-off requests. People with the **Human resources** role can access this calendar from the **Links** tab of the **Leave and absence** workspace.
  - **Manager team calendar** - shows all direct reports' time-off requests. Managers can access the calendar from the **My team** tab in Employee self service under **Leave and absence**. 

- **Leave and absence holiday calendars** - Leave types include a new **Holiday** option, used in conjunction with the working time calendar. Days defined by holidays and closures are now designated as **Holiday** when working days are generated. When accruals are processed, adjustments are made to employees assigned to the calendar to account for holidays falling on a working day.

- **Leave accrual auditing** - A new screen lets you review when accruals have been processed and deleted, both by all employees and individual employees. You can access this new screen from the **Links** tab of the **Leave and absence** workspace.

- **Leave accrual deletion** - You can now delete accrual records for specific leave plans. You can access this new option from the **Links** tab of the **Leave and absence** workspace. For individual employees, this option appears in the **Leave and absence** grouping in the employee profile. 

- **Leave accrual rounding** - New options for **Leave type** define what type of rounding accrual should use, plus the decimal precision of the rounding during the accrual process. When accruals are processed, the rounding and precision are applied to the accrual records. 

- **Configure multiple leave types on a single leave plan** - A new column in the leave accrual schedule for leave types lets you define multiple leave types on a leave and absence plan with different accrual schedules. The previous **Leave type** field is removed. On the employee enrollment, the balances for the leave types now display in a table instead of at the top of the screen.

  > [!IMPORTANT]
  > You can't turn this feature off after you enable it.

- **Use an employee's full-time equivalency (FTE) for accrual** - a new column on the leave accrual schedule allows using FTE for accrual. When accruals are processed, the application uses the employee’s primary position and the FTE defined to determine the prorated accrual amount.

  > [!NOTE]
  > This feature is only available if you enable **Configure multiple leave types per leave plan**. 

## Feedback

We want to hear from you about your experience with preview features. We encourage you to regularly post your feedback on the following sites as you use these or any other features:

- [Community](https://community.dynamics.com/enterprise/f/759?pi53869=0&category=Talent) – This site is a great resource where users can discuss use cases, ask questions, and get community help.
- Let us know about features that you want to see in the product, or let us know about any changes you think we should make to existing features. Suggest product ideas on [Human Resources ideas](https://powerusers.microsoft.com/t5/Ideas-for-Human-Resources/idb-p/HumanResources)
    
Please don't include personal data (any information that could identify you) in your feedback or product review submissions. Collected information might be analyzed further and isn't used to answer requests under applicable privacy laws. Personal data that is collected separately under these programs is subject to the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).

## See also

- [What's new in Human Resources](hr-admin-whats-new.md)
- [Dynamics 365 and Power Platform Release Plan](https://docs.microsoft.com/dynamics365/release-plans/#pivot=products&panel=products1)