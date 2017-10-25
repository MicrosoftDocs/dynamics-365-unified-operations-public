---
# required metadata

title: Configure expense management
description: This article describes the considerations and the decisions that you must make during the planning process before you configure Expense management in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. 
author: KimANelson
manager: AnnBe
ms.date: 08/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: GlobalCategory, ProjCategory, TrvLocations, TrvParameters, TrvPaymethod, TrvPerDiems
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 23001
ms.assetid: aa3fd14d-7e94-4603-985f-ca26d6f860ea
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure expense management

[!include[banner](../includes/banner.md)]


This topic describes the considerations and the decisions that you must make during the planning process before you configure Expense management in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. In Expense management, you can store information about payment methods, travel requisitions, expense reports, policies, and so on.

Because many of the decisions that you make when you plan your configuration for Expense management are based on your organization’s hierarchy and financial structure, you must refer to the planning documents for those areas.

## Intercompany expenses

When you enable intercompany expenses, you allow legal entities and employees to incur expenses on behalf of another legal entity, and collect payment from the legal entity of employment within your organization. For example, an employee in legal entity A completes a project for legal entity B, and the project incurs travel related expenses. If intercompany expenses are enabled, the employee can then file an expense report that will post the expense to legal entity B, and the expense must then be paid by legal entity A. If your organization doesn’t have multiple legal entities, you don’t have to enable intercompany expenses.

**Decision:** Do you want to enable intercompany expenses?

## Financial management

Expense management is tightly integrated with the financial management of your organization. Lots of your configuration for Expense management will be based on the decisions that you’ve made about your organization’s finances. The following sections describe the various areas that require planning and decisions, based on your organization’s financial decisions and guidance from your leadership team.

### Per diems

You must define the employee per diems that your organization provides. Because per diems are typically used to cover expenses such as meals, lodging, and other incidental expenses, you can create rules for the per diem allowances that your organization offers. per diem rates can be based on the time of year, the travel location, or both. When you define a per diem rule, you can specify that a percentage of the per diem rate will be withheld if a worker receives complimentary meals or services. You can also define per diem rate tiers to set the minimum and maximum number of hours that the per diem rate can be applied to a worker’s travel.

**Decisions:**

- Default per diem rules for the first and last days:

    - What is the minimum number of hours that an employee can claim for a day and still receive a per diem?
    - Is there a reduction in the amount that is offered for meals for the first day and last day? If there is a reduction, what is the percentage of the reduction?
    - Is there a reduction in the amount that is offered for a hotel for the first day and last day? If there is a reduction, what is the percentage of the reduction?
    - Is there a reduction in the amount that is offered for other expenses that are incurred on the first day and last day? If there is a reduction, what is the percentage of the reduction?

- Default per diem rules:

    - Is there a percentage reduction in the per diem allowance for each meal if, for example, the meal is complimentary? If there is a reduction, what is the reduction percentage for each meal?
    - Is the meal reduction calculated per day, per trip, or by the number of meals per day?
    - Should per diem amounts be rounded in the regular manner or rounded up?
    - Are per diems calculated on a 24-hour period or on a calendar day?

- Per diem rules that are based on location:

    - Do per diem rates vary according to location? What locations are included?
    - If per diem rates vary according to location, for each location, what percentage amount is provided for the following types of expenses:

        - Meals
        - Hotel
        - Other expenses

### Expense management journals and accounts

Expense management requires that you use multiple journals and accounts. You must decide, for example, whether the same account is used for cash advances and credit card disputes.

**Decisions:**

- Which ledger journal are approved expense reports posted to?
- Which account is used for cash advances?
- Should cash advances be posted immediately?

### Payment methods

When you allow employees to incur expenses on behalf of your business, you must define the payment methods that employees are allowed to use. For example, you might allow employees to use cash or a corporate credit card. You might also allow employees to use personal credit cards, and then reimburse the employees. You must make the following decisions for each payment method that you allow.

**Decisions:**

- What payment methods are allowed?
- Who owns the payment method expenses?
- Is there an offset account type? If there is an offset account type, what is it?
- If there is an offset account, what is the account?
- If the payment method is a credit card, should the payment method be used only with imported transactions?

### Expense categories and shared categories

When employees create an expense report, each expense that they record must be associated with an expense category. Expense categories are derived from shared categories that can be shared across the legal entities in your organization. These categories can also be shared in Project management and accounting, depending on the way that your organization is defined. Based on the definition of your organization and guidance from the implementation team, determine whether the categories that are used in Expense management will be used only in Expense management, or whether they should be shared between Project management and accounting and Expense management. Note that these categories can be shared between Project and Expense or Project and Production, but not between Expense and Production. You must make the following decisions for each expense category.

**Decisions:**

- What is the expense category? Examples include categories for flights, hotel, or mileage.
- Can the expense category also be used in Project management and accounting?
- What is the expense type?
- What is the default payment method for the expense category?
- Do expenses in the expense category have to be itemized?
- What is the main default account for the expense category?
- What is the default item sales tax group for the expense category?
- Are additional payment methods allowed for the expense category? If additional payment methods are allowed, what are they?
- Are there subcategories in this expense category? If there are subcategories, you must also make the following decisions:

    - Are any of the subcategories excluded from tax recovery?
    - What is the item sales tax group of the subcategories?

If the expense category is also used in Project management and accounting, answer the remaining questions. Otherwise, move on to the next section.

- Which cost accounts will be used for the following expenses?

    - Cost
    - Payroll allocation
    - WIP-cost value
    - Cost-item
    - WIP-cost value-item
    - Accrued loss
    - WIP-accrued loss

- Which revenue accounts will be used for the following?

    - Invoiced revenue
    - Accrued revenue-sales value
    - WIP-sales value
    - Accrued revenue-production
    - WIP-production
    - Accrued revenue-profit
    - WIP-profit
    - Accrued revenue-subscription
    - WIP-subscription

### Taxes

For expense-related taxes, you must determine what is included or enabled on expense reports.

**Decisions:**

- Is sales tax included in the expense amounts?
- Should tax recovery be enabled on expenses?

    > [!NOTE]
    > When you were planning the general ledger, if you decided to apply U.S. sales tax and use tax rules, you can’t enable tax recovery on expenses. (To apply U.S. sales tax and use tax rules, set the **Apply sales tax taxations rules** option to **Yes**.)

## Policies

By creating expense report policies, you can help your organization save time and money when employees incur expenses on its behalf. Policies help guarantee that employees stay in budget, provide all required information, and spend money only as they require it. You must make the following decisions for each expense report policy and each expense report approval policy that you create.

**Decisions:**

- What is the name of the policy?
- What is the expense policy for?
- If you previously decided to enable intercompany expenses, which companies in your organization will this policy apply to?
- When does the policy become effective?
- When does the policy expire?
- What is the policy rule?
- What is the outcome of the policy rule?
