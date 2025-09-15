---
# required metadata
title: Employees select plans by using Employee self service (optional)
description: This article describes how employees can select or update their benefits.
author: ramagadu 
ms.date: 04/25/2025
ms.topic: article
# optional metadata

# ms.search.form: EssWorkspace, 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: anisagrawal
ms.search.validFrom: 2020-12-28
ms.dyn365.ops.version: AX 7.0.0, Human Resources

---

# Employees select plans by using Employee self service (optional)

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

When a new employee is hired, or a life event occurs, the employee can use **Employee self service** to select or update their benefits during open enrollment.

To access their benefits for enrollment, the employee goes to **Employee self service**, select **Benefits self-service** on the **Benefits** tile.

On the **Benefits self-service** page, benefit plans are grouped by plan type. To view the benefit plans in a plan type, the employee selects a tile on the **Employee benefits** page. The employee sees only the benefits that they are eligible for.

> [!IMPORTANT]
> Before a plan type can be shown in **Employee self service**, it must be configured. For more information, see [Configure Employee self service](/dynamics365/human-resources/hr-benefits-setup-employee-self-service).

Depending on the plan type, one or more benefits can be selected for enrollment. For example, a medical plan type might be configured to limit the employee to one medical plan. A life insurance plan type might allow the employee to select multiple life insurance plans.

After the employee decides which plan to enroll in, they might be required to select dependents. If the employee selects a coverage option that is **Employee +1**, **Employee + children**, or **Family**, dependents must be selected. For more information about coverage options, see [Create coverage options](/dynamics365/human-resources/hr-benefits-setup-coverage-options).

To select a benefit plan, the employee selects either the ellipsis button (**…**) or **Add to cart**. After the employee finishes adding all the benefit selections to the cart, they select **View cart**. The employee is then taken to the **Plans** page, where they can view their selected and waived benefit plans.

The employee must select the **I agree** option before they can select the **Checkout** button. The statement that appears to the right of the **I agree** option can be customized on the **Benefits Management** tab of the **Human Resources Shared Parameters** page.

When the employee confirms their benefit plan selections by using **Employee self service**, those selections are recorded and shown on the **Worker benefit plans** and **Worker benefit plans bulk update** pages.

After the employee selects their plans, the status of the benefits is shown as **Selected**. When the employee selects **Check out** on the **Benefits self-service** page, the **Checked Out** option is selected.

> [!IMPORTANT]
> To complete enrollment, the benefits administrator must select **Confirm** for each employee benefit that is selected. Confirmation can be completed on the **Worker benefits plan** or **Worker benefit plans bulk update** page.

Employees aren't required to select benefits by using **Employee self service**. Benefits can be selected on behalf of an employee on the **Worker benefits plan** or **Worker benefit plans bulk update** page. The employee isn't enrolled in those benefits until the benefits administrator confirms them.

## My benefit plans

In Dynamics 365 Human Resources, employees can view selected benefits through the new **My benefit plans** tile in **Employee self service**.

This experience gives employees a consolidated view of their active benefit selections, including details about the dependents and beneficiaries that are associated with each plan. Employees can also view information about their previous year's enrollment.

### My benefit plans features

- The **My benefit plans** tile is available in the **Employee self service** workspace.
- View all current benefit selections in one place.
- View dependent and beneficiary details for each benefit plan.
- View a summary that provides combined coverage information across all plans.
- Access details about the previous year's enrollment for historical reference.

> [!IMPORTANT]
> Before you can use the **My benefit plans** tile, the **Benefits management** feature must be enabled in Feature management.

To view your benefits, follow these steps.

1. Go to **Employee self service**.
1. Select the **My benefit plans** tile.
1. Select the benefit period to review.
1. View your selected benefits together with dependent and beneficiary details.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
